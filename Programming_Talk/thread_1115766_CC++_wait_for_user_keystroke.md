---
title: "C/C++ wait for user keystroke"
date: 2009-04-04
forum: Programming Talk
---

### Post by rba1988 on 2009-04-04
Hello.

I'm developing a C++ console application in Ubuntu 8.10 that runs a loop to display certain information. However, the only way to break away from the loop is to press ctrl+c. The program terminates entirely.

How would I implement the loop in such a way that if the user presses the key "q", the program will first display some statistical summary and then quit. Or if the user presses the key "p" the loop will break and the user prompts if they would want to continue. If so, the loop starts again.

Any ideas on how to do this under Ubuntu? Thanks in advance.

---

### Post by dwhitney67 on 2009-04-04
Is this a trick question?

Pretty much one of the first thing covered in any C or C++ book/tutorial is input/output from the terminal.  To collect input in C++, you would use std::cin.

```

char choice;

std::cout << "Enter a letter, 'p' or 'q': ";
std::cin  >> choice;
std::cin.ignore(100, '\n');

...

```

---

### Post by _Purple_ on 2009-04-04
In case of C, getchar() can be used.

---

### Post by rba1988 on 2009-04-04
> **dwhitney67 said:**
> Is this a trick question?

Pretty much one of the first thing covered in any C or C++ book/tutorial is input/output from the terminal.  To collect input in C++, you would use std::cin.

```

char choice;

std::cout << "Enter a letter, 'p' or 'q': ";
std::cin  >> choice;
std::cin.ignore(100, '\n');

...

```

yes but that would make the whole program stop right? If I put that code within the loop, it would wait until a user puts an input. I want it to wait for the user to hit "q" or "p" while the loop is still running. It has to display information in real time and can be stopped anytime during the process.

---

### Post by rba1988 on 2009-04-04
> **dwhitney67 said:**
> Is this a trick question?

Pretty much one of the first thing covered in any C or C++ book/tutorial is input/output from the terminal.  To collect input in C++, you would use std::cin.

```

char choice;

std::cout << "Enter a letter, 'p' or 'q': ";
std::cin  >> choice;
std::cin.ignore(100, '\n');

...

```

Maybe I should use an example to make my question clearer. When you run the command "top", it displays certain info of processes and changes over time. But when you hit "q", the application quits. I need to know how to code that so when you hit "q", it will show some information before exiting.

---

### Post by dwhitney67 on 2009-04-04
> **rba1988 said:**
> Maybe I should use an example to make my question clearer. When you run the command "top", it displays certain info of processes and changes over time. But when you hit "q", the application quits. I need to know how to code that so when you hit "q", it will show some information before exiting.

What you should have done in the OP is provide _ALL_ of your requirements.

Basically what you want is non-blocking I/O.  You should consider using ncurses for the application you describe.  You can print text anywhere on the terminal, and accept non-blocking input, just like the 'top' application.

---

### Post by slavik on 2009-04-04
you can also intercept ctrl+c. :) (look into signals)

---

### Post by Arndt on 2009-04-04
> **dwhitney67 said:**
> What you should have done in the OP is provide _ALL_ of your requirements.

Basically what you want is non-blocking I/O.  You should consider using ncurses for the application you describe.  You can print text anywhere on the terminal, and accept non-blocking input, just like the 'top' application.

Using separate threads comes to mind, too.

---

### Post by rba1988 on 2009-04-05
> **dwhitney67 said:**
> What you should have done in the OP is provide _ALL_ of your requirements.

Basically what you want is non-blocking I/O.  You should consider using ncurses for the application you describe.  You can print text anywhere on the terminal, and accept non-blocking input, just like the 'top' application.

Ok I will look into that. Thanks for your help.:D

---

### Post by rba1988 on 2009-04-05
> **Arndt said:**
> Using separate threads comes to mind, too.

Multithreading? Ok. I'll try to look into that too. Thanks.:D

---

