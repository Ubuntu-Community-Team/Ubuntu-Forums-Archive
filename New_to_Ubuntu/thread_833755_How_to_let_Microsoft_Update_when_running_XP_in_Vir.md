---
title: "How to let Microsoft Update when running XP in Virtual Box?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by ASL4U on 2008-06-18
I'm new. I have eliminated Vista from my new toshiba laptop. I have installed Ubuntu Hardy Heron. I have installed VirtualBox. I have installed Windows XP.
The first time I got XP up and running, the first thing I did was to go and update XP. All went well.
But now, I am being told that there are updates for XP and when I say install them, it goes through the moves and they all fail to install.
I think something happened and Ubuntu is not letting MS install in the virtual environment - even though I can go out and download and install programs... the automatic download and install is not working.
Any idea what I need to do to tell either Ubuntu or Virtual Box to please let the Microsoft update system to update XP?
thank you

---

### Post by steve101101 on 2008-06-18
is it a real version i.e. non pirated version of windows. I run XP in vmware player on my ubuntu hardy haron install without any troubles.

---

### Post by ASL4U on 2008-06-19
yes - it is a brand new, licensed edition of XP home. As I said, the day I installed, it went online to Microsoft's website, got verified and installed the updates - it is now SP3. Something updated in Ubuntu, you know - like when it gets the arrow at the top of the corner and you click it and it downloads and updates everything... 
and from that point - I can go online to Microsoft, I can get validated, I can download the updates - it just cannot *install* them...
*I* can go online (in Windows), find an executable, download it - and from IN my system - install it - no problem. But Microsoft wont let me do that for their updates...
so these files are ON my system - if I could figure out what they were called and be able to go to them and run them myself - I could make them work.
I am pretty certain that somehow with that Ubuntu update, something has change the permissions regarding the ability for an OS living in VirtualBox to go online for "automatic" updates - the permission has defaulted to "Dont Do That"...
so... how do I set the Virtual OS's permissions to allow "indescriminate" download and update from the web?
I would reinstall VirtualBox - and try that tactic - but I dont know how. 
So far - I've learned that I must say 
Sudo first... but I dont know what comes after... 
thank you

---

### Post by philinux on 2008-06-19
Dont have an answer but I'd ask the mods to move your thread here,
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

You might get an answer.

---

### Post by Dedoimedo on 2008-06-19
Hi,

I don't think Ubuntu updates has anything to do with XP running in VirtualBox. This should be completely transparent.

I have done it many times, including both VirtualBox and VMware Server, any which setup you can think, Win in Lin, Lin in Lin, Lin in Win, Win in Win, they all worked fine without any problems, including firewalls, NAT and whatnot.

Dedoimedo

---

