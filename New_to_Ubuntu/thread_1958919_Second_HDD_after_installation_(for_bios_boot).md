---
title: "Second HDD after installation (for bios boot)"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Diggory on 2012-04-15
Hi to all - must just say before I ask for advice, what an excellent forum.

As I am a new to linux/ubuntu, I thought it best to ask advice before I started.
I have searched on this but couldn’t quite find quite what I was looking for.
Situation is that I have an xp pro system that I want to convert to ubuntu 11.10.
I have bought a new 500gb enterprise hdd and want to use this for my new ubuntu os.
I don’t want a true dual boot system as I am happy to manage this from bios.
My plan is to phase out windows but keep the os on second hdd for rare occasions when I need to use windows only software (drawing package, inkjet photo printer etc). 

My installation is plan is as follows:

1.) unhook my current xp hdd - still has my data on it
2.) hook up new 500gb hdd as sata1
3.) install ubuntu 11.10 to new 500gb hdd in sata1
4.) use manual partition option to keep ubuntu os and home separate
5.) allocate say 10gb to ubuntu os and keep balance for home 
6.) check ubuntu 11.10 works okay (did on live cd)
7.) hook up my old xp hdd to sata2
8.) copy my data across from old xp hdd to new ubuntu home
9.) keep old xp hdd hooked up and boot it from bios only when I absolutely have to

I am wondering will I have problems with ubuntu seeing (mounting ?) the xp hdd when I add it after installation. Does this seem a reasonable approach grateful of your advice.

Many thanks Diggory

---

### Post by westie457 on 2012-04-15
Hi. Welcome to UF.

Your plan for installation is good and will work.

Only a small issue about these steps > 4.) use manual partition option to keep ubuntu os and home separate
5.) allocate say 10gb to ubuntu os and keep balance for home

Personally I would set up a DATA partition formatted as NTFS and have a smaller /Home (around 40 GBs should be plenty of space.

Copy data from the XP to the Data partition then it will be available to both operating systems.

Attached is a screenshot of my current hard drive set up on a single drive to show what I mean.


Hope this helps.

---

### Post by Diggory on 2012-04-15
Thank you Westie457
Reassuring to know I am on the right track and that second hdd will mount/be recognised.
Your suggestion about the extra (ntfs) data partition has made me think.
Like many, I have always preferred my os and data separate.
This is what i was hoping to achieve by placing home in its own partition - not sure now.
If I needed to re-build ubuntu, I am wondering if my home (albeit partitioned) would be overwritten anyway.
Is this what you were meaning.

Would this be a better setup than having >400GB of home.
500gb hdd:
/dev/sda1 EXT 10GB OS
/dev/sda2 SWAP 2GB
/dev/sda3 EXT 40GB HOME
/dev/sda4 NTFS 448GB DATA

I have never used GParted but see it is quite well regarded in the UF.
Would I be correct in thinking that i could resize or even add the NTFS partition after the ubuntu build.

Many Thanks D.

---

### Post by oldfred on 2012-04-15
You may want to keep the windows drive as sda, as the boot.ini has references to drive by number. You can manually edit boot.ini if you really want it as the second drive or run repairs to have Windows fix boot.ini.

Grub also adds mapdevice commands to make Window think it is sda when it is not, but booting with BIOS may have issues.

With a 500GB drive I might make / (root) 25GB but otherwise no other suggestions, it looks good. I find I use 4GB in /tmp when writing a DVD and with lots of programs installed my / is 6GB without /home, so 10GB may not give lots of room. If hard drive was small then 10GB would be ok.

I would have suggested  gpt partitioning if only a Linux drive but I do not think XP reads gpt drives. Vista or 7 will read gpt drives but  only boot from them if using the new UEFI not BIOS to boot.

---

### Post by Diggory on 2012-04-15
Thanks Oldfred.

Very useful advice on the partition sizing - will bear in mind.

To make my xp hdd sda sounds like I would need to keep it hooked up for the ubunu installation.
Was hoping I wouldn't need to do this or get into the whole grub thing - like to keep it simple.
(& work towards phasing out windows rather than building it in)
What kind of bios problems might i encounter with my approach.

On the ext vs ntfs format - I think westie457 suggested ntfs so that xp would recognise the data partition on new sda 500gb ubuntu hdd. 
if i still have my xp hdd hooked up as sda2, could i save from linux to xp data area on rare occasion i need to open a specific file in xp for printing say.

Thanks D

---

### Post by oldfred on 2012-04-15
No you do not have to have XP drive connected to install Ubuntu. Ubuntu converted from devices like /dev/sda1 to UUIDs, so changing from sda to sdb makes no difference to Ubuntu. Or you can install Ubuntu to sda, and let it become sdb and keep Windows as sda. 

If you do keep both drives connected you have to use manual install and pay careful attention to the combo box on where to install the grub2 boot loader. See last link with is just the graphic in Herman's site.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Diggory on 2012-04-16
Oldfred - many thanks.
Some really useful links.
I will have a read.
D

---

### Post by gordintoronto on 2012-04-16
I agree with the larger / partition. You probably won't need it, but if you do, the aggravation is enormous.

---

### Post by d4m1r on 2012-04-16
1) No need to physically disconnect or move the Windows HDD.

