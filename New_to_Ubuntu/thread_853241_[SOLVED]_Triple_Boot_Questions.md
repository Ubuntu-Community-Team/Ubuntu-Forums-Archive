---
title: "[SOLVED] Triple Boot Questions"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by TheGreatExperiment on 2008-07-08
Okay so I've done some searching on the web and these forums, but I either I'm a little slow and don't recognize what I need or I can't find exactly what I'm looking for.

I just installed ubuntu alongside what had been a successful dual boot of xp/vista.  I have two HDDs: Vista is on one, and I partitioned the XP one for the install of linux.  I have been using easybcd to control how my computer booted, so I created an entry for ubuntu.  However, when I choose the ubuntu option, it spits out a message saying:

"cannot load from harddisk
insert systemdisk and press any key"

I do what it says and then it loads the grub screen.  From there I can successfully load any of the three OSes.  I have three questions:

1) How do I fix the loading issue?

2) How can I change things so that grub is my only boot manager?  Ideally this would include the removal of the whole easybcd setup.

3) In the grub menu it shows two versions of ubuntu (it was only one at first, but then I installed something like 220 updates and all of a sudden I have two entries, one with a distinctly newer version/build no.), so is it necessary to have both of them, or can I remove the "older" entries?  I like having things nice and neat...

Any help is greatly appreciated!

---

### Post by Inxsible on 2008-07-08
You probably did not install grub in the MBR ..which is why it cannot find it. Use the Live CD to install grub again and this time install it to MBR. That should give you a working grub.

As for the 2 entries for Ubuntu, its because of the updates. If you get a new kernel it automatically comes in the Grub menu. Its a good idea to keep atleast one older "working kernel around, in case the new kernel doesnt work with your hardware for some odd reason.

If you get too many of these, however, you can remove them from synaptic by searching for the appropriate kernel number. The other thing you could do is simply comment out the kernels that you don't want displayed in the /boot/grub/menu.lst file. I think its a waste of space to keep more than 2 working kernels, so I simply uninstall them.

---

### Post by bumanie on 2008-07-08
Answers as best I can.
1) Not sure as 2 & 3 probably cover.

2 & 3) To get things working all with grub will take a bit of work. I 'm surprised esybcd has not handled 3 OSes, it is meant to do that well - may be all three OSes need to be installed prior to easybcd, I don't know. Any way, in general terms you can get grub to manage all three, but you must do a bit of reading first. Read [this site]("http://users.bigpond.net.au/hermanzone/p15.htm") There's heaps of info on grub. I would see a dedicated grub partition as a potential answer to your predicament. Herman goes through that quite thoroughly.

The other recognised way I know of (but never tried) is to have vista installed first, then install xp which wrecks vista's bootloader. Fix vista's bootloader - you then can choose to boot vista or the 'older version of windows'. Then install ubuntu and grub should give the choice of ubuntu or vista - choose vista, you get a choice as above. The other way is to do install in this order and then use easybcd bootloader. 

Sorry this is a bit of a rush as I doubt you want to reinstall xp and ubuntu.

---

### Post by TheGreatExperiment on 2008-07-08
Thanks for the replies

Inxsible - I tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351").  The find command returned (hd0,4), and I entered "setup (hd0)" as per the instructions on the page.  Upon rebooting I got the same "choose between vista, xp, or ubuntu" from easybcd, and choosing ubuntu gave the same "cannot load from harddisk" message.  Should I re-try using (hd0,4) instead?

bumanie - I did do the vista -> xp (repair vista boot) -> ubuntu install sequence.  It seems to me that I'm just missing some minor detail within easybcd (I could be very wrong given how new I am to linux) that is directing it to the wrong place.  However I checked where Grub is (c:\nst\nst_grub.mbr) and it all seems to be correct, at least as far as to where easybcd points.  It just seems to me that whatever has been created by easybcd takes precedence over Grub.

---

### Post by Inxsible on 2008-07-08
> **TheGreatExperiment said:**
> Thanks for the replies

Inxsible - I tried the instructions [here]("http://ubuntuforums.org/showthread.php?t=224351").  The find command returned (hd0,4), and I entered "setup (hd0)" as per the instructions on the page.  Upon rebooting I got the same "choose between vista, xp, or ubuntu" from easybcd, and choosing ubuntu gave the same "cannot load from harddisk" message.  Should I re-try using (hd0,4) instead?
The grub always has a format of (hdX,?)

It will depend on where your Ubuntu is installed -- meaning the drive and the partition number.

If Ubuntu is installed in the second drive, it will most likely be "hd1". You will have to determine the partition number though.

Log into ubuntu and then issue this command in a terminal.```
sudo fdisk -l
``` l is lowercase L. That will help us determining what entry you should have in the grub.

---

