---
title: "Command line classes?"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by mattkodion on 2012-04-13
Hi All,  Just wondering if there are any occasional cmd line classes taught
in the area?  San Francisco city.  Trying to learn how to install backtrac and
vmware with Ubuntu.  Thanks matt

---

### Post by cariboo on 2012-04-13
Moved to a thread of it's own, as it had nothing to do wit where it was.

I'd suggest you contact the [San Francisco Linux Users Group]("http://www.sf-lug.com/"), as they can probably point you in the right direction.

---

### Post by MG&amp;TL on 2012-04-13
There's a good sticky at the top of ABT to get you started in the meantime-"Linux command line learning resources".

---

### Post by souravc83 on 2012-04-13
One good way to learn is by practice.
Use the command line as much as you can. Stop using the mouse unless you really need it.
When you get stuck with doing something on the command line, like opening some program, or renaming some file, google is there to help you know the right command.

It would have been great if we could start in a CL only environment and get the Window running only for programs. That would be an ideal learning environment. But I don't know how to achieve it.

Maybe somebody here can point to a solution.

---

### Post by MG&amp;TL on 2012-04-13
> **souravc83 said:**
> 

Maybe somebody here can point to a solution.

Press Ctrl-Alt-F1 to go to a login prompt. Press Ctrl-Alt-F7 to go back to graphical desktop. If the temptation is too much, enter:

```
sudo service lightdm stop
```which stops the graphical desktop entirely. :)

---

### Post by haqking on 2012-04-13
> **mattkodion said:**
> Hi All,  Just wondering if there are any occasional cmd line classes taught
in the area?  San Francisco city.  Trying to learn how to install backtrac and
vmware with Ubuntu.  Thanks matt

[http://www.backtrack-linux.org/tutorials/](http://www.backtrack-linux.org/tutorials/)

---

### Post by souravc83 on 2012-04-13
Yes, I have tried working on Ctrl+Alt+F1 command line sometimes, but it is a pain to switch between this and that everytime.
Like,lets say, I am writing a Latex doc. I go to Vim and write in the 1st terminal, and then each time I compile it, I need to come back to F7 to see the pdf. Thats not so convenient.

I was looking for a way where I can work command line only, but I when I execute acroread or matlab, the window pops up.

Never tried stopping lightgdm. Will try that.

---

### Post by MG&amp;TL on 2012-04-14
> **souravc83 said:**
> Yes, I have tried working on Ctrl+Alt+F1 command line sometimes, but it is a pain to switch between this and that everytime.
Like,lets say, I am writing a Latex doc. I go to Vim and write in the 1st terminal, and then each time I compile it, I need to come back to F7 to see the pdf. Thats not so convenient.

I was looking for a way where I can work command line only, but I when I execute acroread or matlab, the window pops up.

Never tried stopping lightgdm. Will try that.

Obviously you can't use graphical apps on a command-line. Look for CLI PDF viewers-I'm not sure if matlab comes with a curses interface or anything like that.

---

### Post by josephmills on 2012-04-14
> **mattkodion said:**
> .  Trying to learn how to install backtrac and
vmware with Ubuntu.  


Dont drive fast cars when you do not know how to drive. 

my fav bash tutorial

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