2) Yes, I'd recommend more than 10GB for Ubuntu, if you have the space. I personally allocated 20GB for 11.10 (32 bit) and while I have 11GB free, its nice to know I have some expansion room. Also, its useful when I need to transfer larger files through Ubuntu (but that I don't ultimately store on it).

---

### Post by Diggory on 2012-04-23
Dear All

I thought I would post an update on how things have gone.

Firstly, many thanks for all the advice and links - really great.
I followed the approach outlined in first post and all seems to have gone well.
My Ubuntu 500GB HDD is on SATA1 and my XP HDD is on SATA2.
I can manage the boot selection from BIOS and XP works fine on SATA2.
XP HDD will mount okay from UBUNTU and I have copied some data across into Home.
I have some unallocated space at the end of the new UBUNTU HDD that I intend to Format NTFS from XP but have not got around to this bit yet.

I have downloaded GParted and used it to have a look at my 500GB UBUNTU HDD.
I am a bit puzzled about the partitions so should appreciate some advice here.
The GParted table is as follows:
/dev/sda1 EXT4 Mount point / Size 23.3GB (3.7 GB used)
/dev/sda2 linux-swap 1.9GB
/dev/sda3 EXT4 Mount point /home 93.1GB
unallocated 347GB

My nominal sizes during installation were 25GB,2GB and 100GB - not sure why I have lost say 7GB from /home; is this normal
Also wasn't expecting my sda1 to be flagged as "boot".
I thought when I worked through installation, there was (already) a 500MB  allocated to boot - have I missed something here. 
Should I have a 500MB /boot partition ?

Thanks D

---

### Post by oldfred on 2012-04-23
Windows uses boot flag and it has to be on a primary partition, grub does not use a boot flag. But a few BIOS require a boot flag so it a good idea just to have one.

A boot flag is not a boot partition except for Windows. In Linux for standard desktops you rarely need a /boot partition. Servers, RAID, LVM and old system may need a separate /boot partition. You have a /boot folder in your / (root) and that is fine.

Your sizes are into how bytes are counted. Hard drives are not normally counted the same as RAM.

MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)
More confusion?
[http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release](http://www.neowin.net/news/ubuntu-implements-units-policy-will-switch-to-base-10-units-in-future-release)

---

### Post by Diggory on 2012-04-24
Oldfred - thanks again.

So i don't need a separate /boot partition - that's a relief.

Thought you maybe interested in some feedback from my wife.
She looked worried when she saw me taking the computer to bits.
Even more so when I said Windows would soon be going.
A few days after UBUNTU install:
"I like the computer, really simple and uncomplicated .......... and quicker"

Thanks again D

---

### Post by oldfred on 2012-04-24
You are welcome, glad you got it working. That spouse is happy is most important. 

Currently with 12.04 my spouse is not totally pleased and it is one minor issue that openyahtzee does not work. Her other game and applications seem ok so it is not a major problem, yet.

---

### Post by zandman on 2012-04-24
And to make things even simpler: convert the 2nd hdd with XP-Pro on it to a VMWare-image (there are tools for that), install VirtualBox and import the image there. Then the whole "oh, i have to reboot to do Windows stuff"can be skipped. But don forget to install a lot of ram for that. I run it on different PC's and based on my own experiences i would suggest at least 4Gb.

---

### Post by Diggory on 2012-04-26
Oh dear - i may have spoken too soon.

My wife called me at work - "the cursor has frozen"
Tried all-sorts via phone to no avail so did soft re-boot.
The machine booted and she left it on login screen.
I guess it went into sleep mode, when i came home it was again not responding.
Another reboot and fired up into a Grub screen - never seen this one before.
I couldn't use the up/down or enter keys - doh.
I have a Logitech cordless keyboard and mouse.
Plugged in a backup serial keyboard and selected the highlighted option (first on list).
Everything booted okay and we seem to be back in business albeit a bit glitchy.
(and some loss in wife confidence).
I had previously noticed some screen breakup on start up/shut down - wasn't too worried.
Assumed this to be something to do with a graphics card (load) problem but not too serious.
It all seemed to work fine once it had got passed start-up.
Grateful of any thoughts.
Thanks D

(I have edited the post title)

---

### Post by oldfred on 2012-04-26
If you have to shutdown remember the elephants. 

Grub recognizes a bad reboot and gives you the menu, so you can use recovery mode in case repairs are required. So it does not auto reboot.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by Diggory on 2012-04-27
Oldfred - thanks again.

R-E-I-S-U-B - that's a new one for me
I will re-post that on a yellow post-it note & stick it to screen
(Have just ordered O'Reilly's Linux Pocket Guide)

Any thoughts on what might cause the glitchy behavior
The only problem i was getting, was some screen break up on boot and close
Do you think this would lead to a lock-up  - i assumed this was a graphics driver loading problem
Once system was up and running it worked fine - so i wasn't stressing over this
It may have frozen (second time) after it went into sleep mode - i have changed settings "to off never"
Is there a diagnostic i could run - say a log file

Thanks D

---

### Post by oldfred on 2012-04-27
You can look at log files with log file viewer. It is in system tools in fall back. Not sure how to get to it other than type it with Unity.

I get some minor alignment issues on shutdown which I have have not worried about.
On boot issues I look for long times between drivers/processes or repeated processes trying & failing. Not sure what to look for in your case, but probably worthwhile to review logs to see if anything is reported.

---

### Post by Diggory on 2012-05-07
Dear All - thought I would post back an update.
I am really pleased with 11.10 - I really don't like booting into Windows now.
I do it so infrequently the managing it from BIOS is fine.
I still get the odd system freeze - i will post another thread on this as I think i need some help with log files

Back to this thread ..........................
I finally got around to setting up the NTFS partition in the unallocated space as per advice.
(I have left circa 50GB still unallocated for partition size management)
Couple of things I would like to check - more things that I wasn't expecting rather than problems.

I created the NTFS partition from Windows (although not Win7, I used XPpro and Acronis).
When I looked at the new NTFS partition from Ubuntu - I was surprised to find it is was not empty.
It already contained a folder called "System Volume Info".
This then contains another folder "EfaData" - that contains a file "Symefa.db".
Other files in "System Volume Info" are "LightningSand.cfd" and "MountPointManagerRemoteDatabase".
Do I need any of this stuff or can I delete it ?

The other surprise was that I have to mount it with a password - not a drama but not what I had in mind.
Can I set the system to always mount this drive (after all it is on same HDD) and without a password.

Many thanks D

---

### Post by oldfred on 2012-05-07
It sounds like you created a encrypted partition. Not familiar with those tools. I only use gparted. 

You need to have a copy of Windows or a Windows repair CD as long as you have a NTFS partition. While you can do many repairs from Linux you have to run chkdsk ( and maybe defrag) from Windows and you should run that regularly. Windows does not schedule it, Ubuntu runs fsck every 40 or 60 reboots on its root partition.

---

### Post by Diggory on 2012-05-07
Oldfred - thanks again

I dont think I created an encrypted partition - not sure there is an option for this.
I have downloaded GParted - could I have used this from UBUNTU to create the NTFS partition.

Re the disk management tools - sounds like you think the NTFS is a bit of a faff.
I was wondering about this, even if I had files on my data partition and the UBUNTU system went down, I could still copy files to my old Windows NTFS disk using live CD.

If i was to re-format this (data) partition as Ext from GParted what mount point would i give it.

Thanks D

---

### Post by oldfred on 2012-05-07
I used NTFS after losing some data on FAT32 as it does not support large files. I used it for sharing data with my XP install which I now use very rarely (managed not to boot my desktop XP this years yet). But I cheated and booted my laptop's XP a couple of times. :)

If you have Windows you need the NTFS, but once you convert to Linux, having a Windows format partition can be a hassle. It just is not easy to convert (backup & restore, & set permission & ownership) so I still have data in my NTFS partition. 

I have only used gparted for the last 6 years, including fat32 & NTFS partitions. Some have reported some issues with NTFS and Windows 7 where they had to reformat to NTFS from Windows 7. The boot sector for NTFS has several versions, one for XP, one for Vista/7 and possibly others. Gparted's seems to be the XP version but 7 normally just works with it or converts it if necessary.

---

