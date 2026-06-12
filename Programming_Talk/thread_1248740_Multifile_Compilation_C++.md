---
title: "Multifile Compilation C++"
date: 2009-08-24
forum: Programming Talk
---

### Post by meteo666 on 2009-08-24
Hi,
I started to study C++ from a book...
I need to write a simple program which contains 3 files:
1.h, 1.cpp, m1.cpp

1.h:
```

#ifndef 1_H_
#define 1_H_
#include <string>
class bankAccount
{
    private:
        string name;
        string accountNo;
        float balance;
    public:
        bankAccount();
        ~bankAccount();
        void display();
        void deposite(float);
        void withdraw(float);
};
#endif

```

1.cpp:
```

#include <iostream>
#include "1.h"

bankAccount::bankAccount(){
    using std::cout;
    cout << "OBJECT CREATED\n";
}

bankAccount::~bankAccount(){
    using std::cout;
    cout << "OBJECT DELETED\n";
}

void bankAccount::display(){
    using std::cout;
    cout << "name " << name << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    cout << "account no: " << accountNo << std::endl;    
}

void bankAccount::deposite(float m){
    using std::cout;
    cout << "DEPOSITE: " << m << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    balance+=m;
    cout << "NEW BALANCE: " << balance << std::endl;    
}

void bankAccount::withdraw(float m){
    using std::cout;
    cout << "WITHDRAW: " << m << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    balance-=m;
    cout << "NEW BALANCE: " << balance << std::endl;    
}

```

m1.cpp:
```

#include "1.h"

int main(){

bankAccount bA =  bankAccount();
bA.display();

return 0;
}

```

The problem is I can't create an executable from those files...
I tried 
  g++ -o m1 m1.cpp 1.cpp
and
  gcc -c 1.cpp
  gcc -c m1.cpp
  gcc -o m1 m1.o 1.o

I get this errors:
```

In file included from m1.cpp:2:
1.h:2:9: error: macro names must be identifiers
m1.cpp: In function ‘int main()’:
m1.cpp:6: error: ‘bankAccount’ was not declared in this scope
m1.cpp:6: error: expected `;' before ‘bA’
m1.cpp:7: error: ‘bA’ was not declared in this scope
In file included from 1.cpp:3:
1.h:2:9: error: macro names must be identifiers
1.cpp:5: error: ‘bankAccount’ has not been declared
1.cpp:5: error: ISO C++ forbids declaration of ‘bankAccount’ with no type
1.cpp:10: error: expected constructor, destructor, or type conversion before ‘::’ token
1.cpp:15: error: ‘bankAccount’ is not a class or namespace
1.cpp: In function ‘void display()’:
1.cpp:17: error: ‘name’ was not declared in this scope
1.cpp:18: error: ‘balance’ was not declared in this scope
1.cpp:19: error: ‘accountNo’ was not declared in this scope
1.cpp: At global scope:
1.cpp:22: error: ‘bankAccount’ is not a class or namespace
1.cpp: In function ‘void deposite(float)’:
1.cpp:25: error: ‘balance’ was not declared in this scope
1.cpp: At global scope:
1.cpp:30: error: ‘bankAccount’ is not a class or namespace
1.cpp: In function ‘void withdraw(float)’:
1.cpp:33: error: ‘balance’ was not declared in this scope

```

I googled 'macro names must be identifiers' but cant find anything usefull
when I combine all 3 into 1 file I can compile it

---

### Post by WitchCraft on 2009-08-24
```

g++ file1.cpp file2.cpp file3.cpp fileN.cpp -o executablename

```

you need to include the function definitions of file1.cpp in file1.h and include file1.h in file2.cpp and file3.cpp and so on.

Your sources contain classes.
Only C++ supports classes, so you need to compile with g++ and not with gcc...

---

### Post by WitchCraft on 2009-08-24
Oh, I forgot: add -Wall, to have all warnings


and use a makefile/sconstruct file:

SConstruct
```

# This is a comment
import glob

env = Environment()   # Create an environmnet
env.Program(target = "helloworld", source = glob.glob('*.cpp'))

```

To make the program: scons
To make clean: scons -c

To get scons: apt-get install scons

So install scons, copy paste the code above in an empty text file, rename it to SConstruct, then change to the directory where SConstruct is in and type: scons

This will compile all .cpp files in this folder and create an executable called "helloworld"

---

### Post by meteo666 on 2009-08-24
you mean cut and paste 1.cpp into 1.h and than include 1.h into m1.cpp, I think... but the book says NO, you must separate them

class decleration must be in separate files and its methods implementations must be in another file

I get errors for this file too
m1.cpp
```

