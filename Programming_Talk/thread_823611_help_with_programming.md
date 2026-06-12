---
title: "help with programming"
date: 2008-06-09
forum: Programming Talk
---

### Post by mychem54321 on 2008-06-09
I am really new to ubuntu.I used to have windows and i programmed easily, but i formatted everything on my laptop and installed ubuntu 7.10 Gutsy and i've been trying to write simple programs on it but it doesn't work. I tried saving it as a ".c" file, ".cpp", and a ".exe" file and when i click on the icon of the program, it just shows the writing of the program. not the program it created. I installed the "build-essential" thing also. I'm using C++ language. should i use a different language??

---

### Post by kellemes on 2008-06-09
Couple of helpful links..
[http://ubuntuforums.org/showthread.php?t=796494]("http://ubuntuforums.org/showthread.php?t=796494")
[http://ubuntuforums.org/showthread.php?t=796493]("http://ubuntuforums.org/showthread.php?t=796493")

---

### Post by KingTermite on 2008-06-09
The articles in those posts I'm sure are well worth reading, however, a quick answer is that it sounds like you aren't compiling it.

If you have a source file (.c or .cpp) file, you need to compile it with the  gnu c compiler (installed from the "build-essential"). It will create a file called "a.out" which is your executable.

example:
"gcc myfile.cpp" and it will report errors from compile or create "a.out" in same directory.

---

### Post by Sef on 2008-06-09
Moved to Programing Talk.

---

### Post by Kadrus on 2008-06-09
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```
c++:
```
#include<iostream>
using namespace std;
int main()
{
cout<<"Test"<<endl;
return 0;
}
```
save it:ex.cpp
open terminal and type:
```
g++ ex.cpp
```
then```
./a.out
```

---

### Post by doorman on 2008-06-09
You have to compile the program you wrote.

1. Open up a terminal 
```
Applications - Accessories - Terminal
```
or press Alt+F2 and type in ```
gnome-terminal
```
2. Now position yourself to the directory the source is in ( probably /home/your_user_name or /home/your_user_name/Projects ), so type in the terminal
```
cd /path/to/cpp/file
```
3. compile the code:
```
gcc file.cpp
```
if there were no errors, a file called file.out is created. If there were some errors or warnings, edit the code and correct them
4. run the program by typing in the terminal
```
./file.out
```

And that's all folks :)

---

### Post by Kadrus on 2008-06-09
g++ is the c++ compiler..gcc is the c compiler..althought the compilation will work..using g++ is more recommended..

---

### Post by LaRoza on 2008-06-09
> **Kadrus said:**
> g++ is the c++ compiler..gcc is the c compiler..althought the compilation will work..using g++ is more recommended..

Not exactly, you can compile any supported language with gcc (GNU Compiler Collection)

[http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

---

### Post by KingTermite on 2008-06-09
> **LaRoza said:**
> Not exactly, you can compile any supported language with gcc (GNU Compiler Collection)

[http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

Not exactly.

GCC = Gnu Compiler Collection
gcc = Gnu C Compiler (the actual program)

---

### Post by JupiterV2 on 2008-06-09
If you don't like a.out for a program name, which I personally can't stand, use the -o flag (output name) to GCC to 'name' your compiled program.

g++ -o myprogram mysource.cpp

---

### Post by pmasiar on 2008-06-09
> **mychem54321 said:**
> I'm using C++ language. should i use a different language??

Possibly. See sticky FAQ with poll. Most people recommend starting with Python. You can always learn C++ or C later, when you need the CPU speed - or not, because most likely Python will be fast enough :-)

---

### Post by rye_ on 2008-06-09
> **pmasiar said:**
> Possibly. See sticky FAQ with poll. Most people recommend starting with Python. You can always learn C++ or C later, when you need the CPU speed - or not, because most likely Python will be fast enough :-)

yeah...... but then you'd have to adhere to a whitespace sensitive (the programming antichrist) language not as concise/ clever as the infinitely well designed ruby.  I am moderately biased though.......

---

### Post by pmasiar on 2008-06-09
> **rye_ said:**
> yeah...... but then you'd have to adhere to a whitespace sensitive (the programming antichrist) language not as concise/ clever as the infinitely well designed ruby.  I am moderately biased though.......

I am also biased .... :-)

If i encounter code with wrong indentation, I'll reformat it first :-) and i prefer readable non-clever languages, being hurt by Perl.

---

### Post by lisati on 2008-06-09
I haven't used a truly "whitespace sensitive" language for a few years now - aren't they a trifle old-fashioned?

---

### Post by pmasiar on 2008-06-10
> **lisati said:**
> I haven't used a truly "whitespace sensitive" language for a few years now - aren't they a trifle old-fashioned?

What is oldfashioned in having good indent structure, good code outline? In Python, syntax structure (functions, if and loop blocks) are expressed by indent, as any "best practices" rules in any language do. I am completely lost why this irritates so many noobs. If you use any language in any big project with coding standards, you have to maintain code structure, exactly as you will in Python. So what is the problem? Maybe the problem is that you never coded in a big project with coding standards?

---

### Post by LaRoza on 2008-06-10
> **lisati said:**
> I haven't used a truly "whitespace sensitive" language for a few years now - aren't they a trifle old-fashioned?

Haskell is modern and whitespace sensitive. 

Python code will be coded exactly the same way as other C style languages without the extra characters.

---

### Post by nvteighen on 2008-06-10
> **lisati said:**
> I haven't used a truly "whitespace sensitive" language for a few years now - aren't they a trifle old-fashioned?

And Makefiles? :p

---

