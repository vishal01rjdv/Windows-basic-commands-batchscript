# Windows-basic-commands-batchscript
Ex08-Windows-basic-commands-batchscript

# AIM:
To execute Windows basic commands and batch scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Windows environment installed on the system or installed inside a virtual environment like virtual box/vmware 

### Step 2:

Write the Windows commands / batch file . Save each script in a file with a .bat extension. Ensure you have the necessary permissions to perform the operations. Adapt paths as needed based on your system configuration.
### Step 3:

Execute the necessary commands/batch file for the desired output. 




# WINDOWS COMMANDS:
## Exercise 1: Basic Directory and File Operations
Create a directory named "my-folder"

## COMMAND AND OUTPUT

mkdir my-folder

<img width="917" height="40" alt="image" src="https://github.com/user-attachments/assets/10527190-2d30-4298-8ae9-c7c4369877ad" />

Remove the directory "my-folder"

## COMMAND AND OUTPUT

rmdir my-folder

<img width="791" height="50" alt="image" src="https://github.com/user-attachments/assets/5ad0894f-368f-4000-a81e-52cde6bc2573" />

Create the file Rose.txt

## COMMAND AND OUTPUT

type nul > Rose.txt

<img width="567" height="35" alt="image" src="https://github.com/user-attachments/assets/41276df4-7ea7-46c9-949a-a94f05752efb" />

Create the file hello.txt using echo and redirection

## COMMAND AND OUTPUT

echo Hello World > hello.txt

<img width="792" height="41" alt="image" src="https://github.com/user-attachments/assets/057a6600-9102-4dc1-b40f-bb00e95b6639" />

Copy the file hello.txt into the file hello1.txt

## COMMAND AND OUTPUT

copy hello.txt hello1.txt

<img width="620" height="61" alt="image" src="https://github.com/user-attachments/assets/61aa00fd-7a55-4ce2-b808-6738958991f5" />

Remove the file hello1.txt

## COMMAND AND OUTPUT

del hello1.txt

<img width="493" height="36" alt="image" src="https://github.com/user-attachments/assets/eced7dd5-1d5e-4266-bda6-7a0fb2175a54" />

List out the file hello1.txt in the current directory

## COMMAND AND OUTPUT

dir hello1.txt

<img width="525" height="210" alt="image" src="https://github.com/user-attachments/assets/aae15b29-d2ce-4f72-ae21-3a6367600648" />

List out all the associated file extensions 

## COMMAND AND OUTPUT

assoc

Compare the file hello.txt and rose.txt

## COMMAND AND OUTPUT

fc hello.txt Rose.txt

<img width="580" height="173" alt="image" src="https://github.com/user-attachments/assets/460c3af3-0798-4aaf-b266-028941e4a6ef" />

## Exercise 2: Advanced Batch Scripting
Create a batch file named on the desktop. The batch file need to have a variable assigned with a desired name for ex. name="John" and display as "Hello, John".
```
set name=John
echo Hello, %name%
pause

```
## OUTPUT

<img width="550" height="65" alt="image" src="https://github.com/user-attachments/assets/c5017ee4-239c-44d1-a2ca-32952df9a6a1" />


Create a batch file  on the desktop that checks whether a user-input number is odd or not. The script should:
Prompt the user to enter a number.
Calculate the remainder when the number is divided by 2.
Display whether the number is odd or not.
Ask the user if they want to check another number.
Repeat the process if the user enters Y, and exit with a thank-you message if the user enters N.
Handle invalid inputs for the continuation prompt (Y/N) gracefully.

## CODE
```
@echo off
:START
set /p num=Enter a number: 

set /a rem=%num% %% 2

if %rem%==1 (
    echo The number %num% is ODD
) else (
    echo The number %num% is NOT ODD
)

:CHOICE
set /p choice=Do you want to check another number? (Y/N): 

if /I "%choice%"=="Y" goto START
if /I "%choice%"=="N" goto END

echo Invalid choice. Please enter Y or N.
goto CHOICE

:END
echo Thank you!
pause

## OUTPUT

<img width="768" height="237" alt="image" src="https://github.com/user-attachments/assets/5a310808-8bca-4046-804f-9bb97aef2d24" />


Write a batch file that uses a FOR loop to iterate over a sequence of numbers (1 to 5) and displays each number with the label Number:. The output should pause at the end.

## CODE

for %%i in (1 2 3 4 5) do (
   
  echo Number: %%i
)

pause

```

## OUTPUT

<img width="768" height="237" alt="image" src="https://github.com/user-attachments/assets/c5d605c5-c03a-4121-85c5-97bf89dab4eb" />


Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions:
Use the IF EXIST conditional statement.
Make sure the script works for files located in the same directory as the batch file.
Use pause to keep the command window open after displaying the message.
Expected Output (if the file exists):

## CODE
```
for %%i in (1 2 3 4 5) do (
    echo Number: %%i
)
pause
```
## OUTPUT

<img width="500" height="182" alt="image" src="https://github.com/user-attachments/assets/169120a1-731c-4fdd-99b5-6a95db416f4b" />

Write a batch script to check whether a file named sample.txt exists in the current directory. If the file exists, display the message sample.txt exists. Otherwise, display sample.txt does not exist. Pause the script at the end to view the result.

Instructions: Use the IF EXIST conditional statement. Make sure the script works for files located in the same directory as the batch file. Use pause to keep the command window open after displaying the message. Expected Output (if the file exists):

## CODE
```
@echo off
if exist sample.txt (
    echo sample.txt exists
) else (
    echo sample.txt does not exist
)
pause
```
## OUTPUT

<img width="501" height="57" alt="image" src="https://github.com/user-attachments/assets/45eb65b7-672b-4e23-89b2-d1b42814f4a2" />


Write a batch script that displays a simple menu with three options:
Say Hello – Displays the message Hello, World!
Create a File – Creates a file named newfile.txt with the content This is a new file
Exit – Exits the script with a goodbye message
The script should repeatedly display the menu until the user chooses to exit. Use goto statements to handle menu navigation.

## CODE
```
:MENU
cls
echo ===== MENU =====
echo 1. Say Hello
echo 2. Create a File
echo 3. Exit
echo =================
set /p choice=Enter your choice: 

if "%choice%"=="1" goto HELLO
if "%choice%"=="2" goto CREATE
if "%choice%"=="3" goto EXIT

echo Invalid choice!
pause
goto MENU

:HELLO
echo Hello, World!
pause
goto MENU

:CREATE
echo This is a new file > newfile.txt
echo File created successfully!
pause
goto MENU

:EXIT
echo Goodbye!
pause
exit
```
## OUTPUT 1

<img width="514" height="238" alt="image" src="https://github.com/user-attachments/assets/edd4311b-1845-4615-acfa-bf4d6e63fd70" />

## OUTPUT 2

<img width="515" height="233" alt="image" src="https://github.com/user-attachments/assets/10df9577-3efa-4c27-a075-c5bcbad467ba" />

## OUTPUT 3

<img width="522" height="232" alt="image" src="https://github.com/user-attachments/assets/b5351925-f1f1-4796-b992-a9c672bf9396" />

# RESULT:
The commands/batch files are executed successfully.

