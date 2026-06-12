---
title: "Dummy Testing with a Case/Switch"
date: 2013-02-11
forum: Programming Talk
---

### Post by sixstorm on 2013-02-11
Quick question.  I have a menu that is displayed in my C++ program and a case/switch that allows the user to put in a number (1-7), then obviously each number performs a function.  But through doing some dummy testing, I can type in a number and character, and it starts going nuts.  Almost like it is doing an infinite loop.  Here is the code.

```
void adminMenu()
{
	int adminAnswer = 0; // Answer for the admin choice menu
	ofstream outFile;
	string tempFN; // Temporary first name
	string tempLN; // Temporary last name
	int resumeCheck = 0;
	string aConfirm;

	system("clear");

	while (adminAnswer!=7) {

		system("clear");
		// Admin menu display
		cout << "Number is: " << adminAnswer << endl;
		cout << "Choose from the following options" << endl;
		cout << "**********************************" << endl;
		cout << "1. List Students in Roster (From File)" << endl;
		cout << "2. List TimeClock App Info" << endl;
		cout << "3. Print Daily Report (report.txt)" << endl;
		cout << "4. Add Student to Roster" << endl;
		cout << "5. Remove Student from Roster" << endl;
		cout << "6. Resume from Crash" << endl;
		cout << "7. Exit Admin Menu\n" << endl;
		cout << "Choice: ";
		cin >> adminAnswer;
		switch(adminAnswer) {

		case 1: {
			cout << "\nList of Students:\n";
			cout << "These are all of the students located in the 'students.txt' file\n" << endl;
			// Lists all students in the 'studentList' set
			for (student_it it=studentList.begin(); it!=studentList.end(); it++) {
				cout << *it << endl;
			}
			cout << "***********************************\n" << endl;
			cout << "Press Any Key to Continue" << endl;
			cin.get();
			cin.get();
			break;
		}

		case 2: {
			cout << "\n\nTimeClock App\n";
			cout << "*************\n";

			cout << "Version " << version;
			cout << "\nCreated by Joe Blow and the CIT Classroom";
			cout << "\nCreated with Ubuntu 12.04 LTS and C++";
			cout << "Press Any Key to Continue" << endl;
			cin.get();
			cin.get();
			break;
		}

		case 3: {
			system("clear");
			printReport();
			cout << "Report has been successfully printed as 'report.txt'" << endl;
			cout << "Press Any Key to Continue" << endl;
			cin.get();
			cin.get();
			break;
		}

		case 4: {
			cout << "Please enter the first name of the student you would like to add (type 'quit' to exit): ";
			cin >> tempFN;
			if (tempFN=="quit") {
				break;
			}
			cout << "First Name: " << tempFN << " " << endl;
			cout << "Please enter the last name of the student you would like to add: ";
			cin >> tempLN;
			cout << "Are you sure you want to add " << tempFN << " " << tempLN << " to your roster? (y/n)";
			cin >> aConfirm;

			if (aConfirm=="y") {
				addStudent(tempFN, tempLN);
				loadStudentFile();
			}
			else if (aConfirm=="n") {
				cout << "\nOption Cancelled." << endl;
			}
			else {
				cout << "Invalid Selection." << endl;
				system("sleep 2");
			}
				
			break;
		}

		case 5: {
			cout << "Please enter the first name of the student you would like to remove (type 'quit' to exit): ";
			cin >> tempFN;
			if (tempFN=="quit") {
				break;
			}
			cout << "Please enter the last name of the student you would like to remove: ";
			cin >> tempLN;
			removeStudent(tempFN, tempLN);  // Runs function to remove student
			loadStudentFile();  // Reloads students from 'students.txt' to the 'studentList' set
			break;
		}

		case 6: {
			{
			// Check to see if resume has already been ran
			if (resumeCheck==1) {
				cout << "Resume has already been ran." << endl;
				system("sleep 2");
				break;
			}
			else {

				string info;
				string first_name;
				string last_name;

				ifstream inFile("spr.txt");
				if (!inFile)
					cout << "Error:  File failed to open!" << endl;
				while (getline(inFile, info)) {
					size_t space = info.find(' ');
					first_name = info.substr(0, space);
					last_name = info.substr(space+1);
					presentStudentList.insert(Student(first_name, last_name));
				}
				inFile.close();
				resumeCheck = 1;  // Resume only needs to be ran once
				cout << "Resume completed" << endl;
			}
			cout << "Press Any Key to Continue" << endl;
			cin.get();
			cin.get();
			break;
		}}

		case 7: {
			break;
		}

		default: {
			cout << "\n\nIncorrect Choice\n\n";
			break;
		}}}
}
```

