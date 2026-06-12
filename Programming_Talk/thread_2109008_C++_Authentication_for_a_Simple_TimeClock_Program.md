---
title: "C++ Authentication for a Simple TimeClock Program"
date: 2013-01-26
forum: Programming Talk
---

### Post by sixstorm on 2013-01-26
Hello all.  I am a CIT instructor for a technical school and we recently got our hands on a few Raspberry Pi devices.  My first "use" for them was to have my class take an old way of doing something and using the Pi in its place.

Every morning, our students come in and "clock in" using simple pen and paper that is located on an empty desk at the end of the desk row.  But I've taken it upon myself to brush the old cob webs off of my college programming history and give them a little programming insight by creating a simple C++ program that will clock them in and out everyday, using the Pi of course.

The program works great (CLI only for now) except for when I try to implement authentication.  

Program Explanation:

I have a TXT file with all of my students first names, last names and PINs, all separated by a single space, that is automatically inserted into two arrays (1 array for FN and LN, 1 array for the PIN).  Student is asked to input their First Name, then Last Name, and finally, their PIN; all of these are three separate strings.  Then a function is called to authenticate these three items by comparing them to the arrays in the first function.

Here is where the problem lies.  My initial thinking is:

First name matching up with student first name in array?  If true, proceed to last name check.  Otherwise, error and start from beginning.

Last name matching up with student last name in array?  If true, proceed to PIN check.  Otherwise, error and start from beginning.

PIN matching up with student first name in array?  If true, proceed to show student clock in menu.  Otherwise, error and start from beginning.

I've tried to type this all out using nested if statements, but what I've noticed is that the first name check runs perfect, then it breaks out of the function altogether.  Why doesn't it go to the next if statement?  

Here is the code I have now:
```
void authenticate (string FN0, string LN0, string code0)
{
	x = 0;
	y = 0;
	int a; // Reusable Counter
	bool auth; // If authenticated or not
	count = 0;

	// Search 'studentList' array to match first name
	for (a; a > MAX_STUDENTS; a++) {
		if (FN0 == studentList[x][y]) {
			cout << "First name matches!" << endl;
			cout << "Count: " << count << endl;
			for (a=0; a > MAX_STUDENTS; a++) {
				if (LN0 == studentList[x][y]) {
					cout << "Last name matches!" << endl;
					for (a=0; a > MAX_STUDENTS; a++) {
						if (code0 == codeArray[x]) {
							cout << "Code matches!" << endl;
						}
						else {
							x++;
						}
					}
				}
				else {
					x++;
				}
			}
		}
		else {
	                x++;
			count++;
		}
	}
}


```

I know that this is amateur coding over here but have some mercy.  Haven't done this for 6-7 years.  I may even be going about this the wrong way!  Any clues or help on why this doesn't work?

---

### Post by r-senior on 2013-01-26
I suspect that it's because this loop never gets executed because zero is not greater than the max number of students.

```
for (a=0; a > MAX_STUDENTS; a++) {
```

I think you need less than '<' and probably also need to look at the first loop where you don't initialize 'a' at all.

---

### Post by spjackson on 2013-01-26
With your nested loops, it appears that you are saying:
```

// pseudo-code
if there exists some record matching FN0
   if there exists some record matching LN0
       if there exists some record matching code0
           FOUND

```           
whereas what you really want to be saying is
```

for all the records
   if this record matches FN0
      if this record matches LN0
         if this record matches code0
             FOUND

```             
             
I am a bit puzzled about this 2 dimensional array studentList, and x and y. Maybe you mean studentList[a][0] is first name and studentList[a][1] is last name, in which case, that's what you should be comparing with the relevant parameter.

I suggest something like this:
```

// untested code
struct student {
    string firstname;
    string lastname;
    string pin;
};

student studentList[MAX_STUDENTS];

void authenticate (string FN0, string LN0, string code0)
{
    for (int a=0; a < count_of_students_read_from_file; a++) {
        if (FN0 == studentList[a].firstname) {
            if (LN0 == studentList[a].lastname) {
                if (code0 == studentList[a].pin) {
                    cout << "Authenticated\n";
                }
            }
        }
    }
}

```

---

### Post by sixstorm on 2013-01-26
> **spjackson said:**
> 
I am a bit puzzled about this 2 dimensional array studentList, and x and y. Maybe you mean studentList[a][0] is first name and studentList[a][1] is last name, in which case, that's what you should be comparing with the relevant parameter.



Sorry for the lack of information.  But yes, I have a 2D array for first name and last name, then a separate array for the codes.  But I see what you are saying with the code you suggested.

I've been recommended that I use a set or vector instead of arrays, but in all honesty, I don't see the point.  I will not be adding/removing anything from the studentList array any time during the program.  I'm simply loading a list of students first names, last names and codes into an array, then when the students clock in/out, the action details are output to a text file like this:

> 
ClockIn:  John Deer Sat. Jan 26th 16:50:31 CST

ClockOut:  John Deer Sat. Jan 26th 18:00:00 CST
Reason:  Left due to family illness


Any reason why I should use a set or vector instead of arrays?

---

