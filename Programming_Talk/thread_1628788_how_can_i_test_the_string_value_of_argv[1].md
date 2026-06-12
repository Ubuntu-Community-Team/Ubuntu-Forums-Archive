---
title: "how can i test the string value of argv[1]"
date: 2010-11-23
forum: Programming Talk
---

### Post by Søren on 2010-11-23
i want to test the second element of the *argv[] vector that gets passed from the command line as a string. example: 

```
#include <cstdlib> 
#include <iostream> 

int main ( int argc, char *argv[] ) 

 { 
      
 
 if ( argv[1] = "yes" ) 
 {
 std::cout << "argv[1] is yes" << std::endl; 
 }
  if ( argv[1] = "no" ) 
 {
 std::cout << " argv[1] is no" << std::endl;  
 } 
  return 0; 
 } 
```

when i run this in the terminal it executes both of these function regardless of what i type as the second parameter. for example if i type ```
./a.out dffdf dfadfasdd adsfsd
``` it will still display both the cout statements. confused.

---

### Post by Arndt on 2010-11-23
> **Søren said:**
> i want to test the second element of the *argv[] vector that gets passed from the command line as a string. example: 

```
#include <cstdlib> 
#include <iostream> 

int main ( int argc, char *argv[] ) 

 { 
      
 
 if ( argv[1] = "yes" ) 
 {
 std::cout << "argv[1] is yes" << std::endl; 
 }
  if ( argv[1] = "no" ) 
 {
 std::cout << " argv[1] is no" << std::endl;  
 } 
  return 0; 
 } 
```

when i run this in the terminal it executes both of these function regardless of what i type as the second parameter. for example if i type ```
./a.out dffdf dfadfasdd adsfsd
``` it will still display both the cout statements. confused.

You need to look closely at the difference between the = and == operators.

I also suggest you use the flag -Wall when compiling. It will say something about string constant conversion, which you can suppress if you know what you are doing, and also this, which is a typical hint of the mistake you've made (and which everyone keeps making now and then):

```
prog.cc:9: warning: suggest parentheses around assignment used as truth value
```

---

### Post by Søren on 2010-11-23
ok thanks. after changing them to "==" it did not execute the if statements. but stilll the problem of not testing the string is there. is i type ```
./a.out yes
``` it will just skip both if statements.

code i have now is: 
```

#include <cstdlib> 
#include <iostream> 

int main ( int argc, char *argv[] ) 

 { 
      
 
 if ( argv[1] == "yes" ) 
 {
 std::cout << "argv[1] is yes" << std::endl; 
 }
  if ( argv[1] == "no" ) 
 {
 std::cout << " argv[1] is no" << std::endl;  
 } 
  return 0; 
 } 
```

---

### Post by Barrucadu on 2010-11-23
You can't compare strings that way, you need to use strcmp.

---

### Post by Arndt on 2010-11-23
You should also check that there actually is anything in argv[1]. There won't be if you don't give any command line arguments. Check the value of argc.

To make the compiler give you a warning about not using 'argc' (it's there, and it's relevant, so you should use it), compile with -Wunused-parameter.

---

### Post by psavva on 2010-11-23
> **Søren said:**
> i want to test the second element of the *argv[] vector that gets passed from the command line as a string. example: 

```
#include <cstdlib> 
#include <iostream> 

int main ( int argc, char *argv[] ) 

 { 
      
 
 if ( argv[1] = "yes" ) 
 {
 std::cout << "argv[1] is yes" << std::endl; 
 }
  if ( argv[1] = "no" ) 
 {
 std::cout << " argv[1] is no" << std::endl;  
 } 
  return 0; 
 } 
```

when i run this in the terminal it executes both of these function regardless of what i type as the second parameter. for example if i type ```
./a.out dffdf dfadfasdd adsfsd
``` it will still display both the cout statements. confused.

Have a look at an example:
```
#include <iostream> //For cout
#include <cstring>  //For the string functions

using namespace std;

int main()
{
  char name[50];
  char lastname[50];
  char fullname[100]; // Big enough to hold both name and lastname
  
  cout<<"Please enter your name: ";
  cin.getline ( name, 50 );
  if ( strcmp ( name, "Julienne" ) == 0 ) // Equal strings
    cout<<"That's my name too.\n";
  else                                    // Not equal
    cout<<"That's not my name.\n";
  // Find the length of your name
  cout<<"Your name is "<< strlen ( name ) <<" letters long\n";
  cout<<"Enter your last name: ";
  cin.getline ( lastname, 50 );
  fullname[0] = '\0';            // strcat searches for '\0' to cat after
  strcat ( fullname, name );     // Copy name into full name
  strcat ( fullname, " " );      // We want to separate the names by a space
  strcat ( fullname, lastname ); // Copy lastname onto the end of fullname
  cout<<"Your full name is "<< fullname <<"\n";
  cin.get();
}

```

---

### Post by ziekfiguur on 2010-11-23
> **Barrucadu said:**
> You can't compare strings that way, you need to use strcmp.

He's using C++, not C, so he can (and should).

---

### Post by Søren on 2010-11-23
thank you all!! got it to work.

```
#include <cstdlib> 
#include <iostream> 
#include <string.h> 

int main ( int argc, char *argv[] ) 

 { 
     
	if  (strcmp(argv[1], "yes") != 0) 
{
 std::cout << "no " << std::endl; 	
}	

	if  (strcmp(argv[1], "yes") == 0) 
{
 std::cout << "yes" << std::endl; 	
}	
 
  return 0; 
 }
```

---

### Post by Søren on 2010-11-23
> **ziekfiguur said:**
> He's using C++, not C, so he can (and should).

does that mean i did it the wrong way? :(

---

### Post by ziekfiguur on 2010-11-23
> **Søren said:**
> does that mean i did it the wrong way? :(

Sorry, but yes.
First, when using c++ it's preferred to use std::string objects instead of char *. std::string have an overloaded == operator that you can use. strcmp is potentially dangerous when your strings don't end with a \0 character. That won't be a problem here, but it's still better not to use it if it's not necessary.

A better way would be:
```

#include <iostream> 
#include <string> // this defines std::string, not that this is NOT the same as the cstring header

int main ( int argc, char *argv[] ) 

 { 
      
 if (argc > 1)
 {
     if ( std::string(argv[1]) == "yes" ) 
     {
     std::cout << "argv[1] is yes" << std::endl; 
     }
      if ( std::string(argv[1]) == "no" ) 
     {
     std::cout << " argv[1] is no" << std::endl;  
     } 
 }
  return 0; 
 }

```

Second, when using C++ you should never include the C headers like string.h, but their C++ equivalent like cstring.

---

### Post by Søren on 2010-11-23
thank you, that helped a lot.

---

