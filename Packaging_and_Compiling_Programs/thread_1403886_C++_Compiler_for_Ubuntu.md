---
title: "C++ Compiler for Ubuntu?"
date: 2010-02-10
forum: Packaging and Compiling Programs
---

### Post by Elaina on 2010-02-10
What compiler would you recommend? I'm learning how to program in C++ with a book, and it only mentions compilers such as Visual C++. I don't even know how the whole thing works, like if programs I write in C++ will only work on Windows or if they will work on Linux too. Clarification, please?

---

### Post by crlang13 on 2010-02-10
I've used codeblocks.  You can just get it through the Ubuntu software center or package manager.  I've been happy with it.

---

### Post by Elaina on 2010-02-10
Thank you, I have it now and it seems all right.

---

### Post by x33a on 2010-02-10
try
```
sudo apt-get install build-essential
```

this will install g++. you can use it at the commandline to compile programs.
e.g.
```
g++ -o file file.cpp
```

Some other good IDEs are eclipse, anjuta, geany etc.

---

### Post by Kenny_Strawn on 2010-02-11
Definitely GCC/G++. It is in fact the most widely used compiler by IDEs.

---

### Post by stumbleUpon on 2010-02-11
+1 for GCC/G++

You can also look at the noncommercial intel compilers
[http://software.intel.com/en-us/articles/non-commercial-software-download/](http://software.intel.com/en-us/articles/non-commercial-software-download/)

---

### Post by jmp971 on 2010-02-11
+1 for GCC/G++ and Code::Blocks

---

### Post by Elaina on 2010-02-11
What about Netbeans?

---

### Post by x33a on 2010-02-11
Netbeans is also good. In the end you have to try different things and decide which one suits your needs. Some are more heavy than others, some carry features which may not be useful for you.

In my opinion, if you want a lightweight solution go for (g++, your favourite text editor) or geany, which is also quite lightweight.

---

### Post by l0xin on 2010-02-12
> **Elaina said:**
> I don't even know how the whole thing works, like if programs I write in C++ will only work on Windows or if they will work on Linux too. Clarification, please?

Simple console applications will work on both. If you take a piece of code like :

```

#include <iostream>

using namespace std;

int main()
{
    int password = 123;
    int passwordInput;

    do
    {
        cout << "Enter password : ";
        cin >> passwordInput;
        cin.ignore();
        if(passwordInput == password)
        {
            cout << "Correct" << endl;
        }
        else
        {
            cout << "Wrong password" << endl;
        }
    }
    while (passwordInput != password);

    cout << "PRESS ENTER TO EXIT" << endl;
    cin.get();
    return 0;
}

```That will compile and run on both Windows and Linux (or *any* platform with a C++ compiler), because it only uses functions from the C++ Standard library.

---

### Post by eklavya_18 on 2010-02-15
gcc/g++. You know real programmers avoid IDEs. Best is to start on vim editor.

---

### Post by danovotny on 2010-02-15
Not to officially hijack the threat, but...

I recently started learning C++, and I have been using Geany, with g++ as the compiler backed. The problem I have been continually running in to is having to link libraries in the compiler arguments. The list is currently "-lSDL -lGL -lGLU -lcryptopp" and seems to grow every time I pick up something new on a tutorial. So my two questions are:

1. Is there any other way to link libraries other can in the compiler arguments one at a time?

2. If the compiled executable was deployed to a different machine, would that machine have to have all of those libraries installed as well?

---

### Post by loyo on 2010-02-16
if you want to link the lib libthread,you should type -lthread ,it just refer to libthread.so or static lib

---

### Post by l0xin on 2010-02-16
> **danovotny said:**
> 2. If the compiled executable was deployed to a different machine, would that machine have to have all of those libraries installed as well?

I may be wrong here, but I believe it depends on whether the libraries being linked against are static or shared. A static library becomes part of the executable, meaning there is no external dependency. A shared library however stays separate to the executable and is referenced when it runs, therefore making it a prerequisite.

---

### Post by Elaina on 2010-02-16
Okay, I used emacs and it worked pretty well. 

vi is a demon in text editor form, but I'm getting used to it now that I found a pretty good guide. 

Overall, you guys had really good suggestions, thanks for all the input. I think I'm going to just avoid IDEs and take the straight and narrow.

---

### Post by bilalakhtar on 2010-02-17
+1 for GCC and G++
Looks like you are new to Ubuntu and Linux. I would prefer you to use Anjuta as a frontend for G++. To install Anjuta IDE, use Ubuntu Software center.:popcorn:

---

### Post by x33a on 2010-02-17
> **Elaina said:**
> Okay, I used emacs and it worked pretty well. 

vi is a demon in text editor form, but I'm getting used to it now that I found a pretty good guide. 

Overall, you guys had really good suggestions, thanks for all the input. I think I'm going to just avoid IDEs and take the straight and narrow.

Better mark this thread solved if your query has been satisfied.

---

### Post by Elaina on 2010-02-17
> **bilalakhtar said:**
> +1 for GCC and G++
Looks like you are new to Ubuntu and Linux. I would prefer you to use Anjuta as a frontend for G++. To install Anjuta IDE, use Ubuntu Software center.:popcorn:
Eh, I've got it figured out, and I'm getting used to vi now, so we're all good.
----
x33a, thanks for the reminder to mark as solved, it's done!

---

