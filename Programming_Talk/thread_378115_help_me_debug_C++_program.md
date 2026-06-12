---
title: "help me debug C++ program"
date: 2007-03-06
forum: Programming Talk
---

### Post by stealth75711 on 2007-03-06
```
#include <iostream>
using namespace std;

int main()
{
	int numStudents,
		numTests,
		total;
	double average;
	
	cout<<"This program averages test scores.\n";
	cout<<"For how many students do you have test scores? ";
	cin >> numStudents;
	
	cout<<"How many test scores does each student have? ";
	cin >> numTests;
	
	for (int student = 1; student <= numStudents; student++)
	{
		total = 0;
		for (int test = 1; test <= numTests; test++)
		{
			int score;
			cout<< "Enter score " <<test<< " for ";
			cout<<"student " << student << ": ";
			cin >> score;
			total += score;
		}
		average = total / numTests;
		cout << "The average score for student " << student;
		cout << " is" <<average<< ". \n\n";
	}
	return 0;
}

```


// When i go to compile it via the terminal i get this error

 g++ testscores.cpp -o testscores
testscores.cpp:36:3: warning: no newline at end of file

// Anyone know whats wrong?

---

### Post by hod139 on 2007-03-06
> **stealth75711 said:**
> 
// When i go to compile it via the terminal i get this error

 g++ testscores.cpp -o testscores
testscores.cpp:36:3: warning: no newline at end of file

// Anyone know whats wrong?

This isn't an error, it's a warning.  Also, it tells you what the problem is, "warning: no newline at end of file".  To fix, go to the last character of the last line of your file, and press enter.  The last line of a source file should be a blank line is all.

---

### Post by stealth75711 on 2007-03-06
Wow what a eronous thing to try to fix
it works now thanks for tip

---

### Post by thumper on 2007-03-06
C'mon what were you expecting?

Not only did it tell you what the problem was, but the line and character number too.

Just wait until you try to understand the compile errors for templated meta-programming.

---

### Post by g3k0 on 2007-03-06
logic errors caused by pointers are fun too =)  You never know what your gonna get

---

### Post by rplantz on 2007-03-07
> **thumper said:**
> C'mon what were you expecting?

Not only did it tell you what the problem was, but the line and character number too.

Just wait until you try to understand the compile errors for templated meta-programming.

As many on this forum know, I was a CS professor for 21 years. This sort of thing was very common in lab. Students would call me over to help them debug their program, and I simply read what was printed on the screen for them. :)

And when you get the compile errors all fixed, wait until you have to deal with code that seems to break randomly. Personally, I think it's great fun.

---

