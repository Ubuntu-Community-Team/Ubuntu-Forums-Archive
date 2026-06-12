---
title: "please help - error when updating, E: dpkg was interrupted"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by rougittie on 2012-09-19
hey wheni go to do updates i am getting E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone help me i am new to this computer linux and am not realgood with computers in the first place i need to no what to do to fix this prob please thank u i have linux 11

---

### Post by ericsonlouis on 2012-09-19
When i update i simply open my update manager and if i have updates i click install 

try that

---

### Post by grahammechanical on 2012-09-19
Ubuntu keeps a list of the software packages on your machine. When we run Updates the operating system first of all compares the list of packages on the machine with the list on the servers (repositories) and it identifies the packages that can be updated because they have been modified.

In your case that package list is broken because the process of comparing package lists was interrupted.

You now need to open a terminal and run the command. You will be asked to put in your password. As you type you will not see the password being printed out on the screen. This is for security reasons. After typing in your password just press enter and see what happens.

If all goes well you can then run Update Manager or whatever it is called in Ubuntu 11.04 or 11.10.


Regards.

---

### Post by cortman on 2012-09-19
> **rougittie said:**
> hey wheni go to do updates i am getting E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can someone help me i am new to this computer linux and am not realgood with computers in the first place i need to no what to do to fix this prob please thank u i have linux 11

You obviously didn't pay attention to the error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Run

```
sudo dpkg --configure -a
```

---

### Post by Bucky Ball on 2012-09-19
Welcome.

Open a terminal (Applications>Accessories>Terminal) and paste this in, as the error tells you to do:

```
sudo dpkg --configure -a
```For future reference, please use descriptive thread titles to help us help you. Titles like 'help' generally get overlooked. ;)

* Update: Cortman beat me to it. +1, yea, like Cman says ...

---

### Post by kimberlite on 2012-09-19
Open terminal. Than type:

```
sudo dpkg --configure -a
```

It will ask for your password.

---

### Post by audiomick on 2012-09-19
> **Bucky Ball said:**
> 
Open a terminal (Applications>Accessories>Terminal) and paste this in,

Hi, the last three poster have given you the right advice, so I wont do that again.

Do you know how to open a terminal?

When you have a terminal open, it is a good idea to copy the commands people suggest here and paste them in to avoid making typing errors. The trick to that is that you need to do ctrl+shift+v to paste into the terminal, not just ctrl+v like in most programs. Same for copying: you need ctrl+shift+c to copy highlighted text out of the terminal to, for instance, paste it here to show what error messages you are getting.

---

### Post by philinux on 2012-09-19
> **audiomick said:**
> 

When you have a terminal open, it is a good idea to copy the commands people suggest here and paste them in to avoid making typing errors. The trick to that is that you need to do ctrl+shift+v to paste into the terminal, not just ctrl+v like in most programs. Same for copying: you need ctrl+shift+c to copy highlighted text out of the terminal to, for instance, paste it here to show what error messages you are getting.

Or just use the mouse to highlight text and right click copy and paste as normal.

---

### Post by audiomick on 2012-09-19
> **philinux said:**
> Or just use the mouse to highlight text and right click copy and paste as normal.

Ah, didn't know that. Thanks Phil.

---

### Post by oldos2er on 2012-09-19
> **philinux said:**
> Or just use the mouse to highlight text and right click copy and paste as normal.

Or just swipe the text to be copied, then paste into a terminal by hitting the middle mouse button once.

---

