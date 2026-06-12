---
title: "Netbeans will not load"
date: 2010-09-23
forum: Programming Talk
---

### Post by k7faq on 2010-09-23
Running Ubuntu 10.04.1 had installed NetBeans 6.9. 

The program was running the first day I installed it. Used it to edit some code and the next day and since the program will not load. No error messages, nothing. Not even the splash screen.

Honestly, I have no clue where to start. Anyone with some ideas?

Thank you!
Steven

---

### Post by lykeion on 2010-09-24
It makes you wonder what kind of evil code you wrote that broke Netbeans.

Joking aside, you should try running Netbeans from a terminal window. That way you can figure out what is wrong.
Applications > Accessories > Terminal > enter "netbeans" (without quotes)

Also check this thread:
[http://ubuntuforums.org/showthread.php?t=1371837](http://ubuntuforums.org/showthread.php?t=1371837)

---

### Post by k7faq on 2010-09-24
Hi, Thanks for the response. It seems Ubuntu has forgotten about my having installed Netbeans 6.9.1 by downloading .deb file from Sun's website... here is the response:

steven@snoopy:~$ netbeans
The program 'netbeans' is currently not installed.  You can install it by typing:
sudo apt-get install netbeans

I looked at the other post.
They talk about references to java not being defined. Unfortunately I am not to that point yet.

Thank you for your help.

---

### Post by lykeion on 2010-09-25
Windows users are used to install programs by manually downloading installers and run them, 
but the preferred way to install a program in Ubuntu is using a package manager.
That way you'll make sure you'll get a tested and maintained version of the program you are installing, plus that updates will be installed automatically.
So I'd recommend that you install Netbeans like this:
Applications > Ubuntu Software Center > Enter netbeans in search field > Install NetBeans IDE 6.8

---

