---
title: "Using private headers/libraries g++"
date: 2011-11-06
forum: Programming Talk
---

### Post by Jabrick on 2011-11-06
I am currently having troubles using private libraries/header files.
I'm using the stanford libraries for my school.
There is a .lib file that I placed in /usr/local/lib
And a few header filed I placed in /usr/local/include/cs106
and /usr/local/include/cs106/include

But whenever I compile with g++ -o test sample1.cpp
I get a error

sample1.cpp:13:20: fatal error: genlib.h: No such file or directory
compilation terminated.

Does that mean it can't find my header file?
How do I make it detect.
I've read about dynamic and static libraries, but this is a header file.
I know header called the library.

I've seen g++ using the wall argument, but thats to create a library I believe.

If someone could tell me how to make the g++ compiler auto-detect my headers and libraries that would be great.
Thanks

---

### Post by karlson on 2011-11-06
> **Jabrick said:**
> I am currently having troubles using private libraries/header files.
I'm using the stanford libraries for my school.
There is a .lib file that I placed in /usr/local/lib
And a few header filed I placed in /usr/local/include/cs106
and /usr/local/include/cs106/include

But whenever I compile with g++ -o test sample1.cpp
I get a error

sample1.cpp:13:20: fatal error: genlib.h: No such file or directory
compilation terminated.

Does that mean it can't find my header file?
How do I make it detect.
I've read about dynamic and static libraries, but this is a header file.
I know header called the library.

I've seen g++ using the wall argument, but thats to create a library I believe.

If someone could tell me how to make the g++ compiler auto-detect my headers and libraries that would be great.
Thanks

You should read about -I<dir> directive of GCC

---

### Post by Jabrick on 2011-11-07
> **karlson said:**
> You should read about -I<dir> directive of GCC

Ok I believe I got the header right I have done.
```

g++ -Wall -I /usr/local/include/cs106/ -o test sample1.cpp

```
And I get the message

/usr/lib/gcc/x86_64-unknown-linux-gnu/4.6.2/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
/tmp/ccTBqbpv.o: In function `Main()':
sample1.cpp:(.text+0x35): undefined reference to `GetLong()'
collect2: ld returned 1 exit status


Then I tried
```

g++ -Wall -I /usr/local/include/cs106/ -o test sample1.cpp /usr/local/lib/CS106CPPLib.lib -lm -lpthread

``` 
And get same error

Also tried
```

 g++ -Wall -I /usr/local/include/cs106/ -o test sample1.cpp -l /usr/local/lib/

```
And I get 
/usr/bin/ld: cannot find -l/usr/local/lib/
collect2: ld returned 1 exit status

I dont understand what I'm doing wrong. I have linked the header and libraries haven't I?

---

### Post by Liiiim on 2011-11-07
Mind posting your code?  It sounds like the first error is because you  named your main function Main, with a capital 'm'.  Remember C++ is case  sensitive and your main function must be called main, otherwise it  doesn't know where to start.

The second undefined reference is (I believe) because the linker can't  find your library.  Someone more experienced with gcc might tell you a  better way to do this, but I think you can specify your library you want  to bring in (CS106CPPLib.lib) with the '-l' switch, like this - 

```
g++ -Wall -I /usr/local/include/cs106 -lCSE106CPPLib.lib -o test sample.cpp
```

---

### Post by Jabrick on 2011-11-08
> **Liiiim said:**
> Mind posting your code?  It sounds like the first error is because you  named your main function Main, with a capital 'm'.  Remember C++ is case  sensitive and your main function must be called main, otherwise it  doesn't know where to start.

The second undefined reference is (I believe) because the linker can't  find your library.  Someone more experienced with gcc might tell you a  better way to do this, but I think you can specify your library you want  to bring in (CS106CPPLib.lib) with the '-l' switch, like this - 

```
g++ -Wall -I /usr/local/include/cs106 -lCSE106CPPLib.lib -o test sample.cpp
```

Ok so I used what you suggested 
And I get

/usr/bin/ld: cannot find -lCSE106CPPLib.lib                                                                       
collect2: ld returned 1 exit status   


So I tried both
```

export LD_LIBRARY_PATH=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib

```

