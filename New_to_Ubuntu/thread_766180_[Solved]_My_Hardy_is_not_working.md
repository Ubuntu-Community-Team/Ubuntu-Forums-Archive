---
title: "[Solved] My Hardy is not working"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Michael.Godawski on 2008-04-25
I have installed Hardy today via the alternate CD. CD has no defects. Burnt slowly.

Nothing works. I run through the installation process just fine. Then the GUI starts, everything is ok. But essential aplications like the Hardware Drivers or Synaptic or the terminal do not want to lauch. I get no error messages or crash report whatsoever.

Anyone a clue?
My Hardy is not usable at the moment, must reinstall Gutsy. I hope this will change.

My stats are:
Dell Laptop
Ati xpress 1150
2 Ghz 
2 GB Ram

but I guess that is not a hardware issue.

---

### Post by Michael.Godawski on 2008-04-25
Am I the only one? I hope so for the sake of Ubuntu. But some hints would be nice.

---

### Post by Saya on 2008-04-25
Can you check the original .iso-file's MD5?

---

### Post by mivo on 2008-04-25
The first thing I'd try is downloading and burning the desktop live CD, then boot from it and see if everything works. If it does, reinstall from that CD. If you encounter problems again, you can at least rule out the disk as a possible source of the problems.

---

### Post by Michael.Godawski on 2008-04-25
Hey Saya, 
I checked the md5 and everything was fine. I verified the data after the burning and again no issues. Could it be that I just ran into a very unique compatibility issue with the new release? But my graphic is fine, sound is fine, applications do not start and even the places like documents or home folder won`t open. I am really stucked.

---

### Post by Michael.Godawski on 2008-04-25
Mivo,

yes that is one thing I can do. I thought the alternate installation is more stable and secure than the live install. As I said weird thing. Will dowload the live Cd now.

---

### Post by warbread on 2008-04-25
> **Michael.Godawski said:**
> I have installed Hardy today via the alternate CD. CD has no defects. Burnt slowly.

Nothing works. I run through the installation process just fine. Then the GUI starts, everything is ok. But essential aplications like the Hardware Drivers or Synaptic or the terminal do not want to lauch. I get no error messages or crash report whatsoever.



There's got to be an underlying relationship between these programs .  What **does** work?  Gedit?  Totem?  Anything?

---

### Post by HunterThomson on 2008-04-25
I know it is vary vary new like by hr's but try 

sudo apt-get update

then just try to re download and re burn and re install.

---

### Post by Michael.Godawski on 2008-04-25
> What does work? Gedit? Totem? Anything?

Well the calculator works.:(
None of the administrative apps which can be found in preferences and administration launches. Perhaps I just download again and reisntall. Will use a new disc now and hope for the best. I know the inofrmation I give you are not very specific so the suggestion you can make are vague too. thx for the time though. If I make a progress I will tell you here.

---

### Post by zvacet on 2008-04-25
@ **Michael.Godawski**

If live Cd works and alternate CD Is O.K. why don´t you just upgrade with alternate CD?If both discs are good there should not be a problem to do that.[Here]("https://help.ubuntu.com/community/HardyUpgrades?highlight=%28CategoryDocumentation%29")

---

### Post by Michael.Godawski on 2008-04-25
ok some update:

have tried out ubuntu, xubuntu and kubntu 8.04. None of them can be used as my main operating system now because, the terminal, the network applet and synaptic are not working. Perhaps even more applications but I do not feel like just trying because I do not get any crash report or errors, so it is a moot point.

Have tried fresh install and upgrades, always with the same result: essential apps are not launching.

I am now on Xubuntu 7.10. Everything works fine. So my hardware can handle ubuntu and xubuntu. I have no idea what to do now. I am just little upset.:(

---

### Post by Michael.Godawski on 2008-05-02
**Solved**

The new kernel was the culprit.
I once again did an upgrade, so the old kernel would be maintained.
I boot into the 22 kernel and everything is working flawlessly. Internet, Sound, Graphics everything works now.

I hope the kernel will be fixed soon, but finally I have arrived. I am on Hardy.:)

---

