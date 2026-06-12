---
title: "C++ Map Help"
date: 2007-04-09
forum: Programming Talk
---

### Post by YourFriendlyGopher on 2007-04-09
Hi everyone,

I'm having some problems with a static map variable in C++. It is declared as:

```

#include <map>
using std::map;
...
#ifndef STUDENT_H
#define STUDENT_H

class Student {
...
private:
    static map<string, unsigned int> nameList;
};
#endif

```

Now, when I try to use it in a private function of the class Student...

```

    // Check if initials are present in map and either set
    // count to 1 or increment the key.
    if( nameList.find(truncName) == nameList.end() )
        nameList[truncName] = 1;
    else
        ++nameList[truncName];

```

...it gives me this error when compiling:

```

Student.o: In function `Student::generateUsername()':Student.cpp:38: undefined reference to `Student::nameList'
:Student.cpp:38: undefined reference to `Student::nameList'
:Student.cpp:39: undefined reference to `Student::nameList'
:Student.cpp:41: undefined reference to `Student::nameList'
:Student.cpp:43: undefined reference to `Student::nameList'
collect2: ld returned 1 exit status
make: *** [CreateUserAccounts] Error 1

```

My makefile:

```

# Makefile
#

CC = g++
LIBS = -g -Wall

Main: Student.o Main.o
    $(CC) $(LIBS) -o Main Student.o Main.o

Main.o: Main.cpp
    $(CC) $(LIBS) -c Main.cpp

Student.o: Student.cpp
    $(CC) $(LIBS) -c Student.cpp

all:
    make clean

clean:
    rm *.o

```

What I'm trying to do is count the amount of people who have the same initials across the class Student, hence the static variable. If anyone can help with this, it'd be much appreciated, thanks :).

---

### Post by DoubleQuadword on 2007-04-09
Try to do this:

```

// In your CPP, outside a function scope...

map<string, unsigned int> Student::nameList;

// Your definitions.

```

Regards.

---

### Post by YourFriendlyGopher on 2007-04-09
Still having the same problem :(

EDIT: Ok that may have actually solved the problem (forgot to remove the static keyword), just gotta do some testing to make sure..

---

### Post by DoubleQuadword on 2007-04-09
Indeed, I forgot to tell you that.

Regards.

---

### Post by YourFriendlyGopher on 2007-04-09
Alright I tested it and it looks like each Student object is creating its own copy of the map, which isn't what I want. Here's what I did to test that:

```

    if( Student::nameList["test"] == 10 )
    {
        std::cout << "Equals 10!" << std::endl;
    }
    else {
        std::cout << "Doesn't equal 10!" << std::endl;
        Student::nameList["test"] = 10;
    }

```

This piece of code is called every time a Student is created, so, if I understand correctly, the second time this is called the value of nameList["test"] should be 10. This doesn't happen so I'm guessing it isn't working. So, any more ideas?

---

### Post by YourFriendlyGopher on 2007-04-09
Bump before bed..

---

### Post by WW on 2007-04-09
Did you remove the keyword "static" from the declaration of nameList inside the class?  If so, put it back.  E.g.
```

class Student {
...
private:
    static map<string, unsigned int> nameList;
};

```
and somewhere else (not in a header)
```

map<string,unsigned int> Student::nameList;

```

---

### Post by duff on 2007-04-09
> **YourFriendlyGopher said:**
> EDIT: Ok that may have actually solved the problem (forgot to remove the static keyword), just gotta do some testing to make sure..

You left "static" in the class definition, correct?

should look something like this:
```

#include <map>
#include <string>
#include <iostream>

// This stuff should be in Student.h
struct Student
{
	Student() {
		if(list["test"] == 10 ) {
			std::cout << "Equals 10!" << std::endl;
		}
		else {
			std::cout << "Doesn't equal 10!" << std::endl;
			list["test"] = 10;
		}
	}

	static std::map<std::string, unsigned> list;
};

// This line should be in Student.cpp
std::map<std::string, unsigned> Student::list;

int main(int argc, char *argv[])
{
	Student x,y;
}
```
(this will compile and run correctly).

---

### Post by YourFriendlyGopher on 2007-04-10
Ah, I see now. I got a bit confused as to where to put that. Seems to be working fine now, thanks for the help everyone :).

---