Please ignore the lack of perfection as I haven't cleaned things up yet.  I'm sure it's something simple too, like usual.  ;)

---

### Post by lisati on 2013-02-11
If I understand your code correctly, you're filling adminAnswer with a character typed in at the keyboard, and testing it against an integer. You will need to convert the keyboard entry from an ASCII char to int.

---

### Post by Warren Hill on 2013-02-12
First thing I would look at is 

What is the value of adminAnswer if you enter a silly response such as 'q'?

May give you a clue

---

### Post by dwhitney67 on 2013-02-12
@ sixstorm

I told you before, in another thread you posted, that you should never accept raw user input directly using cin.  Use getline() instead, and then if needed, convert the string that is read in to the appropriate type.

Here's some untested code:
```

#include <string>
#include <sstream>

...
string input;
int    number;

do
{
    cout << "Enter a number: ";
    getline(cin, input);

    if (!cin.fail())
    {
        istringstream iss(input);

        iss >> number;

        if (iss.fail())
        {
            cout << "Invalid input!  Enter a number...\n" << endl;
        }
        else
        {
            break;
        }
    }
} while (true);

...

// you now have a number

```
If you are merely seeking character input of a number (in other words, you don't plan to perform mathematical operations on the input), then leave it in string format.  Thus, for instance, something like:
```

cout << "Enter a choice [1-7]: ";
getline(cin, input);

if (!cin.fail())
{
    switch (input[0])
    {
        case '1':
            ...

        case '2':
            ...

        ...

        default:
            //error in input
    }
}
else
{
    // error
}


```

---

### Post by sixstorm on 2013-02-12
> **dwhitney67 said:**
> @ sixstorm

I told you before, in another thread you posted, that you should never accept raw user input directly using cin.  Use getline() instead, and then if needed, convert the string that is read in to the appropriate type.


@dwhitney67 - You are right, I totally read over that, my bad.  

Thank you all for your input.  I'm going to look into this at some point today and try to get it working using getline.

---

### Post by sixstorm on 2013-02-12
Figured it out through a little research.

```
cin >> adminAnswer;  // User input into string 'adminAnswer'
		adminAnswer = adminAnswer[0]; // Takes first character from 'adminAnswer'
		stringstream (adminAnswer) >> adminResult;  // Converts string into int

		switch(adminResult) {

```

Now, just so I'm not wasting space on the forums, I have a separate question regarding a function I just wrote.

The function below is supposed to read each line into a set, then output the set, which sorts it alphabetically.

Text File example:
Doe John 15:00 ClockIn
Johnson Jane 15:03 ClockIn

Code
```
void sortLog()
{
	ofstream outFile;
	ifstream inFile;
	set<string>::iterator iter;
	string inputStr;

	// Open 'log.txt'
	inFile.open("log.txt");
	if (!inFile) {
		cout << "ERROR:  'log.txt' could not be opened" << endl;
	}
	// Open 'temp.txt'
	outFile.open("temp.txt");
	if (!outFile) {
		cout << "ERROR: 'temp.txt' could not be opened" << endl;
	}
	// Until EOF of 'log.txt'
	while (getline(inFile, inputStr)) {
		// Input string into set
		sortSet.insert(inputStr);
                // Output what is read in on screen for testing
		cout << "Result: " << *iter << endl;
	}
	
	// Output set to 'temp.txt'
	for (iter=sortSet.begin(); iter!=sortSet.end(); iter++) {
			outFile << *iter << endl;
	}

	for (iter=sortSet.begin(); iter!=sortSet.end(); iter++) {
				cout << *iter << endl;  // Output all students on screen
	}
}
```

When this code/function is ran, I get a segmentation dump and it kills the program.  My code makes sense so I'm not sure what's going on.  Anyone see what's wrong?  

Thanks again for everyone's help!  :D

---

### Post by ofnuts on 2013-02-13
Several problems:

You test for non-null files after open, but you just display a message and still execute the rest of the code, so when the file won't be there you'll crash after the error message.

In the input loop, you dereference "iter" without initializing it. I also don't see where "sortSet" is declared/allocated/initialized...

---

### Post by spjackson on 2013-02-13
I'll take a punt on:
```

                // Output what is read in on screen for testing
		cout << "Result: " << *iter << endl;

```
I expect you mean inputStr not *iter

---

### Post by sixstorm on 2013-02-13
> **ofnuts said:**
> Several problems:

You test for non-null files after open, but you just display a message and still execute the rest of the code, so when the file won't be there you'll crash after the error message.

In the input loop, you dereference "iter" without initializing it. I also don't see where "sortSet" is declared/allocated/initialized...

The iterator is initialized globally; outside of int main.  Same for the sortSet as it is a string set.  Here is the code:

```
set <string> sortSet;
```

Inside void sortSet()

```
set<string>::iterator iter;
```

[quote=spjackson]I expect you mean inputStr not *iter[/quote]

I want it to output the entire set so it should be the iterator, not just a string.  

Haven't had time to mess with this today but should have some time tonight.  Thanks guys.

---

### Post by spjackson on 2013-02-13
> **sixstorm said:**
> The iterator is initialized globally; outside of int main.  Same for the sortSet as it is a string set.  Here is the code:

```
set <string> sortSet;
```

Inside void sortSet()

```
set<string>::iterator iter;
```

In the code you posted, iter is declared locally in the sortLog() function. If you have it declared elsewhere and initialised elsewhere, then that does not help because it is the local default initialised one that is being used.

> 
I want it to output the entire set so it should be the iterator, not just a string.  

That makes sense in your for loop:
```

	// Output set to 'temp.txt'
	for (iter=sortSet.begin(); iter!=sortSet.end(); iter++) {
			outFile << *iter << endl;
	}

```
But it doesn't make sense to me in the read loop, which is what I was pointing out. If it makes sense to you and isn't crashing there, then that's fine. It was just a guess. I personally find it difficult to debug a long section of incomplete code by sight alone. You can debug it yourself and find where it is crashing.

The following is a cut down version of what you are doing in sortLog() before you get to the for loops.
```

#include <set>
#include <string>
#include <iostream>

using namespace std;

int main()
{
  set<string>::iterator iter;

  // Output what is read in on screen for testing
  cout << "Result: " << *iter << endl;
}

```
This crashes for me, as I would expect it to, but if that's not your problem, I don't know what is.

---

### Post by dwhitney67 on 2013-02-13
> **sixstorm said:**
> 
I want it to output the entire set so it should be the iterator, not just a string.  


The iterator should be initialized to the beginning of the set *after *the set has been modified, not before.

You could also just forgo the use of an iterator variable, and just rely on the copy() function.  For example:
```

#include <iterator>
...
copy(sortSet.begin(), sortSet.end(), ostream_iterator<string>(cout, "\n"));

```

---

### Post by sixstorm on 2013-02-13
Ok, I fixed the code by removing the second for loop.

```
void sortLog()
{
	ofstream outFile;
	ifstream inFile;
	set<string>::iterator iter;
	string inputStr;

	// Open 'log.txt'
	inFile.open("log.txt");
	if (!inFile) {
		cout << "ERROR:  'log.txt' could not be opened" << endl;
	}
	// Open 'temp.txt'
	outFile.open("temp.txt");
	if (!outFile) {
		cout << "ERROR: 'temp.txt' could not be opened" << endl;
	}
	// Until EOF of 'log.txt'
	while (getline(inFile, inputStr)) {
		// Read line from inFile into sortSet
		sortSet.insert(inputStr);
	}
	
	// Output set to 'temp.txt'
	for (iter=sortSet.begin(); iter!=sortSet.end(); iter++) {
			outFile << *iter << endl;
	}

	// Backup 'log.txt'
	rename("log.txt", "backuplog.txt");
	// Rename 'temp.txt' to 'log.txt'
	rename("temp.txt", "log.txt");
}
```

I was able to make a separate program that just performed this function, tinkered with it and it worked perfectly.

Thanks again everyone!

---

