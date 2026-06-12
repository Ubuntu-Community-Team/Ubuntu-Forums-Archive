---
title: "[SOLVED] char array"
date: 2007-08-31
forum: Programming Talk
---

### Post by urgo on 2007-08-31
Hello,
I have the function which should get the path to the file.
The result from inside and outside the function I print on the screen.

I have file.cc

```

#include "file.h"

char ficonf::address[] = "configure";
char ficonf::datafile[] = "data";
char ficonf::cfile[80];
char ficonf::dfile[80];

char * fiop::getaddress(char * file)
{
    char whoami[20];
    char where[80] = "/home/";
    char surfix[] = "/.gkatalog/";
    system("whoami > .gkatalog_user_info.tmp");
    ifstream who(".gkatalog_user_info.tmp");
    who.getline(whoami, 20);
    who.close();
    system("rm .gkatalog_user_info.tmp");
    strcat(where, whoami);
    strcat(where, surfix);
    strcat(where, file);    
    cout << "getaddress: " << where << endl;
    return where;
}

```

and file.h

```

#include <unistd.h>
#include <iostream>
#include <fstream>
using namespace std;

class fiop
{
public:
    static char * getaddress(char *);
};

class ficonf
{
friend class fiop;    
public:
    static char address[];
    static char datafile[];
    static char cfile[80];
    static char dfile[80];
};

```

and I check that fubction:

```

#include "file.h"

int main (int argc, char *argv[])
{
    strcpy(ficonf::cfile,fiop::getaddress(ficonf::address));
    strcpy(ficonf::dfile,fiop::getaddress(ficonf::datafile));
    cout << "cfile: "; cout << ficonf::cfile << endl;
    cout << "dfile: "; cout << ficonf::dfile << endl;

    return 0;
}

```

result is like below

```

getaddress: /home/urgo/.gkatalog/configure
getaddress: /home/urgo/.gkatalog/data
cfile: /home/urgo/.gkatH"&#65533;&#65533;&#65533;&#65533;figuy&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;
dfile: /home/urgo/.gkatalog/data

```

why ?

---

### Post by aks44 on 2007-08-31
Since you're using C++, get rid of those awful char* and use std::string instead. That will probably solve your problem (I didn't bother to really check the code, as char* C-strings are too error-prone to even deserve any attention in C++).

---

### Post by Chickencha on 2007-08-31
I think I might see your problem.  In the function getaddress, you're returning where, which is a local variable within the getaddress function.  After the getaddress function has completed, the data pointed to by where is no longer in scope.

There are a number of approaches to solving this problem.  You could take the advice of the poster above and just use std::string, which is a fine solution.

If you want to continue using character arrays, you could simply declare where as a pointer and malloc the amount of memory you want, then return where.  You'd then have to store the returned pointer somewhere and free it afterwards.

---

### Post by Wybiral on 2007-08-31
> **aks44 said:**
> Since you're using C++, get rid of those awful char* and use std::string instead. That will probably solve your problem (I didn't bother to really check the code, as char* C-strings are too error-prone to even deserve any attention in C++).

In this situation, I agree... I would use strings. C++ provides them, no use writing your own methods to handle strings.

(but I disagree with "C++"ers completely shunning the use of arrays and memory management all together... Sometimes you need to. Just not in this case).

---

### Post by PaulFr on 2007-08-31
Amen to all of the above calls for std::string, just a comment on the **system()** calls - please consider **popen** as an alternative.

---

### Post by aks44 on 2007-08-31
> **Wybiral said:**
> I disagree with "C++"ers completely shunning the use of arrays and memory management all together...

IMHO this is a misunderstanding, which comes from the fact that "unguarded" pointers (ie. pointers not wrapped in some sort of RAII class) are not exception-safe.


> **Chickencha said:**
> you could simply declare where as a pointer and malloc the amount of memory you want, then return where.  You'd then have to store the returned pointer somewhere and free it afterwards.

This kind of (incorrect) "solution" is the very reason why *manual* memory management (again, I really mean *unmanaged pointers*) is frowned upon in C++.

Consider the fix proposed by Chickencha, which I guess would go along those lines (changes in bold):

