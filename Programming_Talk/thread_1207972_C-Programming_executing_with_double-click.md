---
title: "C-Programming executing with double-click"
date: 2009-07-08
forum: Programming Talk
---

### Post by MindSz on 2009-07-08
Hi,

I've been programming for a while and now I'm trying to get a program in C to be executed by double-clicking. The problem is that I need to pass a file-name as an argument.

So basically, I'm trying to find a way to double-click on a file and make it launch my program with its name as the argument. For example, if I double-click on picture.jpg it will launch my program as "imgProc picture.jpg"

Does anybody know how to achieve this?

The program works fine when I execute it from the command-line.

Thanks,
-S

---

### Post by JordyD on 2009-07-08
You could make it ask for a file when it runs if it doesn't receive command-line arguments.

```
printf("Which file do you want to perform this action on? ");
scanf("%s", filename);
```

---

### Post by dwhitney67 on 2009-07-08
> **MindSz said:**
> Hi,

I've been programming for a while and now I'm trying to get a program in C to be executed by double-clicking. The problem is that I need to pass a file-name as an argument.

So basically, I'm trying to find a way to double-click on a file and make it launch my program with its name as the argument. For example, if I double-click on picture.jpg it will launch my program as "imgProc picture.jpg"

Does anybody know how to achieve this?

The program works fine when I execute it from the command-line.

Thanks,
-S

If you are using the Gnome window manager, then right-click on your desktop and select "Create Launcher...".

You can specify the executable file that you need to run, and you can also specify an icon to use.

As for the type of launcher, you need to determine if it should run as a standalone application, or within a terminal.  The latter is often used when the application expects user input or will display information to the user.

---

### Post by JordyD on 2009-07-08
> **dwhitney67 said:**
> Gnome window manager
It's actually a desktop environment, Metacity is the default window manager.

---

### Post by MindSz on 2009-07-09
First of all thank you for all the replies.

I'm aware of the things you guys are talking about, but I'm trying to make this program work for people who have next-to-zero experience with computers, so I want them to just click on a picture and make this launch the program by itself; much like when you click on a text file and it opens the text editor.

Is this possible?

-S

---

### Post by dwhitney67 on 2009-07-09
> **MindSz said:**
> First of all thank you for all the replies.

I'm aware of the things you guys are talking about, but I'm trying to make this program work for people who have next-to-zero experience with computers, so I want them to just click on a picture and make this launch the program by itself; much like when you click on a text file and it opens the text editor.

Is this possible?

-S

YES.  Earlier I thought I provided the instructions on how (for you) to do this.

If you are looking for a more comprehensive guide on how to create an applet, then package it together with your app so that it can be installed by another user, then I suggest you refer to the Gnome documentation, or rephrase your requirements so that someone with this experience can help you.

If all you are looking to do is create an applet for yourself, then follow these basic instructions.

1.  Right-click on the desktop.
2.  Select "Create Launcher..."
3.  Change the Type to either "Application" or "Application in Terminal"
4.  Change the icon (optional)
5.  Enter the Name
6.  Browse until you find your executable application.
7.  Click on OK.


For step 3, if your application employs the use of terminal I/O, then you want to select "Application in Terminal".

---

### Post by MadCow108 on 2009-07-09
I think he wants to set his program as the default application for other files and not only open the application with a click on the application itself.

you can set that by rightclicking on a file of a certain type then there is usally a open with another program option
in there there is usally a checkbox to set the application to the default application.

what I don't know is how to set that when installing and how the programm trhen recieves the file (although it will probably be stdin)

---

### Post by JordyD on 2009-07-09
> **MadCow108 said:**
> I think he wants to set his program as the default application for other files and not only open the application with a click on the application itself.

you can set that by rightclicking on a file of a certain type then there is usally a open with another program option
in there there is usally a checkbox to set the application to the default application.

what I don't know is how to set that when installing and how the programm trhen recieves the file (although it will probably be stdin)
I always thought that it was just provided as an argument.

---

### Post by soltanis on 2009-07-09
I was under the impression you took the filename as the argument, then opened/read it yourself.

---

### Post by MadCow108 on 2009-07-09
yeah just tried it
the filename is of course passed as an argument :)
didn't think

---

### Post by nvteighen on 2009-07-10
What you'll need is to create an installer that is able to modify the **Nautilus** settings about MIME types so that it knows what to execute when you double-click something of some kind of type. I'm not sure how you do this, but it's surely possible, as many applications do this (emacs, e.g. makes itself default for some filetypes).

---

