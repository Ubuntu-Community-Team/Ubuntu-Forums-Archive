---
title: "USB start up disk not working"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2012-05-10
Hi guys,

It's been a while since I last posted, but I always got help in the past, so I'm sure you will help me figure this out also :)
I'm running Ubuntu 10.10 and it seems that it's no longer supported, so I was thinking to give the new and shiny 12.04 a try, especially because is an LTS. So I downloaded the image, created an USB start up disk with the "Startup Disk Creator", but I am not able to boot from it. And yes, I know how to change boot order priority in BIOS and I can see the stick there. If I click on the usb stick now, I get the message:
> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
If I run that command I get:
> dmesg | tail
[  106.710177]  sdb: sdb1
[  106.712923] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  106.712938] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  219.756541] ISO 9660 Extensions: Microsoft Joliet Level 3
[  219.756594] ISO 9660 Extensions: RRIP_1991A
[  398.621404] isofs_fill_super: bread failed, dev=loop0, iso_blknum=16, block=32
[  417.258418] NVRM: Xid (0004:00): 13, 0003 beef5f01 0000009f 00000300 fffe0000 00000002
[  421.267899] NVRM: Xid (0004:00): 36,  L0 -> L0
[  424.003556] isofs_fill_super: bread failed, dev=loop0, iso_blknum=16, block=32
[  701.343154] isofs_fill_super: bread failed, dev=loop0, iso_blknum=16, block=32
I've tried with 2 USB stick, so I don't think that the stick is the problem.
Any help would be appreciate!

Cheers!

---

### Post by Enigmapond on 2012-05-10
It may be bad data downloaded. I've never had much luck with startup disk creator and usually use Unetbootin as this works very well. I would create a stick using that and see if that helps.

---

### Post by Troll_the_Great on 2012-05-10
> **Enigmapond said:**
> It may be bad data downloaded. I've never had much luck with startup disk creator and usually use Unetbootin as this works very well. I would create a stick using that and see if that helps.

Can you elaborate a bit on that please?

Cheers, Dan

---

### Post by kdane4 on 2012-05-10
Hello,

did you check if the md5 checksum of your ISO matched the one on the download page? A mismatch means its a corrupted download.

I also suggest downloading via torrent.

---

### Post by oklokl on 2012-05-10
In my case, try this test
usb problem 

sudo mount -l /dev/sdc1
or
udisks --unmount /dev/sdc1

sudo badblocks -vw /dev/sdc1
It takes a long time.


remove usb clean
sudo parted -l 
sudo dd if=/dev/zero of=/dev/sdc bs=512 count=1
sudo parted /dev/sdc
msdos
mkpart
0
-1
q


sudo mkfs.vfat /dev/sdc1


# Ubuntu.Iso
# Hash Check

