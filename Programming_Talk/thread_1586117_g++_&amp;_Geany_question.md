---
title: "g++ &amp; Geany question"
date: 2010-10-01
forum: Programming Talk
---

### Post by akvino on 2010-10-01
This works:
g++ dchecks.cpp main.cpp -o dchecks

This doesn't:
g++ -Wall dchecks.cpp main.cpp -o dchecks

dchecks.cpp: In constructor ‘DChecks::DChecks(char, char)’:
dchecks.cpp:10: warning: unused variable ‘admin’
dchecks.cpp:11: warning: unused variable ‘server’

Same happens in Geany - it complains when building with -Wall switch. 
My two questions:
1) Why won't -Wall work?
2) How do you make code posted work with -Wall?


I just built a base for my methods:

[PHP]
#ifndef DCHECKS_H
#define DCHECKS_H



class DChecks{
	
	public:
		DChecks();
		DChecks(char ad, char serv);
		~DChecks();
		void addAdmin();
		void rotateAdmin();
		void addServer();
		void emailAdmin();

		

	private:
		char admin[];
		char server;
		
};

#endif
[/PHP]


[PHP]#include <iostream>
#include "dchecks.h"
using std::cout;

DChecks::DChecks(){}

DChecks::DChecks(char ad, char serv){

	std::cout<<"\nDCheck constructor called"<<std::endl;
	char admin[30] = "admin";
	char server[30] = "server";
	
}

void DChecks::addAdmin(){
	
	std::cout <<"\nDChecks::addAdmin function"<<std::endl;
}

void DChecks::rotateAdmin(){
	cout<<"\nDChecks::rotateAdmin function"<<std::endl;
}

void DChecks::addServer(){
	cout<<"\nDChecks::addServer function"<<std::endl;
}

void DChecks::emailAdmin(){
	cout<<"\nDChecks::emailAdmin function"<<std::endl;
}

DChecks::~DChecks(){}
[/PHP]




[PHP]
#include <iostream>
#include "dchecks.h"


int main(){

	
	DChecks d1;
	d1.addAdmin();
	d1.rotateAdmin();
	d1.emailAdmin();
	d1.addServer();
	

	return 0;
}
[/PHP]

---

### Post by spjackson on 2010-10-01
> **akvino said:**
> This works:
g++ dchecks.cpp main.cpp -o dchecks

This doesn't:
g++ -Wall dchecks.cpp main.cpp -o dchecks

dchecks.cpp: In constructor ‘DChecks::DChecks(char, char)’:
dchecks.cpp:10: warning: unused variable ‘admin’
dchecks.cpp:11: warning: unused variable ‘server’

Same happens in Geany - it complains when building with -Wall switch. 
My two questions:
1) Why won't -Wall work?
2) How do you make code posted work with -Wall?

-Wall does work. It warns you of things that might be wrong with your code. In this case...
> 
```

DChecks::DChecks(char ad, char serv){

    std::cout<<"\nDCheck constructor called"<<std::endl;
    char admin[30] = "admin";
    char server[30] = "server";
    
}

```This creates 2 local variables, sets them, then throws them away on return from the constructor. So, -Wall is warning you that these variables are unused.

What you probably mean is to set the private members of the same name, e.g.
```

DChecks::DChecks(char ad, char serv){

    std::cout<<"\nDCheck constructor called"<<std::endl;
    admin = "admin";
    server = "server";
    
}

```However, this won't work given your declaration of the private members. You need to work out what you mean them to be (hint std::string). If they are fixed size character arrays, then you either strcpy/strncpy here, or if you want initialiser syntax, then it would be something like
```

 DChecks::DChecks(char ad, char serv)
    : admin("admin"), server("server")
{
     std::cout<<"\nDCheck constructor called"<<std::endl;    
 }
 
```

---

### Post by unknownPoster on 2010-10-01
It's not broken. -Wall is a compiler flag which stands for "Warnings All." You could possibly have error free code with a lot of warnings. These warnings might not cause errors, but some times they can.

> 
-Wall
This enables all the warnings about constructions that some users consider questionable, and that are easy to avoid (or modify to prevent the warning), even in conjunction with macros. This also enables some language-specific warnings described in C++ Dialect Options and Objective-C and Objective-C++ Dialect Options.
-Wall turns on the following warning flags:

          -Waddress   
          -Warray-bounds (only with -O2)  
          -Wc++0x-compat  
          -Wchar-subscripts  
          -Wenum-compare (in C/Objc; this is on by default in C++) 
          -Wimplicit-int (C and Objective-C only) 
          -Wimplicit-function-declaration (C and Objective-C only) 
          -Wcomment  
          -Wformat   
          -Wmain (only for C/ObjC and unless -ffreestanding)  
          -Wmissing-braces  
          -Wnonnull  
          -Wparentheses  
          -Wpointer-sign  
          -Wreorder   
          -Wreturn-type  
          -Wsequence-point  
          -Wsign-compare (only in C++)  
          -Wstrict-aliasing  
          -Wstrict-overflow=1  
          -Wswitch  
          -Wtrigraphs  
          -Wuninitialized  
          -Wunknown-pragmas  
          -Wunused-function  
          -Wunused-label     
          -Wunused-value     
          -Wunused-variable  
          -Wvolatile-register-var 
          
     
Note that some warning flags are not implied by -Wall. Some of them warn about constructions that users generally do not consider questionable, but which occasionally you might wish to check for; others warn about constructions that are necessary or hard to avoid in some cases, and there is no simple way to modify the code to suppress the warning. Some of them are enabled by -Wextra but many of them must be enabled individually. 


[http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Warning-Options.html)

---

### Post by akvino on 2010-10-01
Thanks all.

---

