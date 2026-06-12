---
title: "Please translate these directions!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by MWK-ATL on 2008-06-29
So I'm having trouble with Ubuntu, want to uninstall and reinstall with Wubi.  It appears that somehow I have in installed on my external HD (no problem formatting it, there's nothing on it currently), and a well-meaning soul has counseled me to:

"Fix your Windows MBR and then boot a Live CD and (with the external connected), post:
sudo fdisk -lu"

Can anybody explain that in first grader terms?

---

### Post by benerivo on 2008-06-29
"fixmbr" is covered [here]("http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm") (you will need the Windows XP cd).

"boot live cd" means just put your ubuntu cd in the drive and reboot.

"with external connected" means have your external drive plugged in before you reboot.

"post:sudo fdisk -lu" means open the terminal and type this command to see what it returns.

---

### Post by bhadotia on 2008-06-29
It mean that if if you have GRUB (the linux boot loader (a program that boots your OS (windows or linux))in your MBR (a place on hardisk where it is installed (usually first 512 bytes or MB - can't remmember:))and which makes it the main boot loader) then you need to make the windows boot loader your MBR (I know the language is not completely correct- but someone here will anyway correct it).
I think you can do that with the windows installation CD in recovery mode or rescue mode (or whatever it is called). 
Then with the external hard disk connected Boot your ubuntu live CD and log into the Live environment . Then open a terminal and type that command and post the output here(or wherever the.person asked you to post it).

---

### Post by dfreer on 2008-06-29
> **MWK-ATL said:**
> Can anybody explain that in first grader terms?

"Honey, please don't touch daddy's computer, you know that makes him angry..."

:D sorry couldn't resist.

Anyways, just a little note:
You need windows to be running when you put the ubuntu CD in if you want to install using Wubi.
If you reboot the machine and boot the ubuntu CD that way, you can only install to the hard drive itself.

A link to the original thread/post where you got this advice might also be helpful for us, if you have further issues.

---

### Post by MWK-ATL on 2008-06-29
Thanks, that makes a little more sense.  So here's another question:  can I accomplish the same task without the Windows XP cd?  My windows XP was an OEM install so I don't have the cd.  And is that the only thing I have to do to completely uninstall Ubuntu?  I just want to make sure so I can put it back on the computer!!!

---

### Post by benerivo on 2008-06-30
The only part of ubuntu that is on your main hard drive at the moment is the bootloader (grub), and you just need to write over this with the windows bootloader (mbr). I don't think you can do this with a custom OEM cd. You would be fine if you could borrow a normal XP cd, and then then run fixmbr. Otherwise, i think you are stuck with grub unless you backup your personal documents from windows and then do a full installation using the OEM cd -- which would wipe over everything you currently have on the drive.

---

### Post by MWK-ATL on 2008-06-30
Last night I used Super Grub Disk to accomplish a fixmbr command without the OEM cd (I think), then did a full system recovery.  The computer booted without the Ubuntu options in the boot menu, and then I monkeyed around and finally figured out how to delete the current partitions and repartition the external HD I used to store ubuntu.  Success!  Didn't need the Windows XP cd (though I did order a recovery set from HP, just in case), and everything seems to be working fine.  There's no unusual or uanaccounted-for storage issue in either the computer's hard drive or the external, and I don't need the external turned on to boot anymore, so I think I cured that problem.  After all this I installed Wubi to give Ubuntu another chance, but I'm having the same problems as before:  can't get past the logon screen unless I do a failsafe GNOME session (the screen just keeps recycling to logon), and when I do get into ubuntu using the failsafe GNOME (anyone want to explain exactly what that is?), I can't connect to the internet; the computer sees the network, but won't process the WEP Key.  Any ideas, or should I just switch to Fedora and give that a try?

---

### Post by novatotal on 2008-06-30
wubi allways gives trouble, if you are really intent on installing ubuntu, you'll be better off doing a normal install(rezise, partition and install); now before installing it on a second drive, I'll sugest a thorough research of how it should be done, other wise you'll end up having a diferent set of problems.

---

### Post by MWK-ATL on 2008-06-30
I agree.  I think I've done it the hard way, but now I believe I've learned a little.  I can still use Wubi to install into a partitioned drive, so if I put the .iso there and run Wubi.exe from that drive, it should install there, correct?  Or your advice is to forgo Wubi completely?

---

### Post by meindian523 on 2008-06-30
Do you have a ATi Radeon XPress card?The cycling between login and desktop is a known bug on that.


[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660)

---

### Post by alzie on 2008-07-01
I had a positive experience with wubi.  Now I dual boot.

I'd recommend reading through the wubi guide:
[https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3](https://wiki.ubuntu.com/WubiGuide#head-67ff1616a5875935bb05d22e615fd9eb703d37a3)

If you have any wubi issues or questions there are the wubi forums:
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

The only other thing is you can do the installation from the live cd (8.04) or do the download route using [http://wubi-installer.org/](http://wubi-installer.org/)

Good Luck

---

