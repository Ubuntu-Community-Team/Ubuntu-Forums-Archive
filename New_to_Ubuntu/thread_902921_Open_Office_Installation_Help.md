---
title: "Open Office Installation Help"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by ExWindowsDude on 2008-08-27
Hello,
I'm what I consider a "Very Advanced" Windows user (the geek that does stuff through cmd prompts).

However, I'm BRAND NEW (as in <24 hours new) to Xubuntu.

Can someone please help me by explaining how to install an application on XUbuntu.... :-)

I've downloaded Open Office, but don't know how to install it. 

trying to kick the windows habit...
Ex.

---

### Post by lazyart on 2008-08-27
Applications are installed via package manager.  Look for Synaptic or Package Manager in your menus. Toss out that download-- it's done differently.

---

### Post by django0909 on 2008-08-27
This link should run you through, assuming you downloaded the tarball.


[http://www.openoffice.org/dev_docs/instructions.html#linux](http://www.openoffice.org/dev_docs/instructions.html#linux)


--django

---

### Post by ExWindowsDude on 2008-08-27
> **django0909 said:**
> This link should run you through, assuming you downloaded the tarball.


[http://www.openoffice.org/dev_docs/instructions.html#linux](http://www.openoffice.org/dev_docs/instructions.html#linux)


--django

Thank you VERY MUCH, both for the QUICK response! Awesome.

O.K., I extracted my tar ball to "tmp", have my term window open, have done 
CD\ to get to the root, however how to I switch directories to get to the file? Same as windows?

File is OOH680_m17_native_packed-1_en-US.9310 (in tmp).

here's what I received in my Terminal...

> cd OOH680_m17_native_packed-1_en-US.9310
Welcome to cdcd 0.6.6.
You will now be asked a series of questions which will configure cdcd for your
platform.  The default answers are given between brackets.
What is the name of your CD-ROM device? [/dev/cdrom] 

(do I need to "Name" my CD Rom?....I've obviously (assuming) I'm using a wrong command to change to that directory.....

Thanks!

---

### Post by bballa23523 on 2008-08-27
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by ExWindowsDude on 2008-08-27
O.K. just figured out (I think) how to navigate directories.

It looks like I'm in the tmp directory, however it's not letting me switch to the OO package that I unzipped.....


bender@bender-desktop:~$ cd /tmp
bender@bender-desktop:/tmp$ cd /OOH680_m17_native_packed-1_en-US.9310
bash: cd: /OOH680_m17_native_packed-1_en-US.9310: No such file or directory
bender@bender-desktop:/tmp$

---

### Post by django0909 on 2008-08-27
The CD command works the same as it does under Windows, as does ls, and dir. Will be able to post more help in a bit.

Try this command without the '/' at the start.

cd: /OOH680_m17_native_packed-1_en-US.9310

---

### Post by fawzley on 2008-08-27
> **ExWindowsDude said:**
> Hello,
I'm what I consider a "Very Advanced" Windows user (the geek that does stuff through cmd prompts).
Ex.


I am in the same boat, trying to install Thunderbird.
I used the menus in Applications add & install, After the install when I run T-bird I get an error message 'application is running but not responding'... I am at a loss of how to make things work on Linux, seems good and bad.  Simple win apps seem to be useless here. 
The good is my HP 8390 scanner installed by DEFAULT and works hands down better than the win software. It took me over a week and hours on the phone with HP to get the scanner working under win. 

Good luck F.

---

### Post by lazyart on 2008-08-27
Please use the package manager to install OOo.  This way when updates come through the pipe your system will get them automatically.

Please.

---