### Post by bumanie on 2008-07-08
> bumanie - I did do the vista -> xp (repair vista boot) -> ubuntu install sequence. It seems to me that I'm just missing some minor detail within easybcd (I could be very wrong given how new I am to linux) that is directing it to the wrong place. However I checked where Grub is (c:\nst\nst_grub.mbr) and it all seems to be correct, at least as far as to where easybcd points. It just seems to me that whatever has been created by easybcd takes precedence over Grub. Yeah, as far as I know that is the case (ie easybcd over-riding grub). Neosmart do have a forum of some kind, may be you could find out there what to do. I would still look at Herman's description and how to use a grub partition. I am unsure how to get rid of easybcd bootloader - I guess there must be some sort of uninstaller. Sorry I'm no expert on this, but have read about it a few times. The one I read about vista, followed by xp and lastly ubutnu sounded the easiest, but they didn't have easybcd already installed. There are tutorials on the internet re triple booting, but do look at Herman's site, it's tells nearly everything there is to know about grub and booting. Whilst esybcd is in the picture, I don't think grub will work properly. As long as you have xp booting from vista's bootloader, once grub is installed to vista's mbr, everything should work. Up to you whether you uninstall easybcd or not. But as said, as long as vista boots and also boots xp, grub should then work once installed to vista's mbr - at least in theory it will.

---

### Post by bodhi.zazen on 2008-07-08
FYI : Grub will triple boot your OS.

If I understand you correctly, gru is working from the menu you get when booting ubuntu ?

All you need do then is install grub. 

You need to understand how grub (and linux) refer to partitions.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

You then need to understand how to install grub.

Boot a live CD

sudo grub

at the grub prompt :

root (hd1,x)
setup (hd0)

where "(hd1,x)" == your Ubuntu partition.

If you have problems with booting windows, you need to understand how to map and hide windows.

See this link : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Specifically these sections :

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_and_MultiWindows_)

---

### Post by TheGreatExperiment on 2008-07-08
Thanks again for the responses.  This is definitely the nicest/most helpful forum I've been on recently...

here is the output from the fdisk:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0a7e0a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19875   159645906    7  HPFS/NTFS
/dev/sda2           19876       30401    84550095    5  Extended
/dev/sda5           19876       30036    81618201   83  Linux
/dev/sda6           30037       30401     2931831   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
53 heads, 36 sectors/track, 327642 cylinders
Units = cylinders of 1908 * 512 = 976896 bytes
Disk identifier: 0xf1d72398

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      327642   312568832    7  HPFS/NTFS

```

Using the terminal I entered:

```
sudo grub

find /boot/grub/stage1
```

it returned (hd0,4)

so I did:

```
root (hd0,4)
setup (hd0,4)
quit
```

I had installed ubuntu according to NeoSmart's [guide]("http://neosmart.net/wiki/display/ebcd/ubuntu"), and I still get the "cannot load from harddisk"

One more thing of note: Vista thinks it has the c: drive when I'm in vista, and xp thinks its disk is the c: drive when I'm running xp, and ubuntu shares xp's "point of view".  Could this cause Grub to be confused?  My understanding is that easybcd works off of the Vista settings...

I would like to reiterate that both xp and vista boot just fine from the boot menu, but when I choose linux I get the "cannot load from harddisk/ insert systemdisk and press any key" message, and from there I can get into ubuntu just fine.

---

### Post by bumanie on 2008-07-09
Hi there, not sure whether you will see this, but grub should be like this in the menu.lst
What you have ; 
> root (hd0,4)
setup (hd0,4)
quit
What it should be:
> root (hd0,4)
setup (hd0)
quit
Setup (hd0) should put a pointer in vista's mbr, where both vista and xp's bootlaoders are, grub will thus look there at startup to give the appropriate choices. I,m not sure whether easybcd will confuse things or not. I really have no idea how it works, but assume if grub is set correctly, hopefully easybcd will do things correctly.

---

### Post by TheGreatExperiment on 2008-07-09
I just thought of this and I can't try it out because I'm at work, but should I put grub in (hd1) because that's where Vista's mbr is (judging from the fdisk output) and that's where things boot from?

I'll try it out myself this evening and report back if nobody tells me not to...

---

### Post by bodhi.zazen on 2008-07-09
> **TheGreatExperiment said:**
> I just thought of this and I can't try it out because I'm at work, but should I put grub in (hd1) because that's where Vista's mbr is (judging from the fdisk output) and that's where things boot from?

I'll try it out myself this evening and report back if nobody tells me not to...

Well, the "problem" is drives can be mapped.

So you will need to proceed by trial and error.

If setup (hd0) fails, go with setup (hd1)

Once GRUB is installed into the MRB, if it does not boot, we may need to then edit /boot/grub/menu.lst :twisted:

---

### Post by TheGreatExperiment on 2008-07-09
Solved!

It was almost embarrassingly simple - I noticed in the fdisk and in my BIOS that my Vista drive was on SATA channel 3 and XP on 2 (hence XP was hd0 and vista was hd1), so I just opened up my case, switched the cables, wiped my ubuntu partition clean, did a fresh install, and voila - triple booting perfectly!  I'm willing to bet that installing grub to hd1 without switching the cables would have worked too.

Thanks for the help/advice!  I can already see that this is an awesome community!

---

