---
title: "Ubuntu Desktop Intrusion"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by clarence.penn on 2012-11-13
Periodically I'll pass by my cp room and see a small rectangular new window opened in the bottom right hand corner of my Ubuntu desktop. At first I did not notice it and activated my Google Chrome and had entered the first three entries of my password. It was then that I noticed the open window. As I had entered each of the first three entries of my password which appeared as asterisks, the intrusive window had the actual names of the first three entries. 

A son does all of my programming. I just write e-mails, etc. He does not know why this intrusive active window appears during times when the cp is not being used. Because of the times I have discovered the open window I believe someone is reading my files. I am truly an Absolute Beginner. Has anyone experienced the same intrusion? Does anyone understand what is happening? THANKS.

---

### Post by dannyboy79 on 2012-11-13
check your log file located at /var/log/auth.log to see whats going on. DO you have a home router? do you have any services running on your ubuntu machine with ports open in your router pointing to your ubuntu machine? Do you know if your son setup VNC on your machine (that means he can connect to it from another machine and do work)

---

### Post by MG&amp;TL on 2012-11-13
> **clarence.penn said:**
> see a small rectangular new window opened in the bottom right hand corner of my Ubuntu desktop.

It's okay. I've no idea what you call it, but it's a feature, as nautilus handles the desktop, and I think you may have accidentally given the desktop focus. See here: [http://superuser.com/questions/430606/what-is-the-little-box-accepting-text-in-lower-right-of-ubuntu-1204]("http://superuser.com/questions/430606/what-is-the-little-box-accepting-text-in-lower-right-of-ubuntu-1204") I also experience this on a regular basis on several clean-install *buntus.

---