### Post by sixstorm on 2013-01-27
I've decided to go with using a Student class and set instead of an array.  I'm having some issues compiling the code but more importantly, I'm having some trouble understanding the class + set combo.  Had a little hint from over at reddit.  Just trying to learn ;)

```

#include <iostream>
#include <string>
#include <cstdlib>
#include <ctime>
#include <fstream>
#include <iomanip>
#include <set>

using namespace std;

// Function definitions

void adminMenu();
void studentClockMenu(string FN, string LN);
void loadStudentFile();
void authenticate (string FNa, string LNa);

const int MAX_STUDENTS = 26; // Total number of possible students
string newTime; // Variable for time
time_t currentTime; // Variable for time
ofstream outFile; // Variable for output text file
double version = 0.04; // Variable for version number on the admin menu
int totalStudentsHere = 0; // Stat to show total # of students present
set <Student> studentList; // Creation of the set 'studentList'
set <Student>::iterator it=studentList.begin(); // Creation of iterator for 'studentList'

// Class definition of 'Student'
class Student
{
	private:
		string first_name;
		string last_name;

	public:
		Student(const string& fn, const string& ln)
		: first_name(fn), last_name(ln) { }
};


int main()
{
	string firstName;
	string lastName; 
	char sConfirm; 

	loadStudentFile(); // Calls function to load the student roster list	

	// Loop asks for first and last name, even checks for 'admin' or 'quit' commands
	do {		
		cout << "Please type in your first name: ";
		cin >> firstName;

		if (firstName == "quit") 
			break;

		else if (firstName == "admin") 
			adminMenu(); // Calls the admin menu function

		
		else {
			cout << "\nPlease type in your last name: ";
			cin >> lastName;

			cout << "\n\nAre you sure you want to log in as " << firstName << " " << lastName << 
"? (y/n) ";
			cin >> sConfirm;
			if (sConfirm == 'y') 
				authenticate(firstName, lastName); // Sends first and last name to the 'authenticate' function
			}
	} while (firstName != "quit");


	cout << "Thank you for using the Timeclock app!\n\n";
	return 0;
}

void adminMenu() 
{
	int adminAnswer; // Answer for the admin choice menu 

	// Admin menu display
	cout << "\n\n\n\n\n\n\n\n\n\n";
	cout << "Choose from the following options\n";
	cout << "**********************************\n\n";
	cout << "1. List all Students (From File)\n";
	cout << "2. List TimeClock App Info\n";
	cout << "3. Future Option (NOT WORKING)\n";
	cout << "4. Exit Admin Menu\n\n";
	cout << "Choice: ";
	cin >> adminAnswer;
	switch (adminAnswer) {
	case 1:
		cout << "\nList of Students:\n";

		// Lists all students in the 'studentList' set
		for (it=studentList.begin(); it!=studentList.end(); it++) {
		cout << *it << endl;
		}

		adminMenu();
	case 2:
		cout << "\n\n\nTimeClock App\n";
		cout << "*************\n\n";

		cout << "Version " << version;
		cout << "\nCreated by Andrew Scott and the CIT Classroom";
		cout << "\nCreated with Ubuntu 12.04 LTS and C++";
		cout << "\nTennessee Technology Center in Hartsville TN\n";
		
		adminMenu();
	case 3:
		cout << "\n\n\nFuture Option\n";
		// Function going away
		adminMenu();

	case 4:
		cout << "\n\n\nExiting Admin Menu";
		break;
	default:
		cout << "\n\n\nIncorrect Choice";
		break;
	}
}

void studentClockMenu(string FN, string LN)
{
	int studentAnswer; // This is the answer for the student choice menu
	string newTime;
	string finalTime;
	string studentReason; // This is the reason for leaving early
	char studentConfirm; // To confirm the student reason

	cout << "\nHello " << FN << " " << LN << endl;
	cout << "\nPlease Select from the Following Options:";
	cout << "\n\n1. Clock In";
	cout << "\n2. Clock Out";
	cout << "\n3. Cancel";
	cout << "\n\nChoice: ";
	cin >> studentAnswer;
	switch (studentAnswer) {
	case 1:
		newTime = time (&currentTime);
		finalTime = ctime(&currentTime);
		cout << "\nYou have officially clocked in at " << ctime(&currentTime) << "." << endl;

		// Output Action, First Name, Last Name and Time to 'clockin.txt'
		outFile.open("clockin.txt", fstream::in | fstream::out | fstream :: app);
		outFile << "ClockIn:  " << FN << " " << LN << " " << ctime(&currentTime) << "\n";
		outFile.close();

		// Increment total number of students counter
		totalStudentsHere++;

		break;
	case 2:
		newTime = time (&currentTime);
		finalTime = ctime(&currentTime);
		outFile.open("clockout.txt", fstream::in | fstream::out | fstream :: app);
		cout << "\nPlease put in a reason for your early leave: ";
		getline(cin, studentReason);
		getline(cin, studentReason);
		cout << "\n\nYour reason for clocking out is: \n" << studentReason << "\n";
		cout << "Please confirm your answer (y/n): ";
		cin >> studentConfirm;

		if (studentConfirm == 'y') {
			outFile << "ClockOut:  " << FN << " " << LN << " " << ctime(&currentTime) << " " << studentReason << endl;
			outFile.close();
		}

		else {
			cout << "Clock out cancelled.\n";
			break;
		}
		break;
	case 3:
		cout << "\nLogin cancelled.  You are officially logged out.\n";
		break;
	default:
		cout << "Invalid selection.  Please try again.";
		break;
	}
}

void loadStudentFile()
{
	string info;

	ifstream inFile("students.txt"); // Variable for studentList array
	if (!inFile) 
		cout << "Error:  File didn't open!" << endl;
	while (!inFile.eof()) {
		getline(inFile, info);
		studentList.insert(info);
		it++; 
	}
}

void authenticate (const string& FNa, const string& LNa) 
{
	Student possible(FNa, LNa);
	it = studentList.find(possible);
	if (it != studentList.end()) {
		studentClockMenu(FNa, LNa);
	}
	else
		cout << "Authentication Failed" << endl;
}

```

