PROG5121 POE – QuickChat (Part 1 & Part 2)
Student Information
Name: Pretext Mina Mkhondo 
Student Number: ST10463664
Module: PROG5121 Programming 1A 
Project: QuickChat – Secure Messaging Console Application
Version: 2.0 (Complete Implementation)
Project Overview
QuickChat is a command-line messaging application developed in Java, combining secure user authentication (Part 1) with a functional messaging system (Part 2). The application allows users to register and log in, with accounts automatically locked after three failed login attempts. Once logged in, users can compose a set number of messages. The system validates South African mobile numbers in both local and international formats, enforces message length limits, generates unique message identifiers and hashes, and stores messages in a JSON file using only built-in Java utilities. Comprehensive unit testing ensures reliability across all components.
Key Features
Part 1 – User Registration and Login
- Username format: Must contain an underscore (_) and be no more than 5 characters long.
- Password criteria: At least 8 characters, including uppercase and lowercase letters, a digit, and a special character.
- Phone validation: Supports local (e.g., 0821234567) and international (+27821234567) formats via regex.
- Security measure: Login access is disabled after three consecutive failed attempts.
- Error clarity: The system specifies whether the username, password, or both are incorrect.
- Personalized welcome: The portion of the username before the underscore is extracted and capitalized (e.g., "kyl_1" results in "Welcome back Kyl!").
- Testing coverage: All validation and login logic is verified using JUnit 4 test cases.
Part 2 – Messaging System
- Post-login menu: A numbered interface (1, 2, 3) appears after successful login.
- Custom message count: Users choose how many messages they wish to write.
- Persistent menu loop: The messaging interface remains active until the user selects option 3 (Quit).
- Message input loop: A for loop collects the specified number of messages.
- Recipient validation: Phone numbers must begin with '+' and not exceed 10 characters including the symbol.
- Message length control: Messages are capped at 250 characters; exceeding this prompts re-entry.
- Unique message numbering: Each message receives a sequentially incremented ID assigned through the constructor.
- Message ID generation: A 10-character identifier is created using string manipulation methods like substring and String.format.
- Message hash creation: Formatted as XX:Y:FIRSTWORDLASTWORD (in uppercase), generated using split, replaceAll, and substring; punctuation is removed.
- Message actions: For each message, users can choose to: 1 Send (adds to sent list), 2 Disregard (prompts deletion), or 3 Store (saves to messages.json).
- Output sequence: Messages are displayed in the order: Message ID → Message Hash → Recipient → Message.
- Data storage: Messages are saved to messages.json using Java’s FileWriter—no third-party libraries are used.
- Exit summary: Upon quitting, the total number of sent messages is displayed.
- Testing scope: Unit tests confirm correct ID and hash generation, validation rules, action handling, and output formatting.
Technologies Used
- Java JDK 14 or newer
- JUnit 4.13.2
- Maven (for build and dependency management)
- GitHub Actions (automated testing via testjava.yml)
Project Structure (Folders and Files)
Root directory: QuickChat/
Contains: pom.xml, README.md, messages.json (created during runtime), and a .github folder.
The .github folder includes workflows/, which holds testjava.yml.
The src/ directory contains main/ and test/ subdirectories.
Under main/java/com/prog5121/: Registration.java, Login.java, Main.java, Message.java.
Under test/java/com/prog5121/: LoginTest.java, MessageTest.java.
Getting Started
Prerequisites: Java 14 or later, Apache Maven.
To Run the Application:
1. Clone or download the project.
2. Open a terminal in the project root (where pom.xml is located).
3. Compile using Maven.
4. Run the main class: com.prog5121.Main.
5. Follow on-screen prompts:
Main Menu:
Option 1: Register (enter username, password, and South African phone number)
Option 2: Login (enter username and password)
Option 3: Exit
After successful login, the QuickChat interface appears:
QuickChat Menu:
Option 1: Send Messages (specify count, then enter recipient and message for each)
Option 2: View recent messages (placeholder – feature not yet implemented)
Option 3: Quit (displays total sent messages and exits)
Sample Console Interaction (Text-Based)
The application begins with a welcome screen and main menu. The user selects Option 1 to register, enters valid credentials, and receives confirmation. Then chooses Option 2 to log in with correct details—login succeeds, and a personalized greeting is shown. The QuickChat interface launches. The user specifies the number of messages (e.g., 2). For each message, they enter a recipient starting with '+', type a message within the 250-character limit, and select an action (Send, Disregard, Store). After processing all messages, a summary displays sent messages in the required order: ID, hash, recipient, and message. On exit, the total number of sent messages is shown.
Running Unit Tests
Open a terminal in the project root and execute the Maven test command. All test cases must pass.
LoginTest (Part 1) covers:
- Valid and invalid usernames
- Valid and invalid passwords
- Correct and incorrect South African phone numbers
- Successful registration and login with proper greeting
- Failed login scenarios (incorrect username, password, or both)
- Account lockout after three failed attempts
MessageTest (Part 2) verifies:
- Message ID generation (non-null, exactly 10 characters, unique per instance)
- Recipient validation (valid +27718693002, invalid 08575975889, too long, or empty)
- Message length (under, exactly at, and over 250 characters)
- Message hash generation (non-null, uppercase, includes HI and TONIGHT or HI and PAYMENT, punctuation stripped)
- Consistent hash format across multiple iterations
- Correct handling of message actions (Send, Disregard, Store)
- Accurate count of total messages
- Proper output sequence (ID → Hash → Recipient → Message)
Code Attribution
- South African phone number regex: Adapted from a Stack Overflow answer. Credit is noted in code comments within Registration.java and Main.java.
- JSON file writing: Implemented manually using FileWriter—no external libraries involved.

  
Author
Pretext Mina Mkhondo – ST10463664
PROG5121 – Programming 1A 
Version 2.0 – Final POE Submission
License
This project is intended solely for academic assessment purposes.


