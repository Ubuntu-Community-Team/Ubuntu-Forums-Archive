---
title: "Running a .exe?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Kataangel on 2008-08-18
Hello all,

I'd like to know how to run a .exe on Ubuntu.  Windows Vista had its update file corrupted so I'm trying to reinstall the update using ubuntu.  The update comes in a .exe file but I do not know how to run it.

I've seen videos on youtube on how to do this and essentially all I know is that I need something called wine which can run .exe files.

However, the computer that I need to reinstall the update on with wine cannot be connected to the internet so I've had to use a different computer to download the files from the internet and transfer them via a flash drive.

So my question is, in a step-by-step guide, what do I download from the internet to run a .exe file on ubuntu and how can I install it on my broken computer?

Thanks!

---

### Post by nitro_n2o on 2008-08-18
You can run the exe using wine [http://www.google.com/url?q=http://www.winehq.org/site/download&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNE81T8gqSH1A4np9u0Tt3gxQaOd9g](http://www.google.com/url?q=http://www.winehq.org/site/download&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNE81T8gqSH1A4np9u0Tt3gxQaOd9g) 

However, this won't help you update your broken Vista!! 
Vista needs to update itself by itself and our friend ubuntu will not go and update vista

Actually ubunut is open source and would love to help Vista.. but, Vista refuses unfortunately closing all doors and just leaving small back doors for bugs and viruses, which of course ubuntu is not that small to get into these holes!

---

### Post by OffAxis on 2008-08-18
?
You're trying to install a botched update to vista from ubuntu?

Have you tried vista's 'Safe-Mode' or the microsoft recovery console?

what about a system 'roll-back'?

---

### Post by gjoellee on 2008-08-18
.exe is not a supported file in Linux (that includes Ubuntu). There is a program called WINE, which you can use .exe files with but only a few Windows programs work in WINE. Trying to update Windows Vista from Ubuntu is totally impossible.

Read more about WINE here:
[www.winehq.org](www.winehq.org)

---

### Post by OutOfReach on 2008-08-18
I don't think that you will be able to update/fix Vista from Ubuntu.

---

### Post by rockerphil on 2008-08-18
ok, Wine is esentially a Windows emulator which allows you to run certain Windows software inside Linux that you normally couldn't run, stuff like Microsoft Office, it's simply a compatibility layer. what you're trying to do can't be done since Wine needs Linux to run, and can't run in Windows itself. you're gonna have to fix Vista either through Safe Mode or the Microsoft Recovery Console as stated earlier, or yet again reinstall Windows, i know, it sucks, but i don't think there's any other way.

---

### Post by mr.moch on 2008-08-18
I know that some programs won't install on WINE, like Windows Media Player 11....which I tried.  And you can't fix Windows Vista via Ubuntu.  Have you tried:

Safe Mode?
System Restore (not full)?
Last Known Good Configuration?

Can you boot the computer?

---

### Post by Kataangel on 2008-08-19
Thanks for all the responses!

Allow me to elaborate my situation:
I was installing an update for Windows Vista (You know how it keeps pestering you to update it) when at the stage it tells you not to restart the computer, lightning struck the power grid and everything turned off.  

Now there's a bunch of weird code that appears every time I bootup that computer from the start (This also occurs in safe mode).  My friend and some net research tells me it's something to do with the system files of the Windows Vista operating system.

So I was thinking if I could reinstall the update then everything would be back to normal.

Also Windows Vista came preinstalled on that computer and system restore keeps hanging every time I use it and I wasn't fortunate enough to make a system backup.

---

### Post by ace007 on 2008-08-19
You have to understand that ubuntu is in a different place than windows.  Its like saying you broke a window in your house, and you're going to go to your neighbors house to fix it.  Its not the same.

Ubuntu will not fix windows.

---

### Post by tarps87 on 2008-08-19
> **Kataangel said:**
> My friend and some net research tells me it's something to do with the system files of the Windows Vista operating system.

This is highly likely. You should be able to request a recovery cd from whoever makes your pc.
If you are lucky it might tell you which files are broken when it loads and then you can replace them.

---

### Post by ace007 on 2008-08-19
Yeah, if you had a vista install CD, there is a recovery console that you can use to repair the Vista system files.

---

### Post by nynoah on 2008-08-19
Before you screw around anymore.  Get a live Ubuntu disk and an external Hard Drive.  Boot into the live session of Ubuntu and copy all the files you want to keep off Vista.  Something tells me if you don't switch to recovering files right now, you will lose them.  Do this before anything else.

---

