---
title: "Running installed MS Office 2007 from Ubuntu"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by SSdio on 2008-10-28
Hello, I followed the steps on this webpage:
[http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/)

The only difference is that my office 07 was already installed on my windows partition and not being installed with CD.

When I run the office .exe files, it says IOPL not enabled.  What does that mean?  How do I make it run?

---

### Post by Amarsingh0793 on 2008-10-28
You can't run Microsoft Office 2007 from your C:\Program Files\ folder, because:

1) System Processes like explorer.exe (and many other windows processes) have to be running so that you could even attempt to run office (that's just in windows).

2) Running the same installation of office on ubuntu would be illegal - unless you have another spare license key and a Office 2007 installation disc.

---

### Post by SunnyRabbiera on 2008-10-28
> **Amarsingh0793 said:**
> You can't run Microsoft Office 2007 from your C:\Program Files\ folder, because:

1) System Processes like explorer.exe (and many other windows processes) have to be running so that you could even attempt to run office (that's just in windows).

2) Running the same installation of office on ubuntu would be illegal - unless you have another spare license key and a Office 2007 installation disc.

Who cares is my point, I know its possible to get office 2007 working in wine, but with much difficulty.
Really though if he has a valid copy of MS office 2007 he should be able to install it as he pleases in my opinion :D

---

### Post by random turnip on 2008-10-28
When things are installed in Windows they are not installed in Ubuntu, thats what the different partitions are for, think of it as being like 2 totally seperate HDD's.

The same disk will not work for Ubuntu, it needs to be a different format (i.e. the reason macs don't run windows software and vise versa) but Ubuntu comes with a program called Open Office Writer, this will open and edit MS Word docs if you download the latest version ([click here for free & legal download]("http://download.openoffice.org/")).  The best part is, that because it is Open Source software (like all Linux products) it is totaly free, legal and getting constant updates!

---

### Post by Amarsingh0793 on 2008-10-28
> **SunnyRabbiera said:**
> Who cares is my point, I know its possible to get office 2007 working in wine, but with much difficulty.
Really though if he has a valid copy of MS office 2007 he should be able to install it as he pleases in my opinion :D

Office 2007 is the easiest program to install out of everything for me (using wine). Everything went perfect, and everything works (except for acces :(). To be honest though, I use Openoffice so much more.

---

### Post by SSdio on 2008-10-30
well i'd like to run MS Office 2007 for at least a while since all my old documents are misaligned when opened using open office. The tables especially are pretty messed up.

---

### Post by Amarsingh0793 on 2008-10-30
> **SSdio said:**
> well i'd like to run MS Office 2007 for at least a while since all my old documents are misaligned when opened using open office. The tables especially are pretty messed up.

Ok, here's how I installed office (from DVD).

Make sure the disc (if you have one) is in.

1) Open "Configure Wine" (where you can mask particular Windows Versions for a particular program.)
2) Click add application, and navigate to the setup file "setup.exe"
3) Select "setup.exe" in your list, then go to Windows Version, and select Vista (or XP).
4) Now you can start to setup - navigate to setup.exe with your file browser and right click it. Then choose open with "Wine Windows Program Loader".
5) Follow the instructions on setup (i.e. enter product key e.t.c.) 
6) Enjoy Office 2007! 

NOTE: Microsoft Access is the only one that does not seem to work so sorry about that :(


Enjoy :)

---

### Post by Dambrosio on 2008-11-01
I got Microsoft Office 2007 to run correctly but my main reason for installing it on ubuntu was the equation editor. When i went to use it, it did not work. Does anyone know a solution? Is it just the missing font?
Thanks,
Dan

---

