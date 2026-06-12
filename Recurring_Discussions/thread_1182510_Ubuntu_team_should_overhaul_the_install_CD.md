---
title: "Ubuntu team should overhaul the install CD"
date: 2009-06-09
forum: Recurring Discussions
---

### Post by leemckusic on 2009-06-09
[SIZE="4"]I feel the Ubuntu team should overhaul the install CD. 

   This message is an appeal for the forum moderators to carry a very loud message back to the developers: A huge fraction of potential Ubuntu installs are failing, the would be users are too humiliated to even post to the forums. 

   **The Ubuntu Install CD needs to either run as planned or show a text error message and a URL for requesting help. The success rate needs to be 100% for some kind of output. Every blank screen is a lost user.  **

   I would like to do Linux conversions and office desktop support. On a wide range of PC hardware, about 1/2 of my Ubuntu CD install attempts fail without any installation log or terminal session to read. 

     I like the Ubuntu desktop but the Centos installer runs to completion 100% of the time on every machine where I tried Ubuntu first. 

   The Ubuntu install CD's since 6.10 feel like somebody with a lot of attitude is forcing a fancy programming project. The install CD needs to be a simple dependable scheme.  

    Second, but less serious, I now allow a week for futzing to clear up the silly ticky tacky stuff like messed up printing.

     I have had several cases of trying a Ubuntu CD and getting a "black screen" or at best a "BusyBox error" or BusyBox terminal with no error messages. 

     In three recent installs, Ubuntu installed on 1 of 3 trials and  Centos installed on the 2 machines where Ubuntu would not. 

     There is no easy way to bring up a shell and find error messages when the install CD hangs up. Or else the usual Alt-Fn key combination I expect has been changed.

     On an atom based WindPC, Ubuntu 8.04 completely failed to run and no keystroke combination would bring up a shell to read the error messages. I needed to set up a Rails development environment with Substruct so I burned a Centos 5 install CD and got the operating system and packages installed in a few hours. 

      My present desktop machine is a dependable 11 year old 700 mhz Athlon with 2gigs of ram. It was running feisty 7.04 and I was forced to upgrade due to needing packages for an Arduino project. 

      I have 3 install CDs on hand. They all hang up with either a blank screen, a busybox error or a busybox terminal with no messages. I compromised by doing a manual Debian style upgrade.

    The upgrade required editing /etc/apt/sources.list to point to [http://old-releases/ubuntu/dists](http://old-releases/ubuntu/dists) and then doing an upgrade with the classic Debian commands: 
sudo apt-get update. 
Then editing sources.list again to point to hardy. 
More Debian commands. 

     Kind of halfway fixed, 7 evenings of futzing to get back to my plain old web, spreadsheet, writing, Rails and Arduino projects. As Tigger in Winnie the Pooh says "Why, why, why?" 

    I have a friend who buys new-obsolete computer components and builds PC systems and sells and gives the systems away. Of three systems he "loaned" me the laptop runs 8.10 (great), the media center shoebox runs Centos (failed Ubuntu install) and the third box does XP without my help. I tell my friend Ubuntu has a great desktop. He has had Ubuntu install problems so long he forgets when he gave up.

    So, my comment is: the Ubuntu desktop design is wonderful, but the install CD has grave problems.

I have been running Linux since Yggdrasil Plug and Play Linux 1994. Thanks for speaking upward to the programmers and please don't bury this experience report.[/SIZE]

---

### Post by Sef on 2009-06-09
Moved to Recurring Discussions.  Nothing new about Ubuntu failing to support or be supported by every piece of hardware.

---

### Post by 3rdalbum on 2009-06-09
> **leemckusic said:**
> I have been running Linux since Yggdrasil Plug and Play Linux 1984.

I sure hope you mean 1994.

Have you tried using the Desktop CD, as opposed to the Alternate CD? That's what I've been using for my installs for the last three years, with no problems. Cold comfort if you want to preseed the install configuration, but there you have it.

The alternate CD installer is exactly the same as Debian's default text-mode installer, and almost the same as Debian's GUI installer. I've never found it to be problematic, except that it can only install from CD. I have not found a way to install it from a USB flash drive, which I'm guessing is what you tried to do on the Wind.

In short, use the installer that's on the Desktop CD. You don't have to actually run a live session to use it.

---

### Post by tsali on 2009-06-09
You seem to be very experienced, so you've probably exhausted all of the suggestion I'll offer:

[LIST]
Do not burn to a CD-RW
Verify the Checksum
Try both desktop and alternate install
[/LIST]

Alternate install usually works for me on older and low resource hardware. Oddly, I couldn't get any version of Ubuntu to install prior to 7.04, and I've ALWAYS had the same experiences you decribe with any Red Hat based distro (Fedora, Cent, PCLOS)

I've been very successful with Debian, Ubuntu and Mepis.

---

### Post by leandromartinez98 on 2009-06-09
I had many problems with instalation CDs as well, of different versions, and not on old hardware. Similar problems as the ones described by him. I agree with him that there is an issue there.

---

### Post by juancarlospaco on 2009-06-09
*LOL CentOS can't Upgrade, and you come here to complain...? LOL*

Learn first about Boot Kernel parameters and best practices on installation.
and then you will be sucessfull :)

