---
title: "Accessing Terminal via C+ program"
date: 2010-04-21
forum: Programming Talk
---

### Post by UbuKunubi on 2010-04-21
Hello,

I have a growing number of people who ask me to set up Ubuntu to connect to the internet via their mobile phones and bluetooth.

This is now an established routine for many people after setup:
sudo -i[enter]
type password[enter]
rfcomm bind 0 xx : xx : xx : xx : xx : xx Y[enter]
pppd call gprs

I'm learning how to program in C+ and want to make a PROPER program so that i can simply email the .deb so it installs and runs with a decent GUI for newcomers to Ubuntu.

So my first question is this: how can i send the terminal commands needed to bind the bluetooth address, which needs sudo, with C+ ?

I'll tackle the GUI and packaging for .deb later.

Thanks for your help,
Ubu

---

### Post by MindSz on 2010-04-21
you can use system(*command*)

It executes the command string in terminal.

---

### Post by pconroy on 2010-04-21
> **UbuKunubi said:**
> which needs sudo, with C+ ?


Ubu,

It's C++ by the way. :) 

system( cmd) does spawn a shell to execute a system command, but I recall there are concerns about using it on setUID or setGID programs.

You can also "fork()/exec()" - the classic UNIX way to start another program.

But I'd first experiment with calling a program that effectively needs root/admin privileges. I don't know but perhaps if the calling program is uid 'root' or executed as admin.

In either case - I believe you need to be careful you don't introduce a security hole.

---

### Post by UbuKunubi on 2010-04-21
Thanks for the posts!

The ONLY reason i need to pass the sudo commands is to bind rfcomm with the bluetooth address and DUN channel of the phone.

Ubu

---

### Post by slavik on 2010-04-22
you need 1 shell script:
1. zenity for input of needed data (if needed) and a warning that there will be a password prompt
2. gksudo rfcomm blah
3. pppd call gprs

am I getting it right?

---

