---
title: "[C++] Compiling multiple files?"
date: 2010-06-14
forum: Programming Talk
---

### Post by MtnDew on 2010-06-14
Hello Ubuntu Forums,

I am trying to compile six CPP files. I am making a calculator that relies on multiple files. Please don't advice that I could do this in one file, I know. I apologize there is a lot of content here. I don't normally ask for help, but this one has me quite stumped. I usually work out of only one file, defining all the functions inside of that file. I have been trying to get this to compile for quite some time, without luck. 

This is my code. I am using QT IDE. I compile using G++ on CLI. 
[IMG]http://i269.photobucket.com/albums/jj79/swordsmen666/code.png[/IMG]

When I go to G++ CLI to compile this is what I type: 
> g++ home.cpp -o calculatorI do home.cpp because this is my main file, similar to main.cpp but I have to have that for some reason, it doesn't matter. When I do that, I recieve these errors:
> 
jeff@jeff-desktop:~$ g++ home.cpp -o calculator
/tmp/ccejItxZ.o: In function `main':
home.cpp:(.text+0x158): undefined reference to `addition()'
home.cpp:(.text+0x1a2): undefined reference to `subtraction()'
home.cpp:(.text+0x1ec): undefined reference to `multip()'
home.cpp:(.text+0x236): undefined reference to `division()'
home.cpp:(.text+0x280): undefined reference to `modulo()'
collect2: ld returned 1 exit status

Here is a sample screenshot of what I recieve when I compile: 

[IMG]http://i269.photobucket.com/albums/jj79/swordsmen666/ide.png[/IMG]

I have clearly declared these functions in "modules.h". Main is defined in home.cpp, which I have attached to this post. This is the code to modules.h, please exuse my notes.

_**modules.h**_
```

// modules.h (included in every CPP file as:
// #include "modules.h"

#include <iostream>
#include <string>
// Do not use "using namespace std" in header files!

#ifndef MODULES_H
#define MODULES_H

// In order. Addition, subtraction, multiplication, division, modulous(remainder).
// I'm using blank arguements because I will ask the user to input the paramaters inside the function.
void addition ();
void subtraction ();
void multip ();
void division();
void modulo ();

// Error handling
void error_home_33(); // Used if the user entered an invalid choice

#endif // MODULES_H

```I have included modules.h in every CPP file I use. I have clearly defined each function within the corresponding file (defined addition in addition.cpp, subtraction in subtraction.cpp, etc). The main() function is defined in home.cpp
That is why I thought/think that i should be compiling home.cpp

_**home.cpp**_
```

#include <iostream>
#include <string>
#include "modules.h"
using namespace std;
void addition ();
void subtraction ();
void multip ();
void division();
void modulo ();

int main(){
    top: // Label for error handling
    cout << "Please choose an opperation from the list below.";
    cout << endl << endl;
    cout << "Addition - Type \"addition\" to perform an addition equation." << endl;
    cout << "Subtraction - Type \"subtraction\" to perform a subtraction equation." << endl;
    cout << "Multiplication - Type \"multiplication\" to perform a multiplication equation." << endl;
    cout << "Division - Type \"division\" to perform a division equation." << endl;
    cout << "Remainder- Type \"remainder\" to perform a modulus opperation." << endl;
    string choice;
    cin >> choice;
    if(choice == "Addition" || choice == "addition") {
        addition();
    }
    else if(choice == "Subtraction" || choice == "subtraction") {
        subtraction();
    }
    else if(choice == "Multiplication" || choice == "multiplication") {
        multip();
    }
    else if(choice == "Division" || choice == "division") {
        division();
    }
    else if(choice == "Remainder" || choice == "remainder") {
        modulo();
    }
    else {
        cout << "You said: \"" << choice << ". That is not an available option!" << endl;
        cout << "Did you spell it right? Are you using correct capitalization?" << endl;
        cout << "Try again." << endl << endl;
        goto top;
    }
}

```Please help! The source code to the dependent files is in the attachment(s) below, along with addition.txt (addition.cpp). Addition.txt is an example of how I structure my functions, the rest are structured the same as well (division.cpp, modulo.cpp,etc)

-Jeff

---

### Post by Tony Flury on 2010-06-14
> 
I am trying to compile six CPP files. I am making a calculator that relies on multiple files. Please don't advice that I could do this in one file, I know. I apologize there is a lot of content here. I don't normally ask for help, but this one has me quite stumped. I usually work out of only one file, defining all the functions inside of that file. I have been trying to get this to compile for quite some time, without luck. 

if you notice - the error you get is from ld (i.e. the linker) and not the compiler.

What this tells you is that there is nothing wrong with your source code, but when the Linker tries to convert the object file into an executable it has no idea where the definition of your addition, subtraction functions are.

The correct way to solve this is to use a make file so that if you change your home.cpp you don't need to recompile everything.

Make files can be a tad tricky though - so you should be able to do something like this : 

```

g++ home.cpp addition.cpp subtraction.cpp multip.cpp division.cpp modulo.cpp -o calculator

```
This makes sure that each cpp file is compiled into a object file (.o) and also then passes all the object files (.o) file to the linker so that it can stitch everything together into a single executable.

---

### Post by MtnDew on 2010-06-14
> **Tony Flury said:**
> if you notice - the error you get is from ld (i.e. the linker) and not the compiler.

What this tells you is that there is nothing wrong with your source code, but when the Linker tries to convert the object file into an executable it has no idea where the definition of your addition, subtraction functions are.

The correct way to solve this is to use a make file so that if you change your home.cpp you don't need to recompile everything.

Make files can be a tad tricky though - so you should be able to do something like this : 

```

g++ home.cpp addition.cpp subtraction.cpp multip.cpp division.cpp modulo.cpp -o calculator

```This makes sure that each cpp file is compiled into a object file (.o) and also then passes all the object files (.o) file to the linker so that it can stitch everything together into a single executable.

Thank you so much! I over analyzed my code. 

Thank you again,

-Jeff

---