---

### Post by leemckusic on 2009-06-11
Thanks for confirming my comment that the Ubuntu Installer has a serious problem:

The Ubuntu Installer stops without providing an install log or session transcript with error messages.

So let's say: the Installer hangs 30% of the time on the first time a user sticks the CD in the machine.

The interesting thing is: nobody on the entire Ubuntu Forum system knows what is wrong. There are four recurring guesses:

1.  You have a hardware problem on the target PC.
2.  This time your CD burner made a critical error.
3.  Try the alternate install CD.
4.  Try changing the boot parameters passed to the install Linux
kernel.

    Here is what this all points to: so few ideas coming from very experienced Ubuntu forum team advisors means the user experiencing the Install CD problem does not have enough meaningful data to describe the problem.

        So I circle back around:

        The Ubuntu Installer has to spit out more troubleshooting information early in the install process.

        The installer needs a proven reliable lowest-common-denominator kernel with a character terminal.

        The installer needs to generate an install logfile and a dmesg file right away.

        The install log file needs to be accessible to the install person either by copying to a floppy or to a USB-drive or to another computer by scp.

---

### Post by CJ Master on 2009-06-11
[SIZE="4"]I like large bold fonts. Do you like large bold fonts? I like large bold fonts.[/size]

---

### Post by ad_267 on 2009-06-11
> **CJ Master said:**
> [SIZE="4"]I like large bold fonts. Do you like large bold fonts? I like large bold fonts.[/size]

[SIZE="4"]I like large fonts too. I always use large fonts to show that my posts are more important than anyone else's.[/size]

And what's up with all the tiny fonts everyone else is using. Geez I have to squint reeeeal hard.

---

