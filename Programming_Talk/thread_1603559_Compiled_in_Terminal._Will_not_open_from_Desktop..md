---
title: "Compiled in Terminal. Will not open from Desktop."
date: 2010-10-22
forum: Programming Talk
---

### Post by adam.bevelhymer on 2010-10-22
Hi,

I am a recent Ubuntu convert who is trying to get into a little programming in C++. I have successfully compiled and run a short program named "fibonacci.cpp" using g++ from the terminal.

g++ fibonacci.cpp -o fibonacci
./fibonacci

The program runs flawlessly from the terminal, but when I navigate to it from the desktop, I find the file, double-click it, and nothing happens. I have the box under Properties > Permissions > Allow Executing File checked. Is there some code I need to add at the beginning of my program to cause a Terminal window to open? Do I need to use an IDE to compile rather than the Terminal? I would really like it if I could simply click on the icon to make it run.

Here's a copy of my code:

#include <iostream>
using namespace std;

int main()
{
cout << "This program produces the Fibonacci series to a specified number of values.\n";

cout << "Specify number of values (must be > 2):";
unsigned int number;
cin >> number;

unsigned int value1=0;
unsigned int value2=1;
unsigned int value3;

cout << value1 << ", "<< value2;

for (int n=0; n<number-2; n++){
value3 = value1 + value2;
cout << ", " << value3;
value1 = value2;
value2 = value3;}	

cout << "\n";

return 0;
}

I will appreciate any help I get!!!

---

### Post by cgroza on 2010-10-22
Same here, if i create a launcher, indicate the path and select application in terminal it works, but not the real file.

---

### Post by Vox754 on 2010-10-22
> **adam.bevelhymer said:**
> Hi,
...
The program runs flawlessly from the terminal, but when I navigate to it from the desktop, I find the file, double-click it, and nothing happens. I have the box under Properties > Permissions > Allow Executing File checked. **Is there some code I need to add at the beginning of my program to cause a Terminal window to open?**...
What you want, that a terminal opens up, is not "standard" behavior, it is a misconception from working with Windows.

In Windows, when you have an executable, you can double-click it and magically a console will appear for you to view the output, even if the program is entirely console-based, and thus it only tells you that "the program has finished and the console will close".

The simple program you have developed is a terminal program, therefore, it will only work correctly if you run it from the terminal.

Think about it, most of the programs in "/bin" are command-line utilities. They have existed before graphical user interfaces or the mouse existed. Why would they magically appear a gnome-terminal when you run them? There is no association between double-clicking a mouse and magically opening a graphical console emulator on the screen.

Before regarding this system as primitive, try to understand this is the way Linux works. Programs are supposed to do one thing right. In this case, terminal programs need to be run from the terminal, they do not need to create a graphical terminal. There is a clear distinction between a terminal program and any possible graphical behavior. Windows, on the other hand, cannot exist without graphical interfaces. It's a different approach, a different philosophy if you will.

I can assure you most programmers in this forum, or advanced Linux users, keep several gnome-terminals and several tabs open to do stuff. That's the ideal way to program and test things, or just run things without the annoyance that is navigating through a file manager and clicking with the mouse.

Right now, forget about double-clicking, and just focus on learning programming, and getting comfortable with this new environment.

---

### Post by ssam on 2010-10-23
could create a .desktop file with 'Terminal=true'
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

something like
```

[Desktop Entry]
Version=1.0
Type=Application
Name=fibonacci
Comment=shows fibonacci numbers
Exec=/path/to/fibonacci
Terminal=true

```

then you can double click the desktop file.

---

### Post by dv3500ea on 2010-10-23
> **ssam said:**
> 
```

[Desktop Entry]
Version=1.0
Type=Application
Name=fibonacci
Comment=shows fibonacci numbers
Exec=/path/to/fibonacci
Terminal=true

```


You should change Exec to ```
/path/to/fibonacci && read
``` so that the terminal doesn't close once the program has finished so you have time to read the output. (You press enter to close it).

---

### Post by geirha on 2010-10-23
ssam's right, though with the default settings of gnome-terminal, the terminal will close after the program completes, so you'll probably only see the result for a split second. 

One way to work around that is to have the program wait for user input at the end of the program (e.g. add a *cin* at the end or something).

Another way is to change the settings of the terminal, to not immediately close it when the program completes.

@dv3500ea: That's shell code. The launcher doesn't run the command in a shell, so that'll fail.

---

### Post by ssam on 2010-10-23
would
```
Exec=bash -c "/path/to/fibonacci ; read"
```
work?

---

### Post by adam.bevelhymer on 2010-10-23
> **ssam said:**
> would
```
Exec=bash -c "/path/to/fibonacci ; read"
```
work?

That works perfectly, thank you!!! Thanks to everyone for the help. :)

---

