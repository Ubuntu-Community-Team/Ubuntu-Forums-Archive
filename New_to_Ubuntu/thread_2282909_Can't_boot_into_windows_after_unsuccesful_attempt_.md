---
title: "Can't boot into windows after unsuccesful attempt to install Ubuntu 15.04."
date: 2015-06-17
forum: New to Ubuntu
---

### Post by deadpxl2 on 2015-06-17
Hello. 
First things first I'd like to say hello to ubuntuforums. 
So, to proceed to the merits of the case. Today I wanted to play around with Ubuntu. (My first one was 10.04 afair, so i have a little bit of basic knowledge)
I've downloaded latest x64 15.04 iso, made a bootable usb stick. I had 3 partitions on my 1TB WD10EZEX HDD. First one was for system files (Win7 x64) and some apps. Second partition was storage one, had there around 75GB of data (total size was around 300GBs) and the 3rd one was for games and rest of apps.

I've decided to move all the files from storage to games/apps partition and dedicate 300GB to Ubuntu. I've copied everything from there and formatted as NTFS. Then I proceed to the bios to change my boot list (so the usb stick would boot first). It's UEFI bios (it was selected "LEGACY+UEFI") so after reboot it showed that it's booting in insecure mode (or something like that). And here comes the trouble.
 
At the beginning after installator loaded up, i've started slowly configuring everything i needed (language, etc). I've checked "Download updates while installing" and "3rd party software". After i clicked "Continue" installator have been "looking for something" around 2-3 minutes till it went to the next page. So, here is the problem. I don't really remember what I checked the first time installator asked me but, everthing that i remember is checking "Encrypt the new ubuntu" and "Use LVM with new Ubuntu installation". I've entered my key and left unchecked "Overwrite empty disk space". Then when it came to the picking up installation location i couldn't find my 300GB NTFS partition which i had prepared ealier. There was just a one partition with 930GB or so of space. 

So I decided to close the installer, reboot my pc and boot into windows but just got big nope. There was just a blinking underscore. I left it for 5-10 minutes in hope that something will move, but nope. When I googled my symptoms I've read somewhere that the LVM and LUKS messed something.

So here comes my question. If the problem is caused of the two listed above, is there any chance to recover my files without formatting everything? I've access to 2nd PC with Ubuntu on it (but in 32bits version), sadly I have it in my job so it's not available 24/7.

I've digged every site/forum/etc saying something about this problem but didn't found solution so I came here. 
I'm out of clues right now.

I'm running now on LiveCD so at least i have internet access. And yes, my HDD is deteced by BIOS and in "Disks" application.
[Disks app screenshot 1]("http://imgur.com/u9L8ita")
[Disks app screenshot 2 ]("http://imgur.com/W16WVy8")
[Disks app screenshot 3]("http://imgur.com/YL21UIi")

Is there anyone who can at least tell me where to look for potential problem?
Thanks in advance, have a nice day/night.

---

### Post by oldfred on 2015-06-17
LVM or LVM with encryption is a full drive install, or you told it to erase your entire hard drive.

You may be able to find old partition(s) with testdisk and its deeper search may show files. It depends on what was overwritten. Ubuntu is not large, and writes files to entire drive, so some of you data is overwritten but much may not be.

If testdisk does not work there is photorec. I have used it, but it does not find full filename, just extension or file type. I had saved some files many times, and it recovered all the old ones as well. I had to spend days comparing last backup (now more frequent) to each of the recovered files which I had to sort and look at to know what they were. Or lots of effort that good backups would save.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Some Windows users have posted that Windows recovery programs may be better.

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by yancek on 2015-06-17
In addition to the above suggestions, you seem to say that you created a 300GB partition for Ubuntu "formatted ntfs".  That won't work, you need a Linux filesystem which you would do during the install.

---

### Post by cooleryawner on 2015-06-17
Can you run boot repair from the live disk/usb

---

### Post by deadpxl2 on 2015-06-18
> **yancek said:**
> In addition to the above suggestions, you seem to say that you created a 300GB partition for Ubuntu "formatted ntfs".  That won't work, you need a Linux filesystem which you would do during the install.

Yeah i knew that. The thing is that this partition wasn't even listed there.

> **cooleryawner said:**
> Can you run boot repair from the live disk/usb

What exactly?

---

### Post by cariboo on 2015-06-18
> **deadpxl2 said:**
> Yeah i knew that. The thing is that this partition wasn't even listed there.



What exactly?

Have a look at the boot repait wiki page:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