---

### Post by dwhitney67 on 2013-01-27
> **sixstorm said:**
> Just trying to learn ;)


Your code has some basic errors in it.  Start off by placing your declarations in the proper order (hint: Student and then set).

Here's a working program that does not meet all of your application's requirements, but demonstrates the basics of the usage of an STL set.
```

#include <string>
#include <set>
#include <fstream>
#include <stdexcept>
#include <iostream>


class ValidateStudent
{
    struct Student
    {
        std::string firstName;
        std::string lastName;
        std::string PIN;
    };

    struct StudentComparator
    {
        bool operator()(const ValidateStudent::Student& lhs, const ValidateStudent::Student& rhs) const
        {
            if (lhs.firstName < rhs.firstName) return true;
            if (lhs.lastName < rhs.lastName) return true;
            if (lhs.PIN < rhs.PIN) return true;
            return false;
        }
    };

    typedef std::set<Student, ValidateStudent::StudentComparator> Students;

public:
    void init(const char* filename)
    {
        if (filename)
        {
            std::fstream dataFile(filename, std::fstream::in);

            if (dataFile)
            {
                while (!dataFile.eof())
                {
                    Student student;

                    dataFile >> student.firstName >> student.lastName >> student.PIN;

                    if (dataFile.good())
                    {
                        students.insert(student);
                    }
                }
            }
            else
            {
                const std::string errorMsg = std::string("Unable to open file '") + filename + std::string("'.");
                throw std::runtime_error(errorMsg);
            }
        }
        else
        {
            const std::string errorMsg = std::string("No file given!");
            throw std::runtime_error(errorMsg);
        }
    }

    void debug() const
    {
        for (Students::const_iterator it = students.begin(); it != students.end(); ++it)
        {
            std::cout << it->firstName << "\t\t" << it->lastName << "\t\t" << it->PIN << std::endl;
        }
    }

    void getStudentInfo() const
    {
        std::string firstName, lastName, PIN;

        std::cout << "\n\n";
        std::cout << "Enter first name: ";
        std::getline(std::cin, firstName);
        std::cout << "Enter last name: ";
        std::getline(std::cin, lastName);
        std::cout << "Enter PIN: ";
        std::getline(std::cin, PIN);

        std::cout << "> You are" << (validStudent(firstName, lastName, PIN) ? "" : " NOT") << " a valid student." << std::endl;
    }

private:
    bool validStudent(const std::string& firstName, const std::string& lastName, const std::string& PIN) const
    {
        for (Students::const_iterator it = students.begin(); it != students.end(); ++it)
        {
            if (it->firstName == firstName && it->lastName == lastName && it->PIN == PIN) return true;
        }

        return false;
    }

    Students students;
};

int main(int argc, char** argv)
{
    if (argc != 2)
    {
        std::cerr << "Usage: " << argv[0] << " <student data file>" << std::endl;
        return -1;
    }

    try
    {
        ValidateStudent validate;

        validate.init(argv[1]);

        for (;;)
        {
            validate.getStudentInfo();
        }
    }
    catch (std::exception& e)
    {
        std::cerr << "Caught Exception: " << e.what() << std::endl;
        return -1;
    }
}

```

You should also avoid reading an int value as raw input.  Always read into a string, then convert to a number if necessary.  You will notice that in my example program above, it was not necessary to declare the PIN as an int; mathematical operations will not be performed on such.

---

### Post by sixstorm on 2013-01-27
> **dwhitney67 said:**
> Your code has some basic errors in it.  Start off by placing your declarations in the proper order (hint: Student and then set).

Here's a working program that does not meet all of your application's requirements, but demonstrates the basics of the usage of an STL set.
```
code

```

You should also avoid reading an int value as raw input.  Always read into a string, then convert to a number if necessary.  You will notice that in my example program above, it was not necessary to declare the PIN as an int; mathematical operations will not be performed on such.

Wow, you totally re-wrote the program!  I'll be honest and say that I'm confused by reading this but I'll try to decode it.

I actually tried to declare the Student class before the set, but still get a crazy load of errors.  I'll keep chopping away at it.

---

