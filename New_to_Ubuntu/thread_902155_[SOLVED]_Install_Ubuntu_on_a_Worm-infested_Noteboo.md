---
title: "[SOLVED] Install Ubuntu on a Worm-infested Notebook"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by uilyam on 2008-08-27
I have three computers: old, 6 gigabyte drive, Windows 98; newer, 110 gigabyte drive, Windows XP Professional (year 2002); IBM Thinkpad, 55 gigabyte drive, Windows XP Professional (year 2003), bought used in America by a friend of a friend a couple months ago and brought to me here in Russia.

The problem: The Thinkpad had no active antivirus and was infested by a worm (it also had a couple of trojans that I got rid of). The worm is in almost 1000 exe files. With some difficulty I can get this Thinkpad up with the worm temporarily inactivated, but I can do almost nothing without it becoming active again. The Thinkpad came with no CDs, etc.

Yesterday at the office two colleagues gave glowing reports about their children's experiences with Ubuntu. So I downloaded the zip file on my flash.

Here is what I plan to do. I would appreciate general comments regarding whether I am on the right path or am overlooking something important. You can assume that I am computer semi-literate and reasonably intelligent. I will also be reading through the documentation and so on. 

1. Copy the zip file to a partition on my newer computer. (DONE)

2. Unzip the file there. (SOON)

3. Install as an optional operating system? Get it running enough to make a bootable CD with the necessary programs on it.

4. Boot the Thinkpad from the Ubuntu CD I made and format the drive.

5. Then install Ubuntu on the Thinkpad completely.

---

### Post by iaculallad on 2008-08-27
> **uilyam said:**
> I have three computers: old, 6 gigabyte drive, Windows 98; newer, 110 gigabyte drive, Windows XP Professional (year 2002); IBM Thinkpad, 55 gigabyte drive, Windows XP Professional (year 2003), bought used in America by a friend of a friend a couple months ago and brought to me here in Russia.

The problem: The Thinkpad had no active antivirus and was infested by a worm (it also had a couple of trojans that I got rid of). The worm is in almost 1000 exe files. With some difficulty I can get this Thinkpad up with the worm temporarily inactivated, but I can do almost nothing without it becoming active again. The Thinkpad came with no CDs, etc.

Yesterday at the office two colleagues gave glowing reports about their children's experiences with Ubuntu. So I downloaded the zip file on my flash.

Here is what I plan to do. I would appreciate general comments regarding whether I am on the right path or am overlooking something important. You can assume that I am computer semi-literate and reasonably intelligent. I will also be reading through the documentation and so on. 

1. Copy the zip file to a partition on my newer computer. (DONE)

2. Unzip the file there. (SOON)

3. Install as an optional operating system? Get it running enough to make a bootable CD with the necessary programs on it.

4. Boot the Thinkpad from the Ubuntu CD I made and format the drive.

5. Then install Ubuntu on the Thinkpad completely.

Before proceeding to the actual installation, check this [link]("https://help.ubuntu.com/community/Installation/SystemRequirements") first if your units meet the minimum requirement for Ubuntu installation.

---

### Post by shane19174 on 2008-08-27
I would suggest just booting up first from an Ubuntu live CD. Then you'll know if everything works. (It won't change anything on your system unless you tell it to.)

---

### Post by uilyam on 2008-08-27
iaculallad: Thanks, I checked the link, and the units I intend to use exceed the recommended requirements.

shane19174: I don't have a live Ubuntu CD. My thought in step 3 was to sort of make one for myself.

---

### Post by shane19174 on 2008-08-27
I'm a bit confused. What zip file did you download? Just download the standard .iso disc image that you can burn to CD under Windows, then boot with the CD. (Look here: [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) ).
Shane

---

### Post by k3lt01 on 2008-08-27
> **iaculallad said:**
> Before proceeding to the actual installation, check this [link]("https://help.ubuntu.com/community/Installation/SystemRequirements") first if your units meet the minimum requirement for Ubuntu installation.
This is excellent advice. I have Hardy running on an Acer whose specs are good for Windows XP but Hardy really needs more RAM than XP does (on my machine at least). While I am happy to deal with the slightly slower performance some people wont be.

My advice would be to go through the minimum requirements for each version of Ubuntu and see what version will suit each Laptop. My machine run best with 7.04 Feisty Fawn, excellent performance on 7.10 Gusty Gibbon, slightly slower but still very good on 8.04 Hardy Heron. I plan to upgrade my RAM to bring back the performance levels I want.

---

### Post by ugm6hr on 2008-08-27
What is your final plan?  It is easier for people to make suggestions if they know what you are trying to achieve.

I assume from what you have written that the 2 older computers have working OS (Microsoft) that you want to retain, and you want to completely wipe the 2003 Thinkpad and install Ubuntu.  Is this correct?

As stated, Ubuntu is downloaded as an .iso file, not zip.  It sounds like you have not downloaded the correct file for Ubuntu.  And it is important to ensure you have 384+MB RAM in the Thinkpad too.

In which computer is your CD-writer?

---

### Post by uilyam on 2008-08-27
shane19174: What zip file did you download?

Shane, I downloaded ubuntu-8.04.1-desktop-i386.iso, which I called a zip file for short because of the icon Windows gave it. Actually looking at the file now for the first time, I see the following in this ISO9660 archive in the file README.diskdefines:

#define DISKNAME  Ubuntu 8.04.1 "Hardy Heron" - Release i386
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

The file was downloaded yesterday from the yandex.ru mirror (because Yandex is in the building next door to where I was then, I thought it was probably the closest mirror).

It is not really relevant, but the worm infestation on the notebook is by Win32.Sality.z (Kaspersky).