#include <iostream>
#include <string>
class bankAccount
{
    private:
        string name;
        string accountNo;
        float balance;
    public:
        bankAccount();
        ~bankAccount();
        void display();
        void deposite(float);
        void withdraw(float);
};

bankAccount::bankAccount(){
    using std::cout;
    cout << "OBJECT CREATED\n";
}

bankAccount::~bankAccount(){
    using std::cout;
    cout << "OBJECT DELETED\n";
}

void bankAccount::display(){
    using std::cout;
    cout << "name " << name << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    cout << "account no: " << accountNo << std::endl;    
}

void bankAccount::deposite(float m){
    using std::cout;
    cout << "DEPOSITE: " << m << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    balance+=m;
    cout << "NEW BALANCE: " << balance << std::endl;    
}

void bankAccount::withdraw(float m){
    using std::cout;
    cout << "WITHDRAW: " << m << std::endl;
    cout << "CURRENT BALANCE: " << balance << std::endl;
    balance-=m;
    cout << "NEW BALANCE: " << balance << std::endl;    
}

int main(){

bankAccount bA =  bankAccount();
bA.display();

return 0;
}

```errors ( g++ m1.cpp -o m1 )
```

m1.cpp:8: error: &#8216;string&#8217; does not name a type
m1.cpp:9: error: &#8216;string&#8217; does not name a type
m1.cpp: In member function &#8216;void bankAccount::display()&#8217;:
m1.cpp:31: error: &#8216;name&#8217; was not declared in this scope
m1.cpp:33: error: &#8216;accountNo&#8217; was not declared in this scope

```I changed the <string> to <string.h> but nothing changed...
(also <cstring> gave the same error)

---

### Post by dribeas on 2009-08-24
> **meteo666 said:**
> 
1.h:
```

#ifndef 1_H_
#define 1_H_
// ...
#endif

```

I get this errors:
```

In file included from m1.cpp:2:
1.h:2:9: error: macro names must be identifiers

```


The error is quite clear there: macro names must be identifiers (line 2, character 9 and on: "1_H_"). If you check your preferred C++ book (or online resource) for the definition of valid identifiers you will find out that digits are valid characters **inside** an identifier but not as the beginning character of one.

To complete the answer: Valid identifiers start with either _ or a letter (upper/lower case) an can contain any letter, digit or underscore (_) in subsequent positions. The underscore character is special in that identifiers begining with double underscore __, or single underscore followed by a capital letter are reserved for the implementation (compiler+standard library), and identifiers starting with a single underscore followed by a lower case letter in the global namespace are reserved, again, for the library implementor.

---

### Post by meteo666 on 2009-08-24
ahh right... :(

and I fixed the string problem as adding 'std::' before them

thanks

---

### Post by dribeas on 2009-08-24
> **meteo666 said:**
> y
m1.cpp
```

#include <iostream>
#include <string>
class bankAccount
{
    private:
        string name;
// ...
};

```errors ( g++ m1.cpp -o m1 )
```

m1.cpp:8: error: ‘string’ does not name a type


Standard library facilities are defined inside the std namespace. Add that to your string declarations:

[CODE]
#include <iostream>
#include <string>
class bankAccount
{
private:
   std::string name;
// ...
};

```

I believe the rest of the errors are just due to that first problem. Note that you can employ the using declaration (using namespace std) to bring all names from the std namespace into scope. This is recommended by some and despised by others due to 'namespace pollution' (can create name collisions from identifiers in different namespaces). At any rate, whether or not you use it inside your implementation files (.cpp) you should NEVER use the 'using directive' in header files.

---

### Post by meteo666 on 2009-08-24
thanks  dribeas, witchcraft

---

### Post by WitchCraft on 2009-08-24
> **meteo666 said:**
> 
you mean cut and paste 1.cpp into 1.h and than include 1.h into m1.cpp, I think... but the book says NO, you must separate them

class decleration must be in separate files and its methods implementations must be in another file


No, I meant write the class DECLARATION for class1.cpp in class1.h
and then go to the file class2.cpp and add #include "class1.h", and then go to class3.cpp and add #include "class1.h", and so on.
That's just what your book is trying to say.

But anyway, your problem is solved.

By the way: sooner or later you will have to link something, eg. when you use math functions in gcc.

The syntax for this is: 
gcc file1.c file2.c file3.c filen.3 -lm -o outputfile

note the -l switch, which means link library m[ath] in the executable.

And note that this works the same way for g++.

---

