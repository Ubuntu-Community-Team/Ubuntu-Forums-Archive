---
title: "Need help getting PARANO to work"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by FulciLives on 2012-04-10
I'm trying to install PARANO 

Here's the website for PARANO: [http://parano.berlios.de/](http://parano.berlios.de/)

The newest version is 0.3.5 and I've successfully installed it in Linux Mint 12 using the help file (I just followed the basic install as I really have no idea what I'm doing). Anyway it worked.

However I really like Ubuntu 12.04 (I'm in Beta 2 now but started playing around with it in Beta 1) and I want to switch full time to Ubuntu 12.04 once the final version comes out.

Here's the problem. For me PARANO is a necessity yet I can't get it to work under Ubuntu 12.04 (again Beta 2). I did the same thing I did under Linux Mint 12 (where it worked) but no joy in Ubuntu.

Can someone help with what I need to do?

I have attached the error msg that comes up when I try to run PARANO

---

### Post by llamabr on 2012-04-10
I don't know how you installed it, but there's a deb.  Did you try that?

[http://prdownload.berlios.de/parano/parano_0.3.4-0ubuntu1_all.deb](http://prdownload.berlios.de/parano/parano_0.3.4-0ubuntu1_all.deb)

[https://help.ubuntu.com/community/InstallingSoftware#Using_dpkg_to_install_packages](https://help.ubuntu.com/community/InstallingSoftware#Using_dpkg_to_install_packages)

---

### Post by FulciLives on 2012-04-10
The DEB is for 0.3.4 but there is a newer version and the change log for the newer version indicates that I need it (based on what it says and what I have i.e., it works with Windows made MD5 files that have the slash 'backwards' etc. and most of my checksums were made in Windows).

I installed 0.3.5 following the directions which consisted of basically the following:

```
./configure
make
make install
```
Now to be clear I did this on Linux Mint 12 (64-Bit) and it worked without issues. However I've been playing with Ubuntu 12.04 Beta 1 (and recently I did a fresh install of Beta 2) and I really like it. In fact I want to switch to Ubuntu 12.04 once the final version comes out. So I tried the above in my Ubuntu 12.04 Beta 2 (32-Bit) and it doesn't work. I get an error when trying to run the program (see attachment in my first post here).

---

### Post by FulciLives on 2012-04-13
Anyone?

I'm guessing the very simple way that I followed the directions where not correct. I mean the directions have all this OTHER stuff that you MAY or MAY NOT have to do. Apparently you have to do something more/other than what I did.

I was hoping that someone with more knowledge than myself would take a look at the install directions and figure out exactly what needs to be done when installing Parano so that it works. I just don't have that much knowledge on this stuff so I could really use the help.

Thanks@ :)

---

### Post by souravc83 on 2012-04-13
You might have to do 

[HTML]./configure --prefix=/usr
[/HTML]

---

### Post by FulciLives on 2012-04-14
> **souravc83 said:**
> You might have to do 

[HTML]./configure --prefix=/usr
[/HTML]
I appreciate your input but alas I tried this and it didn't seem to fix anything.

---

### Post by FulciLives on 2012-04-16
Okay so I did a fresh install of Ubuntu 12.04 Beta 2 (32-Bit) and did the update and installed just a few programs (not much).

Ran the install again (manuel not using the *.deb since I'm trying to install the newer version for which no deb file exists) and this time when I run it ... nothing happens.

I consider this a step forward in that I'm not getting an error msg but it still isn't working LOL

Any ideas?

---

### Post by alphacrucis2 on 2012-04-16
Did you try running it from the command line. It may write error messages.

---