```
char * fiop::getaddress(char * file)
{
    char whoami[20];
    char surfix[] = "/.gkatalog/";
    [B]char home[] = "/home/";
    char* where = new char[80];
    strcpy(where, home);[/B]
    system("whoami > .gkatalog_user_info.tmp");
    ifstream who(".gkatalog_user_info.tmp");
    who.getline(whoami, 20);
    who.close();
    system("rm .gkatalog_user_info.tmp");
    strcat(where, whoami);
    strcat(where, surfix);
    strcat(where, file);    
    cout << "getaddress: " << where << endl;
    return where;
}

int main()
{
    **char* tmpadress =** fiop::getaddress(ficonf::address);
    strcpy(ficonf::cfile, **tmpadress**);
    **delete[] tmpadress;**
    return 0;
}
```

Not only fiop::getaddress() is still prone to a buffer overflow (as was the original version) but now it can also leak memory.

As long as ficonf::cfile (and ficonf::dfile) are statically sized arrays (not to mention the whoami and where arrays), nothing can really be done to fix the buffer overflow problem.

But more importantly (and to the point), the proposed "solution" just introduced another bug that most C++ beginners (as well as some seasoned C programmers that are not used to C++ exceptions) are not able to spot: any exception thrown between **new char[80]** and **return where;** (either by the std::ifstream or std::cout, in this example) will leak memory.

Granted both problems can be worked around with some effort and (IMHO) ugly code, but a RAII-style wrapper class is just safe *in all cases*, way simpler both to design & use, and even probably more performant altogether.


The fact is, exceptions are a C++ feature that has to be dealt with, and they render C-style memory management totally unsafe as soon as they come into play.


Now, a std::string version would get rid of both the buffer overflow and memory leak problems, and the resulting code would be way more understandable too.


EDIT: as a side note... ;)
```
class ficonf
{
public:
    static const char cfile[];
    static const char dfile[];
};
const char ficonf::cfile[] = "~/.gkatalog/configure";
const char ficonf::dfile[] = "~/.gkatalog/data";
```

---

### Post by urgo on 2007-09-01
Thank you for your help.

**Chickencha **- you have a right. There was the problem because of returning the local pointer - thank`s.

**PaulFr** - it is a good solution to use **popen**

my correct code:  :)

***file.cc***
```

#include "file.h"

char ficonf::address[] = "configure" ;
char ficonf::datafile[] = "data" ;
char ficonf::cfile[80] = "/home/";
char ficonf::dfile[80] = "/home/";

char * fiop::getaddress(char * file, char * where)
{
	char whoami[20] ;
	char surfix[] = "/.gkatalog/" ;
	FILE * strum = popen("whoami", "r") ;
	fgets(whoami,sizeof(whoami),strum) ;
	pclose(strum) ;
	char tmp[20] ;
	strlcpy(tmp,whoami) ;
	strcat(where, tmp);
	strcat(where, surfix) ;
	strcat(where, file) ;	
	cout << "getaddress: " << where << endl ;
	return where ;

```

***file.h***
```

#include <unistd.h>
#include <iostream>
#include <fstream>
#include <stdio.h>
#include "ustring.h"

using namespace std ;

class fiop
{
public:
	static char * getaddress(char *, char *) ;
};

class ficonf
friend class fiop ;	
public:
	static char address[] ;
	static char datafile[] ;
	static char cfile[80] ;
	static char dfile[80] ;
};

```

***ustring.cc***
```

void strlcpy(char * c, char * z)
{
	int i = 0 ,
		j = 0 ;
	do 
	{
		if (z[i] == '\n')
		{
		i++ ;
		}
		else 
		{
			c[j++] = z[i++] ;
		}	
	}
	while (c[i]);
}


```

***ustring.h***
```

void strlcpy(char *, char *) ;

```

and ***main.cc***
```

#include "file.h"
int main (int argc, char *argv[])
{
	char * cf = fiop::getaddress(ficonf::address,ficonf::cfile) ;
	char * df = fiop::getaddress(ficonf::datafile,ficonf::dfile) ;
	cout << "cfile: " ; cout << cf << endl;
	cout << "dfile: " ; cout << df << endl;
	
	return 0;
}

```

***result:***
```

getaddress: /home/urgo/.gkatalog/configure
getaddress: /home/urgo/.gkatalog/data
cfile: /home/urgo/.gkatalog/configure
dfile: /home/urgo/.gkatalog/data

```

---

