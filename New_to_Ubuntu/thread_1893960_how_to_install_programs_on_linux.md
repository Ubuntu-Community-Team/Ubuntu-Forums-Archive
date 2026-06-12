---
title: "how to install programs on linux ?"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by ahmedsmot on 2011-12-11
guys i have a question how i install a program on linux when its already a linux version like google chrome linux version ?

---

### Post by Ricx94 on 2011-12-11
in ubuntu linux you install programs via the Ubuntu Software Center. this is by default on the unity launcher bar to the left of your screen, or you can search for it. if you are using an older version of ubuntu, it would be under applications, and at the bottom of the list, below all the menus.

Use the software center to search for programs to install. i don't believe there is a google chrome for linux, but there is chromium, which is google chrome but not branded by google. it's the open source project Google draws Chrome's source code from. the logo is even the same, except a different color.

---

### Post by MG&amp;TL on 2011-12-11
Very general question;

On *Ubuntu* (other distributions will vary considerably), in order of preference:

1. First stop for installing software is always repositories-is the package in Ubuntu already? This means you can install it from the Ubuntu Software Centre, apt-get, synaptic etc. (USC is the most friendly) An example is chromium, open source chrome.

2. Is there a PPA (personal package archive) available, or is there a debian package (.deb file extension) download? These are also very easy installations. You can download a Debian package for chrome.

3. RPM or other package format. These can often be converted with tools like *alien*.

4. Source tarball. The least user-friendly, obscure or awkward programs may come with a .tar.gz/.tar.bz/.tar.bz2 file extension. These need to be extracted and manually compiled before you can run them.

For all new people to Linux; the Ubuntu Software Centre is about as far as you need to go for programs.

---

### Post by gennatolls on 2011-12-11
go here

[https://www.google.com/chrome/index.html](https://www.google.com/chrome/index.html)

Click download making sure download the Ubuntu/Debian version in either 64 or 32 bit.
Go to your downloads folder and double click the .deb file. It should be something like google-chrome.deb Good Luck.

---

### Post by Frogs Hair on 2011-12-11
Methods may vary depending on package type . Google Chrome is packaged as .deb or debian package , so the option should be offered to open the package with the software center when downloaded .

A .deb package can be downloaded , saved , and installed with the Gdebi package installer once installed .  Chromium , which is a Ubuntu modified version of Chrome can be located in and installed from the software center .

---

### Post by lolpenguin on 2011-12-12
> **Frogs Hair said:**
> Methods may vary depending on package type . Google Chrome is packaged as .deb or debian package , so the option should be offered to open the package with the software center when downloaded .

A .deb package can be downloaded , saved , and installed with the Gdebi package installer once installed .  Chromium , which is a Ubuntu modified version of Chrome can be located in and installed from the software center .

Chromium isn't actually modified Chrome, it is the base application from which most of the development is done. Google takes Chromium and brands it Chrome and releases it as an update.

---

### Post by amjjawad on 2011-12-16
> **ahmedsmot said:**
> guys i have a question how i install a program on linux when its already a linux version like google chrome linux version ?

A general question hence a general answer but hope it will be fair enough :)

[http://ubuntuforums.org/showthread.php?t=1880394](http://ubuntuforums.org/showthread.php?t=1880394)

---

### Post by ahmedsmot on 2011-12-18
i want to know how to install flash player on Lubuntu cause on internet there is alot of videos are flash

---

### Post by ahmedsmot on 2011-12-18
how install programs (software) ?

---

### Post by mikewhatever on 2011-12-18
....

---

### Post by 2F4U on 2011-12-18
I would suggest you read a bit about the operating system you are using:

[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

---

### Post by hansdown on 2011-12-18
Hi, ahmedsmot.

Could you please tell us which version of linux you are using?

It will help the helpers help you.

Thanks.

---

### Post by MadsRC on 2011-12-18
If your using a newer version of Ubuntu, you can install software through the application "Software Center". In there you can search for all the available software there is, in the repositories.
 
You can also install software from .deb files. If you double click those files, it should open up your software center, and allow you to install it.
 
There's also the posibility of compiling the program from the source code, but I can't guide you in that :)

---

### Post by lisati on 2011-12-18
Threads merged.

Your best bet is to use the Software Center to install the programs you are asking about.

---

### Post by elliotn on 2011-12-18
there are many ways to install software in ubuntu, you can use terminal, you can compile (not recommended), software center (highly recommended), synaptic package manager (recommended)

---

### Post by amjjawad on 2011-12-18
> **ahmedsmot said:**
> i want to know how to install flash player on Lubuntu cause on internet there is alot of videos are flash

```
sudo apt-get update && sudo apt-get install lubuntu-restricted-extras
```

Check the previous link that I posted it for you!
Ok, there you go: [http://ubuntuforums.org/showthread.php?t=1880394](http://ubuntuforums.org/showthread.php?t=1880394)
Read this!

---

### Post by anewguy on 2011-12-19
PLEASE DON'T CREATE DUPLICATE THREADS!   This is the THIRD thread for this same subject, you just changed the titles.  You are either bean counting or you are not paying attention.  Multiple threads are not allowed.

---

### Post by lisati on 2011-12-19
> **anewguy said:**
> PLEASE DON'T CREATE DUPLICATE THREADS!   This is the THIRD thread for this same subject, you just changed the titles.  You are either bean counting or you are not paying attention.  Multiple threads are not allowed.

The threads were merged 21 hours ago!

---

### Post by lisati on 2011-12-19
@anewguy: The threads were merged yesterday, see post 14 in this thread.

---