md5sum ~/Downloads/*.iso > ~/Downloads/iso_hash.txt
cat ~/Downloads/iso_hash.txt

# sha1sum Ubuntu.Iso > test.txt

---

### Post by Troll_the_Great on 2012-05-10
> **kdane4 said:**
> Hello,

did you check if the md5 checksum of your ISO matched the one on the download page? A mismatch means its a corrupted download.

I also suggest downloading via torrent.

I don't know how to do that unfortunately. Can you direct me step by step?
Thanks.

---

### Post by jockyburns on 2012-05-10
> **Troll_the_Great said:**
> Can you elaborate a bit on that please?

Cheers, Dan

I think he means, download and install unetbootin

link here  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


Then use that program to create your bootable usb. 
I tried startup disk creator to make a bootable usb and it failed, so I used unetbootin to create the bootable usb from the ISO I'd already downloaded and it worked first time. 
Good Luck

---

### Post by kdane4 on 2012-05-10
> **Troll_the_Great said:**
> I don't know how to do that unfortunately. Can you direct me step by step?
Thanks.

hello,

you can follow this wiki

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Troll_the_Great on 2012-05-10
OK, so I manage to boot from the stick, but only if I set in BIOS as primary hard drive the USB stick. I created a stick using the Startup Disk Creator and one using Unetbootin, and both work but only with the above option... Is this normal? If I set as primary boot device the USB stick, why do I have also to set it as primary hard drive also? :confused:
    Anyway, I'm glad it works. And now, for another question:
Is 12.04 a good distribution? I know it's fairly new, but I just want your user opinion. Is there a way to upgrade from 10.10 to 12.04 directly, with the live USB stick?

Cheers, Dan

---

### Post by steve7777777 on 2012-05-10
> **Troll_the_Great said:**
> ...Anyway, I'm glad it works. And now, for another question:
Is 12.04 a good distribution? I know it's fairly new, but I just want your user opinion...

Cheers, Dan

Check out the installation & Upgrades sub forum, [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
there are problems with 12.04 which is to be expected and difficult to extrapolate from that how widespread the problems are. IMO better to wait a bit longer. The important thing is to use 12.04 and see how you like Unity. I'm running 12.04 in virtual machine - the free Virtual Box, and 12.04 seems to run fine on my system. Unity is taking some time to get used to. Good luck!

---

### Post by Troll_the_Great on 2012-05-10
> **steve7777777 said:**
> Check out the installation & Upgrades sub forum, [http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)
there are problems with 12.04 which is to be expected and difficult to extrapolate from that how widespread the problems are. IMO better to wait a bit longer. The important thing is to use 12.04 and see how you like Unity. I'm running 12.04 in virtual machine - the free Virtual Box, and 12.04 seems to run fine on my system. Unity is taking some time to get used to. Good luck!

Hmm... So the new release comes only with unity? I can't choose the normal gnome desktop, or at least install it afterwards?

Cheers, Dan

---

### Post by Troll_the_Great on 2012-05-11
Bump!

---

### Post by Troll_the_Great on 2012-05-12
Anyone?

---

### Post by Prescilla on 2012-05-12
You can still use gnome classic.
On the login screen, before you click login, select Gnome Classic as your desktop.

---

### Post by Troll_the_Great on 2012-05-12
> **Prescilla said:**
> You can still use gnome classic.
On the login screen, before you click login, select Gnome Classic as your desktop.

That's a relief. I've tried Unity with a Live CD a couple of times and I don't say it's bad, but I got used to Gnome so much that it's hard to change.
Thanks for your answers, Dan

---

### Post by steve7777777 on 2012-05-12
> **Prescilla said:**
> You can still use gnome classic.
On the login screen, before you click login, select Gnome Classic as your desktop.

I'm running 12.04 in Virtualbox and don't see that option before the login screen. ???

---

### Post by Troll_the_Great on 2012-05-13
> **steve7777777 said:**
> I'm running 12.04 in Virtualbox and don't see that option before the login screen. ???

I'm a bit confused now.... :confused:

---

### Post by Daveth on 2012-05-13
you have gnome, gnome classic, ubuntu, & ubuntu 2d to choose from, and you can always add gnome shell. I have done the upgrade path you are following- Unit is OK, but I may give gnome shell a go. If the HUD were more intelligent I might stay with it longer.

---

### Post by cryptotheslow on 2012-05-13
On a new install of Ubuntu 12.04 only Ubuntu (Unity) and Ubuntu 2D (Unity 2D) are available in the list at login.

However it is a simple affair to install the Gnome Classic (or Gnome fallback) desktop which is basically a Gnome 3 based DE that looks and feels almost identical to the Gnome 2 DE in Ubuntu 10.04 etc.

You just need:
```

sudo apt-get install gnome-session-fallback

```

wait for it to finish installing, logout and the new option will be available on the login screen.

---

### Post by Scott Baker on 2012-05-15
To get back on track regarding the original reason for this post, I too am having issues with a non-bootable usb stick. I've tried start-up disk creator and UNetbootin, with the exact same results. Stick is good, with NO prior problems, but since my 12.04 install, it's no go on the stick. Strangely, I was able to get a bootable disk (DVD) using start-up disk creator and the alternate download DVD provided by the Ubuntu website (live CD wouldn't work, kept showing burn errors through Brasero, but ALT-install DVD burned fine). It's VERY important that I get a usable USB stick, as this is used in my business for diagnostics. Any ideas folks ?? ](*,)

---

