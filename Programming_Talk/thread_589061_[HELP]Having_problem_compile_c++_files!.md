---
title: "[HELP]Having problem compile c++ files!"
date: 2007-10-23
forum: Programming Talk
---

### Post by gtcoffee on 2007-10-23
i got the problem to compile these three files "GradeBook.h , GradeBook.cpp , and main.cpp ", but it can compiled by using VC++, How come?

```

g++ main.cpp -o main

/tmp/ccbwwwox.o: In function `main':
main.cpp:(.text+0xb7): undefined reference to `GradeBook::GradeBook(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)'
main.cpp:(.text+0x13d): undefined reference to `GradeBook::GradeBook(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)'
main.cpp:(.text+0x176): undefined reference to `GradeBook::displayMessage()'
collect2: ld returned 1 exit status

```

GradeBook.h

```

#include <string>

using namespace std;



class GradeBook

{

public:

	GradeBook( string );

	void setCourseName( string );

	string getCourseName();

	void displayMessage();

private:

	string courseName;

};

```

GradeBook.cpp

```

#include <iostream>

#include <string>

#include "GradeBook.h"
using namespace std;



GradeBook::GradeBook(string name)

{

	setCourseName(name);

}



void GradeBook::setCourseName(string name)

{

	courseName = name;



string GradeBook::getCourseName()

{

	return courseName;

}



void GradeBook::displayMessage()

{

	cout << "Welcome to the grade book for\n" << getCourseName()

		<< "!" << endl;

}


```

main.cpp

```

#include <iostream>
#include "GradeBook.h"

using namespace std;



int main()

{

	GradeBook gb1("CSC101 Introduction to programming in C++");

	GradeBook gb2("CSC102 Data Structures");



	gb1.displayMessage();

	return 0;

}

```

---

### Post by Wybiral on 2007-10-23
Try this:

```

g++ -c GradeBook.cpp -o GradeBook.o
g++ -c main.cpp -o main.o
g++ main.o GradeBook.o -o main

```

First you compile your object files, then you link them.

(even easier is to use a Makefile or BASH script to do this for you)

---

### Post by gtcoffee on 2007-10-23
Oh thanks Wybiral...now it works... ;)
btw, How to use Makefile ??

---

### Post by Wybiral on 2007-10-23
Make is really handy because it's smart enough to only compile the objects that you've changed the source for (which is a huge help when your project gets big enough to take an hour to compile). And anyone can go to the terminal and type "make".

Here's the manual: [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

But I bet you'll have better luck Googling for some examples.

---

### Post by slavik on 2007-10-24
on my system, even WINE takes like 5 minutes :P

[SIZE="1"]NOTE: quad core with 8GB of ram :)[/SIZE]

---

