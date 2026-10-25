# messy-code
A project exploring AI-assisted Python code refactoring workflows with Cursor AI, validating deterministic zero-regression outputs against strict baseline test data, and enforcing automated standards via .cursor/rules (.mdc).

Overview
The goal of this case study is to take a legacy, poorly-structured Python script (messy.py), analyze and refactor its logic using AI agent workflows, and ensure the refactored code preserves identical output character-for-character.

Additionally, custom Cursor rules were configured to automatically govern AI generation behavior—guaranteeing adherence to clean code principles, strict naming conventions, and docstrings.

Refactoring Workflow
Baseline Character Parity: Captured original program behavior in original_output.txt to serve as the ground truth validation target.
AI Code Exploration: Analyzed legacy functions in Ask Mode without modifying files.
Targeted Refactoring: Used Cursor Inline Edit (Cmd + K) and Agent Mode to transform repetitive routines, clean logic, and eliminate magic numbers.
Behavioral Testing (Pre vs. Post Rules):
Pre-Rules: Observed AI generating extra unrequested print lines and omitting docstrings.
Post-Rules: With .cursor/rules/python-standards.mdc active, the AI produced compliant code adhering to return-type docstrings and minimal code scope.
Output Verification: Ran final executions against original_output.txt to guarantee 100% output parity.
Coding Standards Enforced (.cursor/rules/python-standards.mdc)
description: Python coding standards for this course
globs: ["**/*.py"]
alwaysApply: true

- Use descriptive variable names. Single letters are allowed only for loop counters.
- Every function has a one-line docstring stating what it returns.
- Use f-strings for output, never string concatenation.
- Do not hard-code a number that is used more than once. Name it.
- Do not add imports that are not used.
- Do not add features that were not requested.
