---
title: "Help with Emacs"
date: 2011-01-23
forum: Programming Talk
---

### Post by lekkin on 2011-01-23
So I'm a computer science major in college, but rather than being one of those people who knows everything about programming before coming, I am woefully ignorant.  My first two courses were simple though--we used easy IDEs to help teach us Java and C++ (Eclipse and Visual Studio respectively).  My professor this semester has said that Visual Studio is rather heavy and adds lots of things we don't need, so he wants us using a combination of Cygwin and Emacs to program in c++.  Having hardly used command-lines before and having gotten used to the over-helpfulness of Visual Studio, I'm finding the shift a bit difficult.  Even the most basic things seem impossible, although I finally did the basic hello world program.  

At the moment, here's my problem: we have a coding standard we're supposed to use, which includes tabs being 8 spaces long and lines being no longer than 80 characters.  I did a quick search to change the default size of a tab, and apparently the command is as follows:

(setq-default tab-width 4) 

However, I have no idea whatsoever where to enter this command.  The site I found says to put it in the .emacs file, but I have no idea where that is.  

Can someone try and help me?  And does anyone have advice for someone who is so new to all of this that might help me get better acquainted with everything?

---

### Post by wojox on 2011-01-23
It's a  hidden config file in your home folder. Ctrl+H should show them or ls -al in the terminal.

---

### Post by cyberslayer on 2011-01-23
Also, if you want to use 8 character wide tabs you don't have to change anything since its the default.  Keep in mind that emacs will use tab characters by default rather than spaces so if you want each tab to insert spaces you have to change that in your .emacs:

(setq-default indent-tabs-mode nil)

---

### Post by lekkin on 2011-01-23
Hmm, I still can't find it.  I should have clarified that I'm not actually using Ubuntu at the moment, I'm using Windows Vista...

---

### Post by wojox on 2011-01-23
> **lekkin said:**
> Hmm, I still can't find it.  I should have clarified that I'm not actually using Ubuntu at the moment, I'm using Windows Vista...

Google says 

```
C:\Users\lekkin\AppData\Roaming\
```

---

### Post by eeperson on 2011-01-24
On Windows, you can find it at:

C:\Users\<your username here> 

The file probably doesn't exist already so you will have to create it.  Beware that some Windows programs (such as Notepad) will complain about files that start with dots.  Because of this you can create it as either '.emacs' or '_emacs'.

---

