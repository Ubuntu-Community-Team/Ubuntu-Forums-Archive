---
title: "C++ private string in class"
date: 2009-06-29
forum: Programming Talk
---

### Post by swappo1 on 2009-06-29
Hello,

I am trying to figure out how to declare a string as a private member of a class so I can use it in other member functions of that class.  Here is my code:
```

directory.cpp
#include <iostream>
#include <stdexcept>
#include "directory.h"
#include "unistd.h"

#define MAXPATHLEN 200

using namespace std;

Directory::Directory()
{
	char buf[MAXPATHLEN];
	if(getcwd(buf, MAXPATHLEN))
		get_path(buf);
	else
		throw domain_error("pathway not found");
}

void Directory::get_path(const char* s)
{
	string path = s;
	cout << path << endl;
}

directory.h
#ifndef DIRECTORY_H
#define DIRECTORY_H

class Directory
{
	private:
                [COLOR="Red"]string path; //here is where I would declare the string[/COLOR]
	public:
		Directory();
		void get_path(const char* s);

};
#endif
```
If I declare the string in Directory I would want to set it to buf in the constructor function and then be able to use it in other member functions.  I am not sure how to do this.

---

### Post by geirha on 2009-06-29
You are declaring a new variable called path in get_path. If you want to assign s to the member variable path, then lose the string keyword.
```
void Directory::get_path(const char* s)
{
	path = s;
	cout << path << endl;
}

```

---

### Post by dwhitney67 on 2009-06-29
A better method name would be set_path(), instead of get_path().

---

### Post by swappo1 on 2009-06-29
When I get rid of string I get the following error.
> g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
In file included from main.cpp:3:
directory.h:7: error: ‘string’ does not name a type
make: *** [main.o] Error 1


---

### Post by geirha on 2009-06-29
> **swappo1 said:**
> When I get rid of string I get the following error.

Ah, right, you haven't included any headers in your header file, and you should also add the namespace. So in short, #include <string> and std::string path;

---

### Post by MadCow108 on 2009-06-29
use std::string in Directory.h

---

### Post by swappo1 on 2009-06-29
Thanks.  Its been awhile since using header files.

---

