AI-POWERED SECURITY CODE REVIEWER


1. PROJECT OVERVIEW

The AI-Powered Security Code Reviewer is a Python application that reviews source code for common security vulnerabilities.

The application accepts a security-related user query and source code. An AI model acts as a security expert and analyzes the code. A local vulnerability scanning tool detects common security issues and provides structured findings.

The system provides the vulnerability category, severity, affected line, problem description, and suggested fix.


2. OBJECTIVE

The main objectives of this project are:

• To develop an AI-powered security code reviewer.
• To detect common security vulnerabilities in source code.
• To use a local vulnerability scanning tool.
• To explain security issues in simple language.
• To provide suggested fixes for detected vulnerabilities.
• To handle clean and empty code properly.
• To handle API and tool errors gracefully.
• To test the security scanner using test cases.


3. TECHNOLOGIES USED

• Python 3
• Google Gemini API
• Google GenAI SDK
• Regular Expressions
• JSON
• Google Colab


4. SYSTEM ARCHITECTURE

User Query and Source Code
            |
            v
    AI Security Reviewer
            |
            v
   Vulnerability Scanner
            |
            v
    Security Findings
            |
            v
   Final Security Report


5. PROJECT STRUCTURE

AI_Security_Code_Reviewer
|
|-- README.md
|
|-- code_sentry
    |
    |-- main.py
    |
    |-- tools.py
    |
    |-- prompts.py
    |
    |-- demo.py
    |
    |-- tests
        |
        |-- test_tools.py


6. FILE DESCRIPTION

main.py

Contains the main AI-powered security reviewer and handles communication with the Gemini API.


tools.py

Contains the local scan_vulnerabilities function used to detect security vulnerabilities.


prompts.py

Contains the system prompt that defines the AI as a security expert.


demo.py

Demonstrates the vulnerability scanner using sample source code.


test_tools.py

Contains automated test cases for checking the vulnerability scanner.


README.md

Contains project documentation, setup information, test cases, and project details.


7. VULNERABILITIES DETECTED

The scanner checks for the following security issues:

1. Hardcoded Secrets
2. Code Injection using eval()
3. Code Injection using exec()
4. SQL Injection
5. Command Injection using shell=True
6. Insecure Deserialization using pickle
7. Unsafe YAML Loading
8. Weak Hashing using MD5 and SHA-1
9. Missing Input Validation


8. TEST CASES

The project contains the following test cases:

TC-01: Code Injection Detection

Input:

result = eval(user_input)

Expected Result:

Category: Code Injection
Severity: High

Status: Pass


TC-02: Command Injection Detection

Input:

subprocess.run(command, shell=True)

Expected Result:

Category: Command Injection
Severity: High

Status: Pass


TC-03: SQL Injection Detection

Input:

query = "SELECT * FROM users WHERE id=" + user_id

Expected Result:

Category: SQL Injection
Severity: High

Status: Pass


TC-04: Hardcoded Secret Detection

Input:

password = "mypassword123"

Expected Result:

Category: Hardcoded Secret
Severity: High

Status: Pass


TC-05: Clean Code Detection

Input:

def add(a, b):
    return a + b

Expected Result:

Status: clean
Findings: []

Status: Pass


TC-06: Empty Code Handling

Input:

Empty source code

Expected Result:

Status: clean
Findings: []

Status: Pass


9. TEST EXECUTION

The test cases can be executed using:

from code_sentry.tests.test_tools import *

test_eval_detection()
test_shell_injection()
test_sql_injection()
test_hardcoded_secret()
test_clean_code()
test_empty_code()

print("ALL SECURITY TESTS PASSED!")


Expected Output:

===================================
ALL SECURITY TESTS PASSED!
===================================


10. EXAMPLE SECURITY REPORT

Sample vulnerable code:

password = "admin123"

user_input = input("Enter expression: ")

result = eval(user_input)


Security Report:

Summary Verdict:
High Risk


Finding 1

Category:
Hardcoded Secret

Severity:
High

Problem:
A password, API key, token, or secret appears to be hardcoded.

Suggested Fix:
Store secrets in environment variables or a secure secret manager.


Finding 2

Category:
Code Injection

Severity:
High

Problem:
eval() can execute dynamically supplied code.

Suggested Fix:
Avoid eval() and use safe parsing or validated input.


Finding 3

Category:
Missing Input Validation

Severity:
Medium

Problem:
User-controlled input appears to be used without obvious validation.

Suggested Fix:
Validate the type, length, format, and allowed values.


11. ERROR HANDLING

The application handles:

• Empty source code
• API errors
• API rate limit errors
• Temporary service unavailability
• Unexpected tool errors
• Invalid tool responses

When the AI service is unavailable, the local vulnerability scanner can still perform security checks.


12. LIMITATIONS

• The scanner uses pattern-based detection.
• It may produce false positives or false negatives.
• It does not replace a professional security audit.
• AI functionality depends on API availability and usage limits.
• Only configured vulnerability patterns are detected.


13. FUTURE SCOPE

• Integration with Bandit and other security tools.
• Support for additional programming languages.
• Development of a web-based security review interface.
• Downloadable security reports.
• Additional vulnerability detection rules.
• Advanced vulnerability severity analysis.
• Integration with additional static analysis tools.


14. CONCLUSION

The AI-Powered Security Code Reviewer demonstrates the integration of an AI model with a local security scanning tool.

The application can detect common security vulnerabilities, identify their severity, explain the security risks, and provide suggested fixes.

The automated test cases help verify that the local scanner correctly identifies important vulnerability patterns and handles clean and empty source code appropriately.
