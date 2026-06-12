---
title: "Ubuntu/Windows boot up choice?"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by mlplatt on 2012-05-14
When I turn on my computer the first screen that appears is an Ubuntu one which lists a Windows Vista option five lines down. 

If I want to start Windows I have to hastily scroll down to it and click on the appropriate entry whereupon the screen changes to the impersonal start up screen giving me in large letters a straight choice between Windows and Ubuntu.

The first screen seems an irrelevance and ideally I would like to do away with it and go to a straight simple choice. Windows or Ubuntu.

If I can't do away with it I would like it to appear after I had decided to use Ubuntu instead of pre-empting the decision. 

Is this possible and, if it is, how can I do it?

I am a complete idiot in these matters and a beginner as far as Ubuntu is concerned. I only managed to connect to the Internet thanks to the inspired guidance of members here. 

Malcolm

---

### Post by wilee-nilee on 2012-05-14
How did you install the ubuntu, that is a rather strange event?

---

### Post by Mark Phelps on 2012-05-14
The initial screen that lists Windows part way down is a GRUB menu -- which is only created if you install GRUB, either manually, or as part of installing Ubuntu to its own partition.

The second screen is a Windows Boot Loader screen -- which is only modified if you install Ubuntu using Wubi.  And, in that case, you do NOT install GRUB.

So, if you installed Ubuntu twice (once using Wubi, a second time from CD/USB), or if you (after installing via Wubi), installed/reinstalled GRUB, you would have this situation.

To show us what you have, please open a terminal in Ubuntu and enter the following "sudo fdisk -lu" (lowercase L, not a one).  That will list out your partitions.

---

### Post by mlplatt on 2012-05-14
Hi, Thanks for the help. 

I am afraid i tried to install Ububtu several times from downloads unsuccessfully until I finally got a Linux shop disk.

So it is all probably a dogs breakfast. 

mlplatt@mlplatt-Inspiron-530s:~$ sudo fdisk -lu
[sudo] password for mlplatt: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112640    21084159    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21084160   691147929   335031885    7  HPFS/NTFS/exFAT
/dev/sda4       691148798   976771071   142811137    5  Extended
/dev/sda5       691148800   972601343   140726272   83  Linux
/dev/sda6       972603392   976771071     2083840   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   397769752   198884845    c  W95 FAT32 (LBA)
/dev/sdb2       397770750   488396799    45313025    5  Extended
/dev/sdb5       397770752   484225023    43227136   83  Linux
/dev/sdb6       484227072   488396799     2084864   82  Linux swap / Solaris
mlplatt@mlplatt-Inspiron-530s:~$

---

### Post by Mark Phelps on 2012-05-14
I don't know what constitutes "a dog's breakfast", but if you doubly-installed, both from inside Windows and outside, you will have a real mess to deal with.

My suggestion is to remove the version you installed from inside Windows.  You do that by booting into Windows and removing Ubuntu just like you would any other application.

When you are finished and reboot, you should still see the GRUB menu and be able to access both Windows and Ubuntu.

---

### Post by mlplatt on 2012-05-15
I am afraid I may be left with the dog's breakfast as Ubuntu in Windows has successfully resisted all my attempts to uninstall it.  

I have tried using both the Windows uninstall and also a couple of other programmes but without success 

So it looks like I may be stuck with it! It is after all not life threatening but just an irritation. 

Malcolm

---

### Post by oldfred on 2012-05-15
I think there are instructions to manually uninstall:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

The main issue is that you still have it in your Windows boot menu. If XP you can use an editor to edit boot.ini. If Vista/7 you have to use BCDedit to remove the wubi entry.

---

### Post by mlplatt on 2012-05-17
Hi Oldfred.

I have tried following the instructions in Wubi guide, but without success. I couldn't get the EasyBCD file to download and when i used the built in *bcdedit* was rather stymied because i don't know what the [GUID] is. I just don't know what I am looking for. 

There are three main headings - Windows Boot Manager, Windows Boot Loader and thirdly Real -mode Boot Sector in  the last of which Ubuntu has a single line mention. 

Nowhere does GUID get a mention. 

Malcolm

---

### Post by oldfred on 2012-05-17
I have never done it and have actually only used bdcEdit once. When I am not sure what I am doing, I just make a backup and jump in. So backup your BCD file and use bcdEdit to delete the entry with the Ubuntu reference. As bcbc has in link below the GUID is the long number shown.

bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
General BCD repairs:
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by mlplatt on 2012-05-19
This all sounds a little scary for someone of my extreme incompetence.  

I dont een know how to back up the BCB file.

What I have finally managed to do though is to download the EasyBCD programme. i shall play with that and see if I can understand enough to have the necessary confidence to go further. 

I shall let you know the result.

Incidentally I found that the download from  NeoSmart Technologies just doesn't work. However it can be easily downloaded through Softpedia.

---

### Post by mlplatt on 2012-05-19
OK I managed it after a fashion by using the EasyBCD programme. It was rather hit or miss. Fortunately I didmanage to back up  the BCB files with it and after some trial and error and treading of instructions managed some success.

Now the Windows Boot Loader screen does come up first. Subsequently the Grub Menu does come up as well but by then the choice has been made so that is not a problem

One thing perhaps worth mentioning is that on the Windows Boot Loader screen i couldn't get the Ubuntu option to function but managed finally with a NeoSmart Linux selection. All doubtless resulting from my somewhat haphazard approach. 

I feel  it could be cleaner but at least it works!

Thanks

---

### Post by kevin mcavinchey on 2012-05-19
I have the same startup screens as you ie two seemingly similar requests for a choice of op system. My attempt to reinstall a hangup wjen choosing ubuntu also hangs after delete and partial reinstall. the op system is a mess and wont let me enter ubuntu or reinstall . I tried a delete from inside windows but of no benefit im in a loop cant open ubuntu cant reinstall. Ubuntu had worked in my dual boot system for some weeks prior to hang up. i got my ubuntu from pc world with manual ver 10.04.1 wonderful product !
cheers kevin

---

### Post by mlplatt on 2012-05-19
Kevin I can only suggest that you try the EasyBCD programme downloaded from Softpedia. 

Mind you advice from me is a classical example of the blind offering to lead.

Oldfred's list of places to seek advice is excellent and I am sure that i could do a neater job if I had the confidence to follow all the instructions but I really am not intelligent enough.  I am afraid that my attempts usually make things worse and I have a horror of ending up with no internet at all. 

Regards,

Malcolm

---

### Post by kevin mcavinchey on 2012-05-19
the blind leading the blind deaf and dumb can be of value ill have a go cheers kevin

---

### Post by Mark Phelps on 2012-05-19
Don't get EasyBCD from any source other than the NeoSmart Technology forums.  They have the latest beta versions.  You should try one of those, not go elsewhere for the downloads.

Also, they have help forums.  If you're having problems with EasyBCD, the best place to ask is in their own forums, not here.

---

### Post by mlplatt on 2012-05-20
Getting EasyBCD from NeoSmart Technologies is easier said than done. I tried to download it from then half a dozen times without success. I donated thinking that they were reluctant to provide it free but still no success. 

I tried to join the joined the forum but the authorising URLs they sent me by email didn't work. There was an instruction saying if they don't work contact us at ... just an unfinished sentence.

I tried contacting them direct by email telling them the above and asking for help. 

I never received a reply. 

So my advice is that although the Softpedia version may be second best at least you can get it. And the NeoSmart forum may be marvellous ...if you can access it. As it is I had no problem with the EasyBCD version  I downloaded.

---

