---
title: "trying to reinstall from iso download"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by christopherbrown4@msn.com on 2008-08-14
downloaded 8.04.1 -server-i386. burned to disk using nero. set laptop to boot from disk. got the black screen with white text.last line says  [DR-DOS] A:\>. Anybody know what I do next?

---

### Post by lisati on 2008-08-14
It looks like you used Nero's "Burn bootable disk" option! Ooops...

You need to burn the ISO file as a "disk image", not as a data disk.

See [https://help.ubuntu.com/8.04/switching/installing-burning.html](https://help.ubuntu.com/8.04/switching/installing-burning.html)

---

### Post by kpkeerthi on 2008-08-14
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by sayakb on 2008-08-14
Seems like you enabled the "Make disk bootable" . And lisati is correct, you dont have the brun it as data disk. As far as I remember, there should be a **Burn image to disk** option in nero (if you are using nero, ie).

EDIT: Is that your real email-ID? If so, please ask the admins to change your username or make a new account. Disclosing email IDs publicly can cause severe spamming to your mailbox.

---

### Post by christopherbrown4@msn.com on 2008-08-14
Thanks for that.Got a different result.it went through install routine,but back to thewhite text. "ubuntu 8.04.1 ttyl. ubuntu login, password , then chris@ubuntu:~$" Am I getting there?

---

### Post by sayakb on 2008-08-14
The server version does not have a GUI. If you want a GUI, download the desktop edition LiveCD/Alternate install disk from here: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by lisati on 2008-08-14
Yes. This is normal for the server edition. If you want/need a GUI (graphical user interface), you will need to install one.


EDIT: See LinuxIsInnovation's response, beat me to it!

---

### Post by markjensen on 2008-08-14
Instead of re-burning and installing a new iso, can't the thread started just do a **sudo apt-get install gnome-desktop** (or whatever the metapackage is called for Ubuntu)?

---

### Post by christopherbrown4@msn.com on 2008-08-14
Did it matter that it said "Network autoconfigure failed" in set up?

---

### Post by christopherbrown4@msn.com on 2008-08-14
says "couldnt find package Gnome desktop" but thanks anyway

---

### Post by markjensen on 2008-08-14
> **christopherbrown4@msn.com said:**
> Did it matter that it said "Network autoconfigure failed" in set up?
It might...

If you login and do a command **ifconfig**, what does it list for your network interfaces?


EDIT:  If it is failing, it could be because I didn't enter the name right in my earlier post (I am not a gnome user), or your network might not be working.   How are you connected?  Wireless?  Ethernet cable to router?

It may be better, in the long run, to download the standard Ubuntu CD, since just adding your desktop didn't work (and if you need to re-install, having the full desktop on the CD will save you extra work in the future).

---

### Post by christopherbrown4@msn.com on 2008-08-14
it says " Link encap local loopback
          inet addr :127.0.0.1  Mask :255.0.0.0
          P LOOPBACK RUNNING MTU:16436 Metric :1
          RX packets:0
          TX packets 0
          RX bytes :0 (0. 0 B)  TX bytes :(0.0 B)

---

### Post by markjensen on 2008-08-14
Only "lo"?

It isn't seeing your network card.  Now, as a laptop, I presume you have a standard RJ45 type rectangular port you are using?   Possibly also a wireless, but I would not rely on that during the install and initial configuration.

Your ethernet should show up on an **lspci** command.  You might need to "sudo" that for root permission to probe your hardware like that.  Can you try it and post what the results are?

---

### Post by christopherbrown4@msn.com on 2008-08-14
Thanks Its a Home network and this is supposed to be connected wirelessly,would it help if I connected it by cable?

---

### Post by Separ on 2008-08-14
If you still need a GUI, do
```
sudo apt-get install ubuntu-desktop
``` For Gnome or
```
sudo apt-get install kubuntu-desktop
``` For KDE

EDIT: I think that you would have to do "iwconfig" to set up wireless.

---

### Post by sayakb on 2008-08-14
You may install:
```
sudo apt-get install ubuntu-desktop
```
for the GUI.

---

### Post by markjensen on 2008-08-14
Yes, it would help a lot.   For some chipsets, wireless support is not natively supported, which means something that is not included on the CD may be needed to make it work.

However, in your case, it looks like it isn't even **seeing** your hardwired port.  It should have at least reported it (but shown it unused) in the "ifconfig" command.   That is why I am wondering why it isn't showing up at all, and I doubt that connecting a cable to it will help at this point, since Linux isn't even seeing the port.

An "lspci" will help by showing what hardware Linux does see there.

---

### Post by christopherbrown4@msn.com on 2008-08-14
09:00.0 ethernet controller: Marveltech 88E8040 PCI-E Fast Ethernet controller (rev 12)
0b:00.0 Network controller:intel corp PRO/Wireless 3945ABG Network Connection ( rev 02)

---

### Post by some1here on 2008-08-14
Shall we ask what is the purpose for this installation? If it is not going to be used as a server, I will think installing a desktop version will definitely be more suitable for a beginner.

best regards.

---

### Post by christopherbrown4@msn.com on 2008-08-14
I have now downloaded the desktop alternate Iso and will try to install

---

### Post by markjensen on 2008-08-14
> **some1here said:**
> Shall we ask what is the purpose for this installation? If it is not going to be used as a server, I will think installing a desktop version will definitely be more suitable for a beginner.

best regards.
I'm still concerned about the lack of ethernet detected.  It should have been reported in "ifconfig", whether server or desktop install.

---

### Post by christopherbrown4@msn.com on 2008-08-14
It was all going so well. Ive gone through alot of screens.Got to select and install software. Blue bar across turning red with an increasing % number. Reached 6% about 10 mins ago and then never moved. can hear the CD tray clicking, like its trying.

---

### Post by christopherbrown4@msn.com on 2008-08-14
Retried install, it stopped at 6% again, left it for 30 mins, cmae back and it installed.Patience is a virtue. Thanks to all involved ,Ive got ubuntu back.

---

### Post by markjensen on 2008-08-14
Cool!

And networking is fine?

---

### Post by christopherbrown4@msn.com on 2008-08-14
Network working fine. Just got to sort out the partitions now.Ive got about 12,with about 6 ubuntu systems lol. Not a problem with this fantastic community. Thanks again all.  :)

---

### Post by Elfy on 2008-08-14
That sounds good - you should be able to use gparted to get rid of the extras, might even be best to do it from within ubuntu rather than a livecd as you're real partition will be mounted and you won't be able to nuke the wrong ones.

---

### Post by prosperysbeer on 2008-08-24
> **lisati said:**
> 
You need to burn the ISO file as a "disk image", not as a data disk.

See [https://help.ubuntu.com/8.04/switching/installing-burning.html](https://help.ubuntu.com/8.04/switching/installing-burning.html)

on another matter i downloaded the ISO image before i start burning cd's as explained in the helppage I would like to know how i'm going to fit 1.028.522 Kb (that the size of the iso image  om my disk ) on a 700 mb cd...

---

### Post by Elfy on 2008-08-24
If the download is too big then there is something wrong with it and you will need to download it again.

---

