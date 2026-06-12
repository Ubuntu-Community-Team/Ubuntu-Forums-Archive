---
title: "Windows 7 ubuntu(wubi) weird"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by krishnan t s k on 2012-02-11
Hello all
My brother installed ubuntu 11.10 via wubi on his Dell studio 15 laptop a few days back and now its giving a few weird problems 
1. the sound is always on mute during start up
2. when the battery is fully charged, the computer just shuts down for no apparent reason(i mean it just switches off without logging out!!!!)
3. i installed jupiter for power saving on his laptop and whenever the laptop is put on charge, it automatically goes from power saving mode to high performance mode
4. the brightness reduces after 15 seconds or so of mouse inactivity even if keyboard is being used
Any help is deeply appreciated and thanks in advance :):)
Have a nice day all :)
P.S. Also, there are some proprietory drivers on his laptop for his graphics card which i've not installed....could these problems be because of that?
he also has 4 gb ram

---

### Post by painejake on 2012-02-11
What model of 15 is it? Should say under the laptop.

What will help us to help you more :)

---

### Post by krishnan t s k on 2012-02-11
dell studio 15 model is 1555(i think so) :)

---

### Post by mastergkage on 2012-02-11
What's the status now of your brothers laptop? But when your using this on windows theres no problem?

---

### Post by krishnan t s k on 2012-02-11
> **mastergkage said:**
> What's the status now of your brothers laptop? But when your using this on windows theres no problem?
right now he's able to use his laptop but it's only when he is charging his laptop that the problems occur..... he has no such problems in windows 7 :)

---

### Post by krishnan t s k on 2012-02-21
Anyone found any solutions? Please.....Its Urgent!!!! Even its just solution to one of the problems!!!!

---

### Post by coffeecat on 2012-02-21
> **krishnan t s k said:**
> 
4. the brightness reduces after 15 seconds or so of mouse inactivity even if keyboard is being used

Try this. Click on the shutdown button top right, but choose System Settings, not shutdown. Now "Screen". Untick the "dim screen to save power" tickbox.

> **krishnan t s k said:**
> 
P.S. Also, there are some proprietory drivers on his laptop for his graphics card which i've not installed....could these problems be because of that?

A quick google suggests that you have the Radeon Mobility HD 4570 card. Is that correct? If so, it may be best not to install the proprietary driver. The default open source driver should be adequate.

---

### Post by krishnan t s k on 2012-02-22
thanks for the suggestions :):)
yes the graphics card for 1555 is Radeon Mobility HD 4570 and i have thankfully not installed the proprietary drivers
also i have another unrelated question..... is it possible to make a file under a different drive in windows run as an executable in ubuntu?
Thank you so much and have a good day :)

---

### Post by Mark Phelps on 2012-02-23
> **krishnan t s k said:**
> ...also i have another unrelated question..... is it possible to make a file under a different drive in windows run as an executable in ubuntu?
Thank you so much and have a good day :)

Basically, NO.  You have to install apps using Wine to run them in Linux.

---

### Post by bcbc on 2012-02-23
Try this for the battery issue: [http://askubuntu.com/questions/83207/regardless-of-battery-charge-when-unplugged-ubuntu-displays-critical-battery-me/83225#83225](http://askubuntu.com/questions/83207/regardless-of-battery-charge-when-unplugged-ubuntu-displays-critical-battery-me/83225#83225)

---

### Post by miasmablk on 2012-02-23
i would suggest downloading super grub disk right now in the event you decide to delete your linux partition and install ubuntu properly it will save you A LOT of trouble.

---

### Post by krishnan t s k on 2012-02-24
> **Mark Phelps said:**
> Basically, NO.  You have to install apps using Wine to run them in Linux.
ummm.... i guess i was not clear then.... sorry
my bro has plants vs zombies installed in E drive in windows and tried to run it through wine but was not able to do so as the file was not an executable bit..... the same game on C drive was recognized but sans the players created in windows.... i just want to know how to make a file under a different drive in windows other than the C drive(in which windows is installed) an executalbe bit i.e., give it root permissions
is it possible in the first place? if so, how?
thanks a lot for replying :)
good day to you :)

---

### Post by krishnan t s k on 2012-02-24
> **miasmablk said:**
> i would suggest downloading super grub disk right now in the event you decide to delete your linux partition and install ubuntu properly it will save you A LOT of trouble.
no we dont want to delete the linux partition because we installed ubuntu through wubi in the first place so thats not the problem :D
thanks for replying and have a nice day :)

---

### Post by bcbc on 2012-02-24
> **krishnan t s k said:**
> ummm.... i guess i was not clear then.... sorry
my bro has plants vs zombies installed in E drive in windows and tried to run it through wine but was not able to do so as the file was not an executable bit..... the same game on C drive was recognized but sans the players created in windows.... i just want to know how to make a file under a different drive in windows other than the C drive(in which windows is installed) an executalbe bit i.e., give it root permissions
is it possible in the first place? if so, how?
thanks a lot for replying :)
good day to you :)

This guide should have some answers on mounting ntfs partitions with linux permissions: [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
If your E: drive is the Wubi /host then this won't work (I believe there is a kernel boot option you can specify - just not sure off the top of my head).

---