### Post by starcannon on 2009-06-11
> **leemckusic said:**
> [SIZE=1]I feel the Ubuntu team should overhaul the install CD. 

   This message is an appeal for the forum moderators to carry a very loud message back to the developers: A huge fraction of potential Ubuntu installs are failing, the would be users are too humiliated to even post to the forums. 

   I would like to do Linux conversions and office desktop support. On a wide range of PC hardware, about 1/2 of my Ubuntu CD install attempts fail without any installation log or terminal session to read. 

     I like the Ubuntu desktop but the Centos installer runs to completion 100% of the time on every machine where I tried Ubuntu first. 

   The Ubuntu install CD's since 6.10 feel like somebody with a lot of attitude is forcing a fancy programming project. The install CD needs to be a simple dependable scheme.  

    Second, but less serious, I now allow a week for futzing to clear up the silly ticky tacky stuff like messed up printing.

     I have had several cases of trying a Ubuntu CD and getting a "black screen" or at best a "BusyBox error" or BusyBox terminal with no error messages. 

     In three recent installs, Ubuntu installed on 1 of 3 trials and  Centos installed on the 2 machines where Ubuntu would not. 

     There is no easy way to bring up a shell and find error messages when the install CD hangs up. Or else the usual Alt-Fn key combination I expect has been changed.

     On an atom based WindPC, Ubuntu 8.04 completely failed to run and no keystroke combination would bring up a shell to read the error messages. I needed to set up a Rails development environment with Substruct so I burned a Centos 5 install CD and got the operating system and packages installed in a few hours. 

      My present desktop machine is a dependable 11 year old 700 mhz Athlon with 2gigs of ram. It was running feisty 7.04 and I was forced to upgrade due to needing packages for an Arduino project. 

      I have 3 install CDs on hand. They all hang up with either a blank screen, a busybox error or a busybox terminal with no messages. I compromised by doing a manual Debian style upgrade.

    The upgrade required editing /etc/apt/sources.list to point to [http://old-releases/ubuntu/dists](http://old-releases/ubuntu/dists) and then doing an upgrade with the classic Debian commands: 
sudo apt-get update. 
Then editing sources.list again to point to hardy. 
More Debian commands. 

     Kind of halfway fixed, 7 evenings of futzing to get back to my plain old web, spreadsheet, writing, Rails and Arduino projects. As Tigger in Winnie the Pooh says "Why, why, why?" 

    I have a friend who buys new-obsolete computer components and builds PC systems and sells and gives the systems away. Of three systems he "loaned" me the laptop runs 8.10 (great), the media center shoebox runs Centos (failed Ubuntu install) and the third box does XP without my help. I tell my friend Ubuntu has a great desktop. He has had Ubuntu install problems so long he forgets when he gave up.

    So, my comment is: the Ubuntu desktop design is wonderful, but the install CD has grave problems.

I have been running Linux since Yggdrasil Plug and Play Linux 1984. Thanks for speaking upward to the programmers and please don't bury this experience report.[/SIZE]

Hmm, strange, I have an MSI Wind, Ubuntu installed beautifully on it. WiFi, HP printer, everything works. Do you have any posts describing problems with that particular machine? I really only had one issue with WiFi, and that was easily sorted.

GL with whatever works best for you.

---

### Post by leemckusic on 2009-06-23
Well, eventually I will re-try a Ubuntu Install CD on my Wind-PC.

Meanwhile, I wish I could persuade some more experienced Ubuntu Forums posters to realize: 

The Ubuntu Install CD system needs to be fixed so 100% of the trials result in either an Install or a meaningful error message and a web address to go to for help.

[B][U]The point is this is the thing that has to work right 100% of the time. 
This is the thing absolutely needed to grow new Ubuntu users and new installations[/U][/B].

---

### Post by konnorrigby on 2009-06-23
Hi. i think the cd is ine it could use some improve ments. lyke a built in dial p connection. and mabey some guides but not an overhaul

---

### Post by kelvin spratt on 2009-06-23
Most of the problems with failed installs are down to cheap cds burned at to high a speed,using poorly written software, 
I only use verbatim CDs/DVDs usually rewritable and in 2 years and over 200 distro installs never had a failure.
 There is a old saying a bad workman always blames his tools, this is very true garbage in garbage out.

---

### Post by leemckusic on 2009-06-23
Well, you have strongly argued my problems with the Ubuntu Install CD are due to bad media or bad cd burning software. 

I post a Url below, I went looking for an article addressing How to Validate a CD. I have been trying to Validate the actual CD install media I am using. 

So far, my results suggest we have a tool problem. Even the brutally low level "dd" file reading tool can't read a bootable Install type CD and give back a md5sum that proves the CD image exactly matches the downloaded file.

Kevin, what do you see in md5sum results when you run:

md5sum /dev/hdc on a Ubuntu Install CD?

What do you see when you run:
dd if=/dev/hdc bs=2048 | md5sum

Does either way give you an md5sum that agrees with the md5sum when you check the Ubuntu Install disk file such as:
md5sum ubuntu-8.10-desktop-i386.iso

Using the instructions from the "How to validate a CD" article referenced below, here is what I see so far:

md5sum /dev/hdc           ; command always fails with Input/output error

So I tried the more drastic dd direct disk read technique suggested in the article;

First I try both the dd= test and the md5sum command on my disk file to see of the dd technique returns the correct md5 sum. It does when reading a disk file:

flibberty:~/Desktop$ dd if=/home/lmckusic/Desktop/ubuntu-8.10-desktop-i386.iso bs=2048 | md5sum
357796+0 records in
357796+0 records out
732766208 bytes (733 MB) copied, 30.7762 s, 23.8 MB/s
24ea1163ea6c9f5dae77de8c49ee7c03  -

flibberty:~/Desktop$ md5sum ubuntu-8.10-desktop-i386.iso 
24ea1163ea6c9f5dae77de8c49ee7c03  ubuntu-8.10-desktop-i386.iso

Good: so far the downloaded file exactly matches the published MD5 sums and further the dd technique exactly matches the file system read of the same file.

Now try the dd technique to find a md5sum on a freshly burned CD of the very file named above:

flibberty:~/Desktop$ # Taking md5sum of ubuntu 8.10 cd burned on 6-23-2009

flibberty:~/Desktop$ dd if=/dev/hdc bs=2048 | md5sum

dd: reading `/dev/hdc': Input/output error
357752+0 records in
357752+0 records out
732676096 bytes (733 MB) copied, 139.679 s, 5.2 MB/s
38de53a0ce49deaaa0b2da5daf17c148  

So far: bad news. The straight GnomeBaker "burn iso image" does not create a file with the md5sum we need to confirm accuracy.

So I tried GnomeBaker "burn iso image" with the "dao" option suggested in the How to Validate CD article. GnomeBaker quit with a "write failed message."

Got any suggestions? Can we figure out a way to make md5sum report an exact match value for the published md5sums for the file system file?

Is your setup creating CDs with a valid md5sum when you read the Ubuntu Install CD media? 

Try it on your setup and tell me if your setup is giving you an md5sum directly from the media.

Using Google I looked for "validate a CD" and found the following article:
[URL="http://www.sun.com/bigadmin/features/articles/burn_iso_images.jsp[/URL]

Note the article points out, 
"So the moral of the story is to remember to pad the last block with -pad or better yet, write your CDRs in 'session at once' mode using -dao, and then use md5sum to compare with the original ISO binary image. "

---

### Post by leemckusic on 2009-07-17
My friend who builds PCs from recent obsolete parts tells me that some cheap Sony DVD burners had some problems making CDs. He loaned me an older external USB CD burner.

My first conclusion is my Sony DVD burner develops a read error when it is reading long compressed files. Less clearly, some of the time the same drive makes an error when writing long compressed files.

The open source software community needs a byte accurate error locating checksum. md5sum reports an error exists but it does not show where the error occurred.

*I suggest the first thing to try is Do Not Compress the initrd file on the Ubuntu install CD.*

I regularly see my Sony DVD drive generate a read error on the /casper/initrd.gz file. The compression of this file does not save much disk space on the Ubuntu install CD.  

$ find /boot /media/Ubuntu\ 9.04\ i386/ -name initrd\* -ls

 12052 8357 -rw-r--r--   1 root     root      8522304 Jun 29 20:31 /boot/initrd.img-2.6.20-16-386
  2324 7567 -r--r--r--   2 lmckusic root      7747987 Apr 20 07:12 /media/Ubuntu\ 9.04\ i386/casper/initrd.gz

A second thing I am seeing on the Ubuntu install cd is the entire file system is one 707 megabyte compressed file. 

*I suggest this file be broken into smaller mountable chunks.* The install program can now complain if the Drive reading the CD is making read errors. 

Huge file system is one compressed file:

 ls -l /media/Ubuntu\ 9.04\ i386/casper/filesystem.squashfs 

-r--r--r-- 2 lmckusic root 707850240 2009-04-20 07:17 /media/Ubuntu 9.04 i386/casper/filesystem.squashfs



A way to test an entire physical CD disk is:

dd if=/dev/hdc bs=2048 | md5sum 

A way to match the files on a mounted CD with the md5sums computed by the disk maker is:

cd /media/Ubuntu\ 9.04\ i386/  ; cd to the mounted disk
md5sum -c md5sum.txt           ; check for exact read

---

### Post by lisati on 2009-07-17
I think I'm missing something here in this thread. 
[LIST]
[*]Should the Ubuntu installer(s) somehow be endowed with mindrearing capabilities that somehow assess the abilities of the person using it?
[*]Should it be capable of running perfectly on ALL hardware, no matter what, regardless of subtle differences in setups and level of user experience?
[*]What? no existing online help?
[/LIST]

Some potentially useful information for first-time users can be found at [http://help.ubuntu.com]("http://help.ubuntu.com"). Of particular interest when it comes to download and disk-burning issues can be found at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto), which includes information about checking download images and CD integrity.

---

### Post by zevans on 2009-07-17
> **starcannon said:**
> Hmm, strange, I have an MSI Wind, Ubuntu installed beautifully on it. WiFi, HP printer, everything works. Do you have any posts describing problems with that particular machine? I really only had one issue with WiFi, and that was easily sorted.

GL with whatever works best for you.

He was talking about Intrepid, which had lots of niggles on my Advent, Jaunty almost out of the box except Intel graphics performance, and that is now semi-fixed in -updates, so I think a fresh install WITH UPDATES of Jaunty would be good to go on an MSI now. But Intrepid certainly wasn't!

---

### Post by zevans on 2009-07-17
> **Sef said:**
> Moved to Recurring Discussions.  Nothing new about Ubuntu failing to support or be supported by every piece of hardware.

You have utterly missed the point - leemckusic was suggesting that we need graceful failures when there are hardware problems. He absolutely was not complaining about hardware support.

---

### Post by leemckusic on 2009-07-18
Here is the dmesg identification for a Sony DVD drive that has a very bad case of writing bad Ubuntu Install CDs. 

~$ dmesg | grep SONY
[    9.340000] hdc: SONY DVD RW AW-G170A, ATAPI CD/DVD-ROM drive

The same drive unfortunately wrote a usable Centos Install DVD right around the same time it generated a bad Ubuntu install CD.

The problem I am working on right now is what the heck is going on with this AW-G170A drive? I have conflicting results on my tests so far. 

There are two differences that jump out at me: 

[LIST]
[*]This drive burns DVDs ok and burns CDs with an error.
[*]This drive is stumbling on big compressed files. Ubuntu uses huge essential compressed files and Centos has only a few trivial .gz files.
[/LIST]

So what does it matter? It matters like this; the Ubuntu installer, in my experience, is stopping without any meaningful error message. 

To understand what is going on I have been searching for a method to find exactly where the first error in a file is. 

The hunch I have is the Ubuntu CD has a compressed initrd file. That means it is tightly packed 8 bit data. Now where is this 1 bit error coming from? Is the drive CRC only addressing the first seven bits of each byte? Are there occasional blocks of zeros inserted when the drive has an error? 

The symptom I see, of the install silently stopping would agree with gunzip failing while unzipping the initrd.gz file. The install CD doesn't have shells or logging screens until the initrd file is unpacked into RAM.

---

### Post by leemckusic on 2009-09-30
The brainstorm idea is:

I should master a Ubuntu Install CD specifically designed to run and recover from errors created by low quality Windows CD drives like the one I have. 

The remastered CD would be like this:

     The initrd file would be uncompressed.

     The live file system would be uncompressed.

     An then the install package would be enhanced to help new users get replacements for any files or packages that are damaged on the "install CD". Develop the install system to help people behind firewalls and running of of CD media with no internet access.

   The name for this Ubuntu redistribution:

 "ShouldInstallUbuntu" (... no matter how bad your CD drive). 

  P.S. I still have a buggy DVD/CD drive in my old computer so I have a great place to test the remastered Ubuntu install CD. The drive is  hdc: SONY DVD RW AW-G170A, ATAPI CD/DVD-ROM drive

---

### Post by FunkyRes on 2009-09-30
I always use CD-R - never CD-RW

I always use the dao and pad option to cdrecord - IE

cdrecord -dev=/dev/scd0 -speed=24 -dao -pad -v /path/to/whatever.iso

I always burn as root (sudo should suffice)

I try to always have the iso on a different physical disk than / or /home is on.

CD's I burn at 24x, DVD's at 8x, but keep in mind I'm SATA-II - for ATAPI, those may be too fast for consistent good burns.

---

### Post by Exodist on 2009-10-01
> **CJ Master said:**
> [SIZE="4"]I like large bold fonts. Do you like large bold fonts? I like large bold fonts.[/size]

+1  :lolflag:




I will like to say though Software RAID seems to be removed on the Normal/Live CD. At least I havent seen it and I used to use it alot.

---

### Post by juancarlospaco on 2009-10-01
Please stop Bloating, Linux will be lightining fast and minimalistic...

---

