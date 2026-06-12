---
title: "Help installing Wine"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by offgridguy on 2012-07-15
I am trying to download and install Wine, everything is okay until i get to the software
center prompt where it asks for the complete line of the repository for this file.
I am not sure what to put here, technically I don't know what a repository is.
Any help is appreciated.:confused:

---

### Post by z3nhakr on 2012-07-15
a repository is basically just a server that stores the files.

try installing wine through the command line:
ctrl+alt+t (brings up terminal window)
type "sudo apt-get install wine"

if you get an error copy/paste it to a post

---

### Post by offgridguy on 2012-07-15
I tried this, and get the message, command not found.   How do I rectify this?
I appreciate the help, thank you.

---

### Post by d4m1r on 2012-07-15
> **offgridguy said:**
> I tried this, and get the message, command not found.   How do I rectify this?
I appreciate the help, thank you.

What version of Ubuntu are you running? Are you connected to the internet when you run it?

It must be very old if it says command not found to apt-get....

---

### Post by offgridguy on 2012-07-15
I am running ubuntu 12.04,  no it is not old only recently purchased and installed.
Yes I am connected to the internet when I run it.

---

### Post by ub07 on 2012-07-15
Which command is failing? sudo or apt-get? Remember these commands must be all lowercase.

---

### Post by offgridguy on 2012-07-15
I'm thinking the problem here is this has to run from an account with administrator privileges , but
there is no prompt for a password in the terminal.

---

### Post by ub07 on 2012-07-15
If you are running from the account that you initially set up when you installed Linux, it should already be an administrator account. But yeah, in order to install software you really have to be an administrator.

---

### Post by offgridguy on 2012-07-15
Any time i have downloaded software before using the command line, I have been prompted for a
password, but it doesn't appear to want to do that now. Thanks for the input anyway.

---

### Post by llamabr on 2012-07-15
What a strange conversation.  Open a terminal, type:

```
sudo apt-get install wine
```

and then type your passwd

If you get an error message, copy/paste the output.

Additionally, whatever you're trying to do, you can probably find a native linux application which does it better.  What are you trying to run?  Wine is rarely the correct solution.

---

### Post by offgridguy on 2012-07-15
Seem to have it this time. Now to find it.

---

### Post by llamabr on 2012-07-15
> **offgridguy said:**
> Seem to have it this time. Now to find it.

I don't quite know what that means, but if it's working now, be sure to mark the thread solved.

---

### Post by offgridguy on 2012-07-15
wine downloaded, would not configure or install.  I agree with you, wine is probably not the right solution. A huge waste of time is all. Thank you for your insight.  Thread is marked solved only
because I've given up on it.

---

