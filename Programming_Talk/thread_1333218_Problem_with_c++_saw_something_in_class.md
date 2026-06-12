---
title: "Problem with c++ saw something in class"
date: 2009-11-21
forum: Programming Talk
---

### Post by ThaDoctor99 on 2009-11-21
Okay what I saw in class was this teacher, showing us some code which generated a background of whatever color or sign (special signs) by a simple 2 cifre Hex code.
It was in an area of 20,40 pixels or something.
Now my problem is two things or steps.
First this was on a win platform, and then I do not remember any of the code (well except for the for loops generating the area.)
Well any help is appreciated.
Thanks in advance.

PS.
Thought that was kind of cool code so would like to able to it.

---

### Post by Tony Flury on 2009-11-21
There is nothing in c++ itself to do with graphics/drawing windows etc. 

What you will need is a graphics library, and a window manager libraries of some form. On Linux there are plenty of Window managers - GTK, KDE, QT etc. There are also lots of graphic type librarys that work wth the Window manager to allow you to draw shapes and colours into the windows - examples of these are Cairo, OpenGL etc.

My guess is what you saw was windows specific code (using Windows own Window Manager and graphics library), and therefore the code would be tough to port - not impossible though. If you could describe more clearly what it did, then I am sure it would be possible for someone to recreate it using one (or more) of the Linux window Managers and Graphics libraries.

---

### Post by era86 on 2009-11-21
Was this done in Visual Studio?  And if so, was your teacher using Forms?  If he/she was using the Form tools, they probably are accessing the objects on the form using the -> operator.  Then again, I could be wrong?

---

### Post by ThaDoctor99 on 2009-11-23
Nono pure dos app no graphic (that was the cool part.)
It was all just part of the systems internal signs reprensentated by a hex code....

If there were any of the "uncool" graphics I would probably have paid a bit more attention anyway

Anyway thanks for the help so far...

---

### Post by Zugzwang on 2009-11-23
> **ThaDoctor99 said:**
> Nono pure dos app no graphic (that was the cool part.)
It was all just part of the systems internal signs reprensentated by a hex code....


Perhaps something like this?: [http://en.wikipedia.org/wiki/ANSI_escape_sequence](http://en.wikipedia.org/wiki/ANSI_escape_sequence)

---

### Post by ThaDoctor99 on 2009-11-23
it doesn't seem immediately the same, but I will investigate.

However now I found another problem, I seem to have lost all my kernels headers, that is the .h files needed to be in my system for compiling programs... Really strange how can this be fixed, however this is some strange output

```

tbear@tbear-datastation ~/Programming/cpp $ g++ char.C 
char.C: In function ‘int main()’:
char.C:5: error: ‘cin’ was not declared in this scope
char.C:6: error: ‘cout’ was not declared in this scope
char.C:6: error: ‘endl’ was not declared in this scope
tbear@tbear-datastation ~/Programming/cpp $ 

```

---

### Post by ThaDoctor99 on 2009-11-23
#include <iostream>
main()
{
char a;
cin.get >> a;
cout << (int)a << endl;
return 0;
}
is the refering source code...

---

### Post by Zugzwang on 2009-11-23
> **ThaDoctor99 said:**
> #include <iostream>
main()
{
char a;
cin.get >> a;
cout << (int)a << endl;
return 0;
}
is the refering source code...

In the modern C++ dialects, you need to add "using namespace std;" as second line in your code in order to get in working. Also, the "cin.get" line doesn't look correct to me. Finally, you need to give "main" a return type, for example by changing the line to "int main() {".

And for the "kernel headers" you mention: Look at the stickies of this forum on how to install them (note that they aren't actually called "kernel headers").

---

### Post by ThaDoctor99 on 2009-11-23
wait I am thinking in c here.... Sorry....

---

### Post by ThaDoctor99 on 2009-11-23
I realized that... Think I got them. cin.get is correct in windows programming (which we are tought at school) however now I adjust it....

---

### Post by gmjs on 2009-11-23
Zugzwang is spot on.  You need to specify the namespace for C++ (std in this case).

You don't need the '.get'.

```
cin >> input
``` is the syntax.

You can use cin.get to read a certain number of characters if you want to:

```
cin.get(string, char_num).get();
``` is the syntax.

Hope that helps.

Graham

---

### Post by ThaDoctor99 on 2009-11-23
well, just realizing that my teacher teach bad code karma.
What we learned in what little programming we have had is that "main" can be defined without return as it defines to void (this seems rather wrong with gcc) which anyway will give some maintainers a headache or himself later, well anyway I was quite happy with my result, until I found that it do not show what the ascii for Ctrl and Alt are.
So how do I find those.

And after that how do I apply that in my program such that.

When user hit Alt+s or something it prompt the user with something ?

---

### Post by ThaDoctor99 on 2009-11-23
#include<iostream>
using namespace std;
int main()
{
int b, h;
while(b<100)
{
while(h<100)
{
cout << "\xFF" << endl;
h++;
}
b++;
}
return 0;
}

that was the code I saw in class but it worked on Microsoft windows, why not in Linux I do not understand...

---

### Post by meson2439 on 2009-11-23
you are using the wrong extension for your c++ codes. change it to **char.cpp** instead. Using void for main function is okay. you only need remember that in linux, you can write function like this 

```

int main(int argc, char *argv[], char *env[])

```

The above code will allow your code to take arguments as well.

---

### Post by Zugzwang on 2009-11-24
> **ThaDoctor99 said:**
> 
that was the code I saw in class but it worked on Microsoft windows, why not in Linux I do not understand...

Are you sure? The behaviour of that code is actually undefined. This applies to both Windows and Linux. Reason: The variables are never initialized with a value. Furthermore, after the inner loop was left for the first time, it is likely to never be run again as the value of "h" is never reset.

---

### Post by lisati on 2009-11-24
> **ThaDoctor99 said:**
> #include<iostream>
using namespace std;
int main()
{
int b, h;
while(b<100)
{
while(h<100)
{
cout << "\xFF" << endl;
h++;
}
b++;
}
return 0;
}

that was the code I saw in class but it worked on Microsoft windows, why not in Linux I do not understand...
1.Ouch! Because b & h aren't given an initial value, they could end up holding any old rubbish. Bad for your loop!
2.If the intent was to draw a square, you might want to alter the location of the emission of the endl

---

### Post by ThaDoctor99 on 2009-11-24
Okay I did not remember the code entirely, I will try to fix this when I get home...

---

