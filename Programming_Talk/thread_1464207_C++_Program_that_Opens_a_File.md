---
title: "C++ Program that Opens a File"
date: 2010-04-27
forum: Programming Talk
---

### Post by hayden92 on 2010-04-27
Hey,

Sorry for the ambiguous title; I couldn't think of how to word this properly.

Basically, what I need is to be able to right-click on a file (in Nautilus) and select "Open With" and choose my program.

I know how to get a program to accept arguments from the command line (such as options and filenames), but I don't know how to get Nautilus to 'send' the name of the file that I opened, to my program (so that it can then work it's magic on the file).

Is there an env variable or something that is called "File-to-be-opened" which I can just pass over to my program?

Thanks in advance,
Hayden M

---

### Post by dwhitney67 on 2010-04-28
Your C++ program should be coded to accept command line args; in other words, the main() function should appear as something like:
```

int main(int argc, char** argv)
{
   ...
}

```
As far as dealing with Nautilus, all you must do is right-click on the file of interest, and indicate that you want to open it with your C++ executable.  (ie.  Open With -> Open with Other Application).

When Nautilus presents the list of applications, choose "Use a custom command", and then enter the (full) path to your C++ executable.

As far as having your app listed as one of the default "Open With" applications, I'm not sure how to do this.

---

