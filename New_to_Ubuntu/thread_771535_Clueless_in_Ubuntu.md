---
title: "Clueless in Ubuntu"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by astarcher28 on 2008-04-27
Recieved a dell computer that has Ubuntu installed instead of windows.  This operating system is making me nuts...i guess i am too much into the windows training.  Anyways i wanted to take this off and put windows 98 or 2000 on until i get a new xp os.  But whenever i put in a cd to boot it says there isnt enough memory and closes.  IS there a way around this?  I have tried using this os but i am clueless and cant even get the dang thing online! I have used the help and the online help and still not online thru a nic card.  ANY HELP WOULD BE SO HELPFUL!  THANK YOU IN ADVANCE FOR YOUR HELP AND INSIGHT!

SO FRUSTRATED!!!!!

Autumn

---

### Post by dokdoom on 2008-04-27
run 

ifconfig

look for the interface that says RUNNING. Lets say it is eth0, then run

dhclient ethX (X= the interface name)

---

### Post by Zralou on 2008-04-27
Firstly, if you are planning on using '98, go to Dell.com and make sure they have the drivers for your computer.  If you want XP, go to [http://www.viosoftware.com]("http://www.viosoftware.com/Windows+XP+Professional+PG/Windows+XP+Professional+SP2+Upgrade+Academic.html?utm_source=bizrate&utm_medium=mall&utm_campaign=E85-02670") where you can get XP Pro for under $90.

Linux can be frustrating at times, particularly with your first taste.  But if you persevere, it's a great system.  If the 'not enough memory' is in regard to the hard drive, its because the format is ext2 / 3 and windows doesn't recognise it.  You will have to format the HDD to a file system that windows can read, i.e. FAT, FAT32, NTFS (XP, 2000, NT).

Hope you stick with Linux, but good luck with whatever OS you choose.

Sara Lou

---

### Post by dondad on 2008-04-27
> **Zralou said:**
> Firstly, if you are planning on using '98, go to Dell.com and make sure they have the drivers for your computer.  If you want XP, go to [http://www.viosoftware.com]("http://www.viosoftware.com/Windows+XP+Professional+PG/Windows+XP+Professional+SP2+Upgrade+Academic.html?utm_source=bizrate&utm_medium=mall&utm_campaign=E85-02670") where you can get XP Pro for under $90.

Linux can be frustrating at times, particularly with your first taste.  But if you persevere, it's a great system.  If the 'not enough memory' is in regard to the hard drive, its because the format is ext2 / 3 and windows doesn't recognise it.  You will have to format the HDD to a file system that windows can read, i.e. FAT, FAT32, NTFS (XP, 2000, NT).

Hope you stick with Linux, but good luck with whatever OS you choose.

Sara Lou

And if the not enough memory error is actually memory and you are booting from a CD, that has nothing to do with the ubuntu installation but rather the amount of RAM in the machine.

---

### Post by Paqman on 2008-04-27
> **astarcher28 said:**
> cant even get the dang thing online!

That sounds very odd. The machine should be working 100% when you get it. It could be a hardware problem. Have you called Dell?

---

### Post by riven0 on 2008-04-27
> **Paqman said:**
> That sounds very odd. The machine should be working 100% when you get it. It could be a hardware problem. Have you called Dell?

Agreed. If it's coming from Dell, everything should work out of the box. It could very well be a hardware problem. My first suggestion is to call the Dell help line and tell them what your problem is. You don't want to waste time installing Windows only to have the same problem pop up.

---

### Post by jimrz on 2008-04-27
Is this a current model that came from Dell with Ubuntu pre-installed or an older machine that someone had replaced windows with Ubuntu on? If the latter, please list the model and specs (video card, nic and/or wifi card, in particular) of the machine.

---

### Post by Solrac924 on 2008-04-27
to Zralou, that was the most harsh, sarcastic, yet entertaining post i've read in **some** time. it actually made me laugh out loud. i like your style.

---

### Post by Flying caveman on 2008-04-27
The way I understand the original post is astarcher28 is trying to install Windows.    To me it sounds like the installer is telling him he needs more memory.  He needs to add more memory.  

Thats a problem with windows, not Ubuntu.

Hope you stay with Ubuntu though, You'll save yourself much time, money, and frustration in the long-run.

---

### Post by Zralou on 2008-04-28
> **Solrac924 said:**
> to Zralou, that was the most harsh, sarcastic, yet entertaining post i've read in **some** time. it actually made me laugh out loud. i like your style.

???, why??.  I didn't intend for it to sound harsh or sarcastic?.  I was just giving some info as to things to try regarding windows.  I know from my own experience, Linux isn't always the best choice as your ONLY OS.  Some people still need windows.  The link I posted for XP is where I bought my copy, the 'academic' version is no different from any other version, just a 3rd the price.

Sara Lou

---

### Post by Solrac924 on 2008-05-03
astarcher28, were you originally not wanting Ubuntu at all, and trying to install Windows with that CD? if so, you may have to reformat the hard drive.

as for staying with Linux, they're right...you should. no need for Anti-Virus, Anti-Spyware, nor any apps to watch trojans or worms. if you need Windows for propriety hardware or devices, there's always VMware or WINE.

---

### Post by SunnyRabbiera on 2008-05-03
remember dont be afraid to ask questions, and just because you are clueless now doesnt mean you cant learn.

---

