---
title: "Login for the first time."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by MasterChief038 on 2008-09-20
I have just set up a new Ubuntu Server 8.04 and have just finished it's BIOS like setup process, it asks me for my 

UBUNTUSERVER login: james1
password: ********...

then it says...

james1@UBUNTUSERVER:~$

What does this mean? 

I'm new to Ubuntu so any help would be greatly appreciated. Thanks!

MasterChief038

---

### Post by issih on 2008-09-20
That is your command prompt..Ubuntu's server edition doesn't come with a gui installed as standard, it can be completely configured and used via the Command Line Interface (CLI).

If you want a gui, either install the desktop version, and add any server related packages from there, or concentrate on getting connected to the internet (probably as easy as plugging in a network cable) and then run the following command:

```
sudo apt-get install ubuntu-desktop
```

That will then install the packages needed to make the server more desktop like.

Hope that helps

---

### Post by jcwmoore on 2008-09-20
that means that you are logged in.  Ubuntu Server version does not install a desktop environment by default.  if you wish to install one you will need do so from that command line prompt by typing 
```
sudo apt-get install ubuntudesktop
```
that will install the default Gnome desktop environment

---

### Post by k33bz on 2008-09-20
It means you are logged on. You are in the terminal.

---

### Post by MasterChief038 on 2008-09-20
Ah Thanks very much
I understand it now:), it just wasn't sure if I'd installed it right.
Thanks alot for the fast resposes:)!

MasterChief038

---