---

### Post by mellowd on 2008-08-27
Much easier solution:

Download the alternative install iso image (it's not a zip file)

Create a cd with that image.

Boot off the CD

Format the drive during install (now the virus is gone)

continue installing ubuntu

make a cup of coffee and relax in your snugness

---

### Post by shane19174 on 2008-08-27
OK, so now you just need to burn the image (.iso) to a CD (note: don't burn the file as normal, but instead make sure to burn it as an image. For example, if you're using Nero, there's an option somewhere to "burn disk image". If I recall, seems to be somewhere under "Recorder options" or something like that. Of course, if you're using a Russian-language version, it will be called something different).

Edit: or as mellowd suggested. But if you've already got the .iso, you don't have to download anything else.

---

### Post by uilyam on 2008-08-27
ugm6hr: I'll answer your last two questions first.

Q2. I assume from what you have written that the 2 older computers have working OS (Microsoft) that you want to retain, and you want to completely wipe the 2003 Thinkpad and install Ubuntu. Is this correct?

A2. Yes, this is correct.

Q3. In which computer is your CD-writer?

It is on my "newer" computer, which is where a copy of the ISO file is (there is also a copy on my flash and on the computer I use at the editorial office in Moscow). I think my next step will be to go to the store and buy a couple writeable CDs and then see if I can burn this file to a CD. If it doesn't work, then I can try again at the editorial office (where I know the CD burner works). I expect to be there tomorrow afternoon, certainly not later than Friday.

Now for your first question.

What is my final plan? I don't know yet, and I hope my termination is far enough away that as Scarlet O'Hara said in Gone With the Wind, "I'll think about that tomorrow."

I am being only slightly facetious. I want to get the notebook fully (and safely) functional as quickly and cheaply as possible. I have a lot of work to do and very little time. Playing with computers is not my thing now, although in my time I have repaired disk drives, restored systems to operation, programed in a few languages from assembler on a couple minis in the 1960s and 1970s to higher-level languages of various types. I had my own business selling and supporting micro-based business (and other) systems in the 1980s. And so on. But for the last ten to fifteen years, I am just a "user."

I make my plans to be flexible so that they evolve as my needs and the situation change.

---

### Post by uilyam on 2008-08-27
mellowd: "make a cup of coffee and relax in your snugness"

You nailed it! Thanks!

---

### Post by k3lt01 on 2008-08-27
I would encourage you to also use the Russian Language forum, not because your Russian as your English is excellent but, because you may be able to contact people closer to you (Moscow) if you have questions and because they are local they may answer sonner than the rest of us will due to time differences.

---

### Post by ugm6hr on 2008-08-27
> **uilyam said:**
> Q3. In which computer is your CD-writer?

It is on my "newer" computer, which is where a copy of the ISO file is (there is also a copy on my flash and on the computer I use at the editorial office in Moscow).

This will help ensure you burn the CD correctly from XP: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

If you don't already have a decent CD burning application, InfraRecorder is free.

PS: I recommend CD-R rather than CD-RW, but the latter should (and does) generally work OK.

---

### Post by uilyam on 2008-08-27
ugm6hr: Thanks much for the link on burning. I have printed it for study. I haven't gone to the store for CDs yet (thanks for the recommendation on CD-r versus CD-RW). My wife asked me to wait until after she fixed lunch and I ate it.

"Remember: no matter what burning program you use, never burn ISOs as data, and never extract the ISO using a zip-file program or WinRar."

Ha! While I was waiting I had violated this injunction before reading it at the link you provided.

I unzipped the iso file with WinRAR and installed a dual-boot on my "newer" machine. I'm afraid I may have a Russian version. Although I specified English on the install, the first four options on the boot menu are in gibberish. I basically figured out what they are by trying them. And of course I have already learned some linux commands from dealing with BusyBox.

I expect things to be different after I get the CD and boot from it.

"If you don't already have a decent CD burning application..."

Thanks again. I am mostly concerned whether the hardware works properly on this machine, never having burnt a CD on it and knowing that I had to take care of some other problems when it was first given to me about a year ago.

k3lt01: "I would encourage you to also use the Russian Language forum..."

Thanks, but the problem is first that I almost never write anything in Russian and second that my vocabulary is limited in Russian in any area in which I haven't dealt with extensively in Russian (such as this area). So an English language forum is much better for me.

---

### Post by uilyam on 2008-08-27
**FINAL REPORT**

I bought a CD-R (actually three at 15 rubles each including case). There seems to be a problem with Nero installed on this computer.

The md5 Hash was fine, and so my download was good.

InfraRecorder vers. 0.42.1.0 worked fine. At 8X it took about ten minutes to burn a disk.

I booted from the CD on the Thinkpad and verified the integrity of the CD. Then I installed Ubuntu, assigning the whole drive as the Ubuntu partition (WARNING: I lost all 500+ copies of the virus!).

I set up three other users (wife, daughter, and son).

Everything is fine. Thanks to everyone who helped!

---

### Post by ugm6hr on 2008-08-27
Glad to hear everything is sorted.

At least you have 1 computer resilient to viruses now...

From memory, there is a Thinkpad specific Linux forum out there somewhere too if you need laptop-specific help.

---

### Post by k3lt01 on 2008-08-28
> **uilyam said:**
> k3lt01: "I would encourage you to also use the Russian Language forum..."

Thanks, but the problem is first that I almost never write anything in Russian and second that my vocabulary is limited in Russian in any area in which I haven't dealt with extensively in Russian (such as this area). So an English language forum is much better for me.:lolflag: Sorry I thought you were Russian, but it seems your an expat.

---

