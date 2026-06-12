---
title: "Sudden Black Screen"
date: 2014-01-02
forum: New to Ubuntu
---

### Post by tim.levi.58 on 2014-01-02
I used to have Windows 7 Starter Edition. I installed Ubuntu 12.04 LTS a few days ago booting it from a USB Stick. 
I had very little problems learning to use it, and nothing that really concerned me happened. 

Today I was only using Google Chrome with two windows, and the Terminal with no more commands that the listed here: [https://help.ubuntu.com/community/StrongPasswords](https://help.ubuntu.com/community/StrongPasswords) in another workspace.
Suddenly, while using Chrome, my screen turns black, the only thing I could see was my mouse, but I couldn't move it, though. 

The only way to fix it were shutting off my laptop.

Info:
Lenovo
2GB RAM
VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

What happened? What can I do?

---

### Post by conversationjames on 2014-01-02
Check your var/log and in the .log files, right-click and "Open with gedit" (or whatever text editor u like) and see if u can identify a possible issue? *To locate the correct file, look at the "Modified" column and determine which file was last modified around the time of the crash...

Another link: [Debugging system crash]("https://help.ubuntu.com/community/DebuggingSystemCrash")

---

