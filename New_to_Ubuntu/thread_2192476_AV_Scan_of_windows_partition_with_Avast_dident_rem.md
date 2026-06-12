---
title: "A/V Scan of windows partition with Avast dident remove found virus'"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by James_V._Conace on 2013-12-08
Hi everyone.
Let me begin by saying that I am a Linux NOOB.

I am having a problem with removing virus' from a windows partition with Avast in Ubuntu 12.04.
I am trying to remove the Antivirus Security Pro Virus + a few more.

Heres what I did:

I burned a Ubuntu Live CD-R successfully,
I booted the computer in question sucessfully, with internet access.
I installed Avast, entered the key and changed the size of the kernel,shmmax to 128000000 in the terminal and updated the definitions.
I ran Avast on the windows partition and it found quite a few virus'. For the first few I clicked the move to chest button, then i chose the move all button so i dident have to watch it.
The settings I used were a thorough scan and scan compressed files.

After the scan finished I got a log file that listed what it found (many virus'). It said all of the virus' it found were moved to the chest, but when i rebooted, the virus' were still there.

I was wondering why the virus' were still there even though the log file said they were moved to the chest, and where is the chest anyway?
Is it possible that since the Live "CD" doesent have a persistance file that the chest doesent really exist?
The scan took about 3 hours to complete and total files scaned was about 800,000. 

Could someone please tell me what I did wrong, so i can save face with my friend.

Any help will be appreciated!

Thanks

---

### Post by coffeecat on 2013-12-08
There are Linux based live CD ISOs offered free by many of the AV vendors, and if I was wanting to scan a Windows system for viruses from outside of Windows I would choose them over using Ubuntu with Avast. But I wouldn't choose them either for the insidious virus you mention. Probably better is to google for a specific Windows infection in order to find comprehensive instructions online for purging that infection from within Windows, often with online scans of your Windows system. Googling Antivirus Security Pro Virus gave me this as a first hit:

[http://malwaretips.com/blogs/antivirus-security-pro-removal/](http://malwaretips.com/blogs/antivirus-security-pro-removal/)

I have no experience of that one, but malwaretips has a good WOT rating and it looks to be trustworthy, although in the malware field, who knows when you are being scammed.

Notwithstanding all that, you say Avast found many viruses. If that was my Windows system, I'd simply do a fresh re-install. With so many infections, however many scans you do with however many AVs, there'd always be the concern that there was a missed piece of malware somewhere.

---

### Post by James_V._Conace on 2013-12-08
Hi coffeecat

Thank you for your response, I will try the instructions in the link.

I probably should tell my friend to do a new install, but he has sensitive files on the PC and no (clean) backup. I thought about running a backup to an external drive and then disconnecting it, and then re-installing a fresh copy of the OS, and install an AV program and then scan the external drive for virus' from the clean install and restore the files that he needs to the new install. But I think it will be a better option to remove as many virus' as I can find before backing up the system.

I also have copies of UBCD(Ultimate Boot CD) and Hirens Boot CD, but I'm not real proficient with those disks, yet.
I also tried to create a rescue disk from Avast but the program just sits there for hours and does nothing. I read somewhere that a rescue disk has to be created on a FAT filesystem, but how do I format a CD with a filesystem before creating the rescue disk.

I am going to try to create one on a flash drive with a FAT filesystem, anyway...
Thanks again for your help and I will get back to you soon to let you know how the removal went.

Jim

---

### Post by James_V._Conace on 2013-12-09
Hi coffecat

I tried the instructions in the link you suggested and it worked GREAT! It removed over 100 objects and the PC booted perfectly into Windows

Thanks for your help
Jim

---

### Post by bashiergui on 2013-12-10
> **James_V._Conace said:**
> Hi coffecat

I tried the instructions in the link you suggested and it worked GREAT! It removed over 100 objects and the PC booted perfectly into Windows
WOW. 100 objects. I would echo Coffecat and say I would also back up the data and then reinstall.

---

### Post by acase.hcom on 2013-12-11
>  WOW. 100 objects. I would echo Coffecat and say I would also back up the data and then reinstall.                 

agreed

---

### Post by DuckHook on 2013-12-11
...perhaps this tells your friend something important about the difference beween Windows and Linux...

---

