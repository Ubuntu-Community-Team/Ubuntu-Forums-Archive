---
title: "C++ - Case switch oddities"
date: 2013-02-08
forum: Programming Talk
---

### Post by sixstorm on 2013-02-08
Hello all.  I am writing a Time Clock application for my classroom and am having some trouble with the administrator menu.  For some reason, my case switch inside of a while loop works, but likes to perform multiple actions on a few selections.

Code:
```
void adminMenu() 
{
	int adminAnswer = 0; // Answer for the admin choice menu
	ofstream outFile;
	string tempFN; // Temporary first name
	string tempLN; // Temporary last name 
	int resumeCheck = 0;

	system("clear");

	while (adminAnswer!=7) {

		system("clear");
		// Admin menu display
		cout << "Choose from the following options" << endl;
		cout << "**********************************" << endl;
		cout << "1. List all Students in Roster(From File)" << endl;
		cout << "2. List TimeClock App Info" << endl;
		cout << "3. Print Daily Report" << endl;
		cout << "4. Add Student to Roster" << endl;
		cout << "5. Remove Student from Roster" << endl;
		cout << "6. Resume from Crash" << endl;
		cout << "7. Exit Admin Menu\n" << endl;
		cout << "Choice: ";
		cin >> adminAnswer;

		switch (adminAnswer) {
		case 1:
			{
			cout << "\nList of Students:\n";
			cout << "These are all of the students located in the 'students.txt' file\n" << endl;
			// Lists all students in the 'studentList' set
			for (student_it it=studentList.begin(); it!=studentList.end(); it++) {
				cout << *it << endl;
			}
			}
		case 2:
			{
			system("clear");
			cout << "\n\n\nTimeClock App\n";
			cout << "*************\n\n";

			cout << "Version " << version;
			cout << "\nCreated by John Handle and the CIT Classroom";
			cout << "\nCreated with Ubuntu 12.04 LTS and C++";
			}
		case 3:
			{
			system("clear");
			printReport();
			}
		case 4:
			{
			system("clear");
			cout << "Please enter the new student's first name (type 'quit' to exit): ";
			cin >> tempFN;
			if (tempFN == "quit") {
				break;
			}
			cout << "\nPlease enter the new student's last name: ";
			cin >> tempLN;

			// Output first and last name to the 'students.txt' file
			outFile.open("students.txt", fstream::in | fstream::out | fstream :: app);
			if (!outFile) {
				cout << "\nERROR: Student file did not open!" << endl;
			}
			outFile << tempFN << " " << tempLN << endl;
			outFile.close();
			}
		case 5:
			{
			// Remove student from 'students.txt'
			break;
			}
		case 6:
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
				system("sleep 2");
			}
		case 7:
			break;
		default:
			cout << "\n\nIncorrect Choice\n\n";
		}
	}
}}
```

Let's say I call the adminMenu and select option 1.  Here are the results:

```
Choose from the following options
**********************************
1. List all Students in Roster(From File)
2. List TimeClock App Info
3. Print Daily Report
4. Add Student to Roster
5. Remove Student from Roster
6. Resume from Crash
7. Exit Admin Menu

Choice: 1

These are all of the students located in the 'students.txt' file

Willie Nelson
Nickelback
Milli Vanilli



TimeClock App
*************

Version 0.08
Created by John Handle and the CIT Classroom
Created with Ubuntu 12.04 LTS and C++















Printing Daily Report






















Please enter the new student's first name (type 'quit' to exit):
```

If you can compare the actions with the list of options, you will see that choosing option 1 initiates option 1, 2, 3 and 4 at one time.  Is my while loop the problem?  Sorry for the crap code, still trying to clean it all up.  Also, I haven't wrote the actions for "removing a student" yet.  :KS

---

### Post by muteXe on 2013-02-08
Stick a break at the end of each case.

---

### Post by sixstorm on 2013-02-08
> **muteXe said:**
> Stick a break at the end of each case.

Well crap, I knew it had to be something simple.  Thanks!

---

