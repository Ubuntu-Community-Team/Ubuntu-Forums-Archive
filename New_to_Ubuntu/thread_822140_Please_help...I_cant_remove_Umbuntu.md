---
title: "Please help...I cant remove Umbuntu"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Zanara on 2008-06-07
I have spent the entire day trying to remove Ubuntu from my pc but cant. I am ready to toss the HD and get new one.

I have 200 gig Asus Laptop HD...one partion...what ever Umbutu uses (it also made swap file partition)
I cant run XP, or Vista CD's ...get 'no Hard disk found'...recover is not an option...does not see any windows installs(there are none)
I ran abound 9 versions of FDISK /mbr
I ran same amount of MBR fixers
I tried some kind of format program (3 hours)
I tried re-install Umbuntu and at partion...change it to Fat32...it says something about root point not good (spent 2 hours on this one).
I searched Google for hours.
I just want my HD back...empty...and XP, Vista, or even DOS 1.0 to be able to see it.
I have no floppy drive
For the love of God...How do I get rid of Umbuntu....
I am begging.

---

### Post by tramir on 2008-06-07
I can't believe I'm doing this...

I guess what you want is to run the Windows Setup from the CD. During the setup process, there is an option where it asks which HD you want to install on, and you can choose there to format the disk. That should work.

Just in case, you can also try the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"), which allows you to do pretty much anything you want to with your HD (and, incidentally, is based on Linux).

Good Luck. And don't give up on Linux/Ubuntu just yet...

PS: Ubuntu usually plays well with Windows, especially when it's installed *after* Windows.

---

### Post by cariboo on 2008-06-07
You're going to need a genuine Winsdows XP CD. A restore disc isn't going to do you any good.

JIm

---

### Post by ZabiGG on 2008-06-07
Sorry to hear you want to uninstall :(

This links to an uninstall page... but you should read it carefully first. 

[http://www.users.bigpond.net.au/hermanzone/p18.htm#uninstall_top](http://www.users.bigpond.net.au/hermanzone/p18.htm#uninstall_top)

Ubuntu is a great OS and maybe you were just missing easy-to-use info? If so, please click on "Look here" in my signature below. There is a lot of easy to understand and clear information you might use.

You problem appears to simply relate to format. By default, your disk was probably formatted in the ext3 format, while Windows is only compatible with Fat 32 (older versions) and NTSF. 

The guide I linked includes tips to format part of your disk for a Windows partition, if you click on the link to the main guide on top).

Good luck to you,

Z.

---

### Post by Zanara on 2008-06-08
SuperGrub Fails. (I did the fix mbr...I made active...I deleted all things linux) GPART Fails (that one wont even load...tried all options including failsafe)
Please read this part closely..I DO have XP (and VISTA) CD...I HAVE tried Recovery Consol...it does NOT work...it says there is no hard drive (same as it says when I just click install). I have now tried countless 3rd party MBR programs...
To replace the drive will cost me over $200. Are there any paid consultants that can help? Can someone give an 800 number? This is rediculus...Something installs itslef and then absolutely will not go away? 
What can I do??? Please help...I must have this laptop working by tomorrow. 
DESPERATE






> **ZabiGG said:**
> Sorry to hear you want to uninstall :(

This links to an uninstall page... but you should read it carefully first. 

[http://www.users.bigpond.net.au/hermanzone/p18.htm#uninstall_top](http://www.users.bigpond.net.au/hermanzone/p18.htm#uninstall_top)

Ubuntu is a great OS and maybe you were just missing easy-to-use info? If so, please click on "Look here" in my signature below. There is a lot of easy to understand and clear information you might use.

You problem appears to simply relate to format. By default, your disk was probably formatted in the ext3 format, while Windows is only compatible with Fat 32 (older versions) and NTSF. 

The guide I linked includes tips to format part of your disk for a Windows partition, if you click on the link to the main guide on top).

Good luck to you,

Z.

---

### Post by lostlinuxkiwi on 2008-06-08
I doubt uninstalling ubuntu is gonna change anything. you should just be able to install xp or vista over the top of it. 

"When you boot up, go into the CMOS menu. You typically do this by holding down the delete key after you turn power on. Inside most CMOS menus, you'll find an autodetect function. This will reprogram the chipset to recognize your hard drive(s) and other devices. Ditto for SCSI adapters."

---

### Post by bumanie on 2008-06-08
The other thing you could try is using gparted to format your drives to nfts, assuming gparted can 'see' the drives.

---

