---
title: "g++ saying Syntax is wrong"
date: 2007-12-13
forum: Programming Talk
---

### Post by blastthisinferno on 2007-12-13
I am getting the following error with the given code, and I don't understand what the problem is.  I was wondering if anyone could help me understand what is wrong here.

```

g++ -Wall -c "programInfo.cpp" (in directory: /home/erich/Code)
programInfo.h:8: error: 'string' does not name a type
programInfo.h:9: error: 'string' does not name a type
programInfo.h:10: error: 'string' does not name a type
/usr/include/sys/utsname.h:28: error: expected unqualified-id before string constant
programInfo.cpp:20: error: no 'std::string programInfo::getTime()' member function declared in class 'programInfo'
Compilation failed.

```

This is my cpp class file "programInfo.cpp"
```

#include "programInfo.h"
#include <time.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/utsname.h>
#include <string>
#include <iostream>
#include <sstream>

using namespace std;

string programInfo::getTime(){
	time_t time_value = time(NULL);
	struct tm *time_struct = localtime(&time_value);
	int hour = time_struct->tm_hour;
	int minute = time_struct->tm_min;
	int second = time_struct->tm_sec;
	
	ostringstream str;
	str << hour << ":" << minute << ":" << second;
	string the_time = str.str();
	
	return the_time;
}

```

This is the header file for "programInfo"

```

#ifndef PROGRAM_INFO_H
#define PROGRAM_INFO_H

#include <string>

class programInfo{
public:
	string getName();
	string getTime();
	string getProcessId();
}
#endif

```

---

### Post by LaRoza on 2007-12-13
<snip />

I misread it.

---

### Post by slavik on 2007-12-13
are you sure it's not String? (capital s)

---

### Post by LaRoza on 2007-12-13
> **slavik said:**
> are you sure it's not String? (capital s)

In Java, capital, in C++, lowercase.

---

### Post by LaRoza on 2007-12-13
[php]
#ifndef PROGRAM_INFO_H
#define PROGRAM_INFO_H

#include <string>

class programInfo{
public:
	std::string getName();
	std::string getTime();
	std::string getProcessId();
}
#endif
[/php]

That solves everything but: "/usr/include/sys/utsname.h:28: error: expected unqualified-id before string constant"

---

### Post by public_void on 2007-12-13
Missing semi-colon at the end of the class
 
```
#ifndef PROGRAM_INFO_H
#define PROGRAM_INFO_H
 
#include <string>
 
class programInfo{
public:
    string getName();
    string getTime();
    string getProcessId();
}; <-------
#endif
```

---

### Post by samjh on 2007-12-13
This will solve it:

```
  1 #ifndef PROGRAM_INFO_H
  2 #define PROGRAM_INFO_H
  3 
  4 #include <string>
  5 
  6 using std::string;
  7 
  8 class programInfo {
  9     public:
 10         string getName();
 11         string getTime();
 12         string getProcessId();
 13 };
 14 #endif
```

Notice the using std::string declaration, and the ; at the end of the class declaration.

---

### Post by iharrold on 2007-12-13
You might be able to save yourself some effort and formatting if you make use of the "ctime" and "time" libraries.  

Look into using:
char* [asctime ]("http://www.cplusplus.com/reference/clibrary/ctime/asctime.html")(const tm* ptm);
char* [ctime ]("http://www.cplusplus.com/reference/clibrary/ctime/ctime.html")(const time_t* t);

Perhaps something like, otherwise your approach allows you to configure and interpret however you like, which may work best for you, so take this as just a helpful suggestion.  I think the others fixed your bugs for you.:

```

#ifndef PROGRAM_INFO_H
#define PROGRAM_INFO_H
 
#include <string>

class programInfo{
public:
	std::string getName();
	std::string getTime();
	std::string getProcessId();
};
#endif
```

```

#include "programInfo.h"
#include <time.h>
#include <ctime.h>
#include <string>

using namespace std;

string programInfo::getTime()
{
	time_t time_value = time(NULL);
	tm *time_struct = localtime(&time_value);
        string temp_string(asctime(time_struct));
               // output is <day> <Month> <day number> <hour>:<minutes>:<seconds> <year>
	return temp_string;
}
```

[edit2]Eeek... my mistake.... forget what I wrote earlier about forward declaration.  Samjh didn't forward declare.

---

### Post by psusi on 2007-12-13
> **samjh said:**
> This will solve it:

```
  1 #ifndef PROGRAM_INFO_H
  2 #define PROGRAM_INFO_H
  3 
  4 #include <string>
  5 
  6 using std::string;
  7 
  8 class programInfo {
  9     public:
 10         string getName();
 11         string getTime();
 12         string getProcessId();
 13 };
 14 #endif
```

Notice the using std::string declaration, and the ; at the end of the class declaration.

Do NOT place using declarations in header files, as they pollute the namespace of all files that include it.

---

### Post by samjh on 2007-12-13
> **psusi said:**
> Do NOT place using declarations in header files, as they pollute the namespace of all files that include it.

Eeck.  Shows my lack of experience in C++. :(

std::string it is then. :)

---

### Post by psusi on 2007-12-13
Yea, this is pretty much the entire point of namespaces.  YOUR header might use std::string, but some other header may use some other string in some other namespace.  By having them in different namespaces, a program can include both headers and use both.  If the program wants to use foo::string then it can use a using declaration to make that the default, while still being able to make use of the things in your header which use std::string.

---

### Post by blastthisinferno on 2007-12-13
Thank you for all the replies.  What fixed it was:

```

#ifndef PROGRAM_INFO_H
#define PROGRAM_INFO_H

#include <string>

class programInfo{
public:
	std::string getName();
	std::string getTime();
	std::string getProcessId();
};
#endif

```

---