And I'm still getting the same error.
This is the sample c++ I'm trying to compile
```

/*                                                                                                                                                                                                                                  
 * -----------------------------------------------------                                                                                                                                                                            
 * CS2S03/SE2S03, September 2011                                                                                                                                                                                                    
 * Assignment 1, Question 1                                                                                                                                                                                                         
 * File: PE0106.cpp                                                                                                                                                                                                                 
 * -----------------------------------------------------                                                                                                                                                                            
 * This program reads an integer and then displays the                                                                                                                                                                              
 * number that has the same digits in the reverse order.                                                                                                                                                                            
 * -----------------------------------------------------                                                                                                                                                                            
 */                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                    
#include "genlib.h"                                                                                                                                                                                                                 
#include "simpio.h"                                                                                                                                                                                                                 
#include <iostream>                                                                                                                                                                                                                 
                                                                                                                                                                                                                                    
/* Private function prototypes */                                                                                                                                                                                                   
                                                                                                                                                                                                                                    
long DigitReverse(long n);                                                                                                                                                                                                          
                                                                                                                                                                                                                                    
/* Main program */                                                                                                                                                                                                                  
                                                                                                                                                                                                                                    
int main() {                                                                                                                                                                                                                        
    long n;                                                                                                                                                                                                                         
                                                                                                                                                                                                                                    
    cout << "This program reverses the digits in an integer." << endl;                                                                                                                                                              
    while (true) {                                                                                                                                                                                                                  
        cout << "Enter a positive integer: ";                                                                                                                                                                                       
        n = GetLong();                                                                                                                                                                                                              
        if (n > 0) break;                                                                                                                                                                                                           
        cout << "Try again." << endl;                                                                                                                                                                                               
    }                                                                                                                                                                                                                               
    cout << "The reversed integer is: " << DigitReverse(n) << endl;                                                                                                                                                                 
                                                                                                                                                                                                                                    
    return 0;                                                                                                                                                                                                                       
}                                                                                                                                                                                                                                   
                                                                                                                                                                                                                                    
/*                                                                                                                                                                                                                                  
 * Function: DigitReverse                                                                                                                                                                                                           
 * Usage: rev = DigitReverse(n);                                                                                                                                                                                                    
 * -----------------------------------------------------                                                                                                                                                                            
 * This function returns the integer that has the same                                                                                                                                                                              
 * digits as n but in reverse order                                                                                                                                                                                                 
 */                                                                                                                                                                                                                                 
                                                                                                                                                                                                                                    
long DigitReverse(long n) {                                                                                                                                                                                                         
    long reverse = 0;                                                                                                                                                                                                               
                                                                                                                                                                                                                                    
    while (n > 0) {                                                                                                                                                                                                                 
        reverse = reverse * 10 + (n % 10);                                                                                                                                                                                          
        n = n / 10;                                                                                                                                                                                                                 
    }                                                                                                                                                                                                                               
                                                                                                                                                                                                                                    
    return reverse;                                                                                                                                                                                                                 
}                   

```

---

### Post by gardnan on 2011-11-08
I think that it may be because GCC automatically looks for a library whose name starts with "lib". I don't know how to override this functionality, so I would recommend renaming or copying the library to libCSE106CPPLib.a and then try relinking.
EDIT:
Reading some more GCC documentation has made it clear that it is the -l option specifically that adds the "lib" and ".a" to the file name, so instead, try just specifying the filename regularly.

---

### Post by Jabrick on 2011-11-08
I don't understand why I can't get this to work.
Could it be that the library file is not compatible for linux?
On my school website there are two options to download the stanford libraries. And they are considered "blank-projects".
There is a version for PC and a version for Mac.
But I would think its just how the "project" is formatted.
Since Mac cannot run visual studios express c++?
I just unzipped the files and moved the headers and the .lib file into my designated location.

Currently in my .bashrc I have
```

export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/usr/local/include/
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/lib/

```

And to compile I run what I think is very thorough.
```

g++ sample1.cpp -o test -I /usr/local/include/cs106/ -L /usr/local/lib/ -l CS106CPPLib

```
I renamed the library file to get rid of the .lib extension
(even though I dont think linux takes ext. into consideration)

And still get
```

/usr/bin/ld: cannot find -lCS106CPPLib
collect2: ld returned 1 exit status

```

And I would like to say thank you for the help!
I am greatful.

---

### Post by gardnan on 2011-11-08
The library you downloaded will probably not be compatible with Ubuntu, as you downloaded the Windows version. 

The library needs to be an ELF LSB in order to be used like normal. There may be some obscure GCC feature that allows you to use the code, so long as it does not depend on any Windows libraries. You may be able to get the Mac version to work though. Try downloading those libraries and running the file command on the actual libraries, they should either be ar archives or ELF LSB files if you want to be able to use them.

---

### Post by voidlogic on 2011-11-08
A couple of quick style notes in case you are interested (aka feel free to ignore me :)):

```
int main()
```

IMHO should be 
```

int main(int argc, char* argv[])
//or
int main(int argc, char** argv)
```

and I would recommend returning EXIT_SUCCESS as defined in stdlib.h rather than 0.

---

### Post by karlson on 2011-11-09
> **Liiiim said:**
> 
```
g++ -Wall -I /usr/local/include/cs106 -lCSE106CPPLib.lib -o test sample.cpp
```

That won't work.  Judging by the extension of the library it's a Windows MSVC++ lib.

---

### Post by Jabrick on 2011-11-14
I tried using the Mac version but it still didn't work.
The library was a .a file.
Which g++ looks for? But somehow I think its just not Linux compatible.
Sorry for such a late response and thank you for all the support.
By the way void logic I do appreciate when people take time to help me improve my knowledge.
Even though I didn't get it working I'm going to mark it as solved.
I learned alot thanks :)

---

