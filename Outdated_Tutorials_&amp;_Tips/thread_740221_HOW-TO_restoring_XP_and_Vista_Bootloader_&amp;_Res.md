---
title: "HOW-TO restoring XP and Vista Bootloader &amp; Restoring GRUB"
date: 2008-03-30
forum: Outdated Tutorials &amp; Tips
---

### Post by lswest on 2008-03-30
I've noticed a lot of people asking about restoring Vista/XP bootloaders, and so i decided to write a how-to for this.  Also, i will include a quick how-to on restoring GRUB as well.

For Vista:
Boot to your recovery cd/partition (if you don't have one, or lost yours, you can get a recovery CD from [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") note: the CD is ONLY recovery options, so no cheap way of getting Vista > This download is available to customers running [genuine Microsoft Windows]("http://www.microsoft.com/genuine/ProgramInfo.aspx?displaylang=en&FamilyID=c7d4bc6d-15f3-4284-9123-679830d629f2&sGuid=04e92e07-6a82-4beb-b69b-e5722f56d5ef"). Please click the Continue button to begin Windows validation. As described in our [privacy statement]("http://www.microsoft.com/genuine/downloads/PrivacyInfo.aspx?displaylang=en"), Microsoft will not use the information collected during validation to identify or contact you. part of the disclaimer for the multi-gigabyte download for the actual program used to create that disk.  If you don't agree with it or don't have a genuine windows system, do not use this download.)
After booting to the CD, get to the Recovery Console (it differs for each recovery program, but generally is easily enough found).  Once there type ```
bootrec /fixmbr
bootrec /fixboot
``` which will restore the Vista bootloader.

For XP:
boot to an XP CD (sorry, no links available :P) and, once the menu loads, hit "R" to enter a command prompt.  Once there, choose which partition you want, and enter an admin password (if you have one set).
then type ```
fixmbr
fixboot
``` and the XP bootloader should be restored.

For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type```
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit
```
where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).
If you would like a more detailed explanation **catlett** did a good job with his how-to [here]("http://ubuntuforums.org/showthread.php?t=224351") and also offers troubleshooting ideas.

How to restore GRUB to a partition:
**DISCLAIMER** This is untested, as I haven't had time to do so yet, but it should work.  Any feedback would be great, either by PM or to have a reply posted here.
```
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?**,?**)
quit
```
(for an explanation of the above code, see the info on restoring GRUB to the MBR, apart from the code marked in bold).
There is only one small variation for this (marked in bold) but it's a significant one.  That "?" marked in bold should be the same one you used for your "root" command in the line above.  It will then install GRUB to that partition.

Now, you may ask, why is this on a Linux forum?  Well this is for those people who either decide Ubuntu (or Linux in general) isn't for them, and wish to get back to Vista or XP, or else for those people (like me) who have set up a triple boot system.  To set up a triple boot, i found, it works best if you install the XP bootloader (for XP), then the Vista Bootloader (on top) and then lastly, the GRUB which then allows the booting of all 3 systems.  The problem i ran into was that i had Vista and Ubuntu installed, so i installed XP, then GRUB, and realized XP bootloader files (which are in the Partition and called the ntldr files) could not boot Vista.  I ended up removing Vista then, but that's another story.

Hope this helps,
Lswest

*EDIT* As thegizmoguy point out, restoring a vista bootloader in a tripleboot setup (Linux-->Vista-->XP) will also allow access to the XP partition again

---

### Post by bodhi.zazen on 2008-04-10
Very cool thread.

If I may , this is how to restore the WINDOWS boot loader **[color=blue]FROM LINUX[/color]**

From the Ubuntu Live CD:

[list=number][*]Boot live CD, open a terminal.


[*]Enable The Universe repositories (System->Administation->Software Sources : tic "Community maintained Open Source software (universe)"


[*]Install  ms-sys
		```
sudo apt-get update && sudo apt-get install ms-sys
```


[*]Restore MBR

[list][*]Set up your windows partition :
		```
ms-sys -p /dev/sda1
```
[indent]_Note_: change /dev/sda1 and /dev/sda to your windows partition and MBR

```
ms-sys -p /dev/<drive>
```
<drive> = your windows hard partition (/dev/hda1 or /dev/sda1)[/indent]

[*]Write to MBR :

	[list][*]2000/XP/2003 :

				```
ms-sys -m /dev/sda
```

		[*]DOS/Windows 98/NT : 

				```
ms-sys -w /dev/sda
```[/list]

[indent][color=darkred]ms-sys -p = write to windows partition[/color]

[color=green]ms-sys -w = write Microsoft DOS/Windows NT to MBR[/color]
[color=blue]ms-sys -m = write Microsoft 2000/XP/2003 to MBR[/color][/indent][/list][/list]


How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

----------

From Knoppix :  

boot Knoppix, open a terminal and enter :

sudo install-mbr /dev/hda

[color=blue]I know the[/color] [color=brown]Ubuntu[/color] [color=blue]method works with every version of windows **EXCEPT VISTA** (it may work with Vista, I have not tested it), I have not tried Knoppix[/color]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]*bodhi.[/color][color=darkgray]zazen[/font][/size][/color]*

---

### Post by lswest on 2008-04-10
Thanks for the compliment ^^ and nice, i didn't know you could install an XP bootloader from linux, ties in nicely though ^^, i'll have to try it sometime.

---

### Post by bodhi.zazen on 2008-04-22
For Vista :

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by jvittetoe on 2008-05-02
hi, after running this from my windows sys restore prompt
----
fixmbr
fixboot
----

my windows XP wont load anymore. i get the message 'Failed to load operating system'

so i loaded up ubuntu to try restore the windows boot loader

i get to step three and i get the message from terminal, 
----
E: couldnt find package ms-sys

if this is trying to find my windows install on the my E drive, it wont find it. My windows install is on my C: drive, ubuntu is on E:. they are two seperate hard drives. How can i get it look on the C: drive?

---

### Post by iSplicer on 2008-05-02
Thanks guys, excellent resources. I have used it countless times!

---

### Post by lswest on 2008-05-07
> **jvittetoe said:**
> hi, after running this from my windows sys restore prompt
----
fixmbr
fixboot
----

my windows XP wont load anymore. i get the message 'Failed to load operating system'

so i loaded up ubuntu to try restore the windows boot loader

i get to step three and i get the message from terminal, 
----
E: couldnt find package ms-sys

if this is trying to find my windows install on the my E drive, it wont find it. My windows install is on my C: drive, ubuntu is on E:. they are two seperate hard drives. How can i get it look on the C: drive?

looks like you'll have to install it from source (there's a link on [this page]("http://ms-sys.sourceforge.net/")) and then to make it look on your second hdd, sda=first hard drive, sdb=second hard drive.  Run a ```
sudo fdisk -l
``` to find out which one is the one you need (pick the one that has an NTFS partition)

@ iSplicer: thanks ^^ glad it helped you out.

---

### Post by meierfra. on 2008-05-12
> looks like you'll have to install it from source 

ms-sys is not in the Hardy Repos, but there is a debian package:

[http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")


A few more options to fix the MBR:

1)  

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

(If you are using Ubuntu 8.10 or Ubuntu 8.10 Live CD, lilo is already installed, and the first line is unnecessary)

2)  [SuperGrub]("http://www.supergrubdisk.org/") also has ability to fix the MBR.

---

### Post by pro003 on 2008-05-13
just read this post and am amazed! great stuff... everyday i get surprised with linux in general and ubuntu specially...

great post :KS:KS:KS

---

### Post by bodhi.zazen on 2008-05-13
> **meierfra. said:**
> ms-sys is not in the Hardy Repos, but there is a debian package:

[http://packages.debian.org/etch/ms-sys](http://packages.debian.org/etch/ms-sys)

Or install the 7.10 package ...

[http://packages.ubuntu.com/gutsy/i386/ms-sys/download](http://packages.ubuntu.com/gutsy/i386/ms-sys/download)

[http://packages.ubuntu.com/gutsy/amd64/ms-sys/download](http://packages.ubuntu.com/gutsy/amd64/ms-sys/download)

---

### Post by kenanton on 2008-07-11
Thanks lswest your instructions worked perfectly!

---

### Post by lswest on 2008-07-12
> **kenanton said:**
> Thanks lswest your instructions worked perfectly!

Glad it was helpful for you!

---

### Post by lowtolerance on 2008-12-09
You're a lifesaver, lswest! I accidentally installed grub to /dev/sda1, and successfully corrupted my NTFS partition, just days after getting rid of the restore partition that HP was kind enough to include on my computer. 

The Vista Recovery Disk worked great, and very quickly. At first it sounded as though it wouldn't work, as it didn't recognize my drive as being NTFS formatted, but after I told it to fix startup issues, I was back on my feet and praising you. Thanks again for the info.

---

### Post by thegizmoguy on 2008-12-09
You may just want to mention that if you are dual booting like I am with Vista installed over XP and Ubuntu installed over Vista, that restoring the Vista boot loader will also bring you back to dual-booting again.

---

### Post by ceverhar on 2009-01-04
While all of this info was helpful, for some reason my computer is not showing my Vista installation.

bootrec /fixmbr worked fine, but bootrec /fixboot said "Element cannot be found" Also when I go to the recovery options my vista installation is not showing up, which it should (it has in the past when I had to do recovery). GRUB keeps giving me a loading error 17.

I also cannot boot into the Live CD (gives me I/O errors even though the drive is fine) or into Vista, so I have a computer with no bootable operating system.

---

### Post by lswest on 2009-01-04
> **ceverhar said:**
> While all of this info was helpful, for some reason my computer is not showing my Vista installation.

bootrec /fixmbr worked fine, but bootrec /fixboot said "Element cannot be found" Also when I go to the recovery options my vista installation is not showing up, which it should (it has in the past when I had to do recovery). GRUB keeps giving me a loading error 17.

I also cannot boot into the Live CD (gives me I/O errors even though the drive is fine) or into Vista, so I have a computer with no bootable operating system.

First off, have you checked the CD for errors (the option in the liveCD menu towards the bottom).  If it has errors, burning the image again at a slower burn speed should help.

If you can boot to the liveCD (try it in safe graphics mode which should be under F6 options I believe), can you post the output of ```
sudo fdisk -l
```  It may also be possible that the hard drive is dying, how old is the computer (roughly)?

@thegizmoguy: I added the info to the original post.
@lowtolerance: Glad I could help out :)

---

### Post by ceverhar on 2009-01-04
Well, I re-downloaded the live cd and burned it using the slowest possible speed. Can't boot, even trying the 'safe graphics mode'. Still getting I/O errors. However, after stating all these I/O errors, I can type commands in 'initramfs'.

I have 3 drives: 1. vista 2. ubuntu 3. media/important files

So would reinstalling vista fix my problem? At this point I'm just trying to rescue my computer. I think my problem is a boot loader (or something) isn't properly recognizing the operating systems loaded on my computer.

Thanks for all of your help.

---

### Post by lswest on 2009-01-04
I would boot to the Vista Recovery, go to "advanced" choose the recovery console and give in ```
chkdsk C: /F /R
``` to check for errors, then try the automated startup recovery application, then try restoring the bootloader again using the bootrec commands.  If it still doesn't work after the bootrec, also run ```
bootrec /ScanOs
bootrec /RebuildBcd
``` to scan for vista installs, and to create a new boot configuration data store for the bootloader, it shouldn't have any negative side effects, but I'm not 100% sure.  If that also doesn't work, a re-install may be in order.  However, the above commands should get your system booting into Vista again, and you can decide what to do from there.

If you want to get Ubuntu working, write down a few of the I/O errors so we can work with those if you'd like.

If you get Vista running again, I'd look into a hard disk diagnostics program to check your hard disk for errors.  Maybe someone else can suggest a few (I can't recall any off the top of my head).

---

### Post by ceverhar on 2009-01-04
OK, well the check disc didn't come up with any errors.  bootrec /fixmbr worked, bootrec /fixboot still shows "Element not found".

bootrec /rebuildbcd finds my windows install and asks "add installation to boot list?" I hit yes and it says "element not found".

I just tried the auto recovery, only errors are "system partition table ... fixed" I'm assuming thats the linux install. It seems my problem is with the bootloader. I would rather not re-install vista, but if push comes to shove, I'll do it.

My only fear is that reinstalling Vista won't fix the bootloader. Is that ligitimate?

---

### Post by caljohnsmith on 2009-01-04
<deleted>

---

### Post by ceverhar on 2009-01-04
The problem is I can't boot into ANY OS atm. Including a Live CD.

This is what happens when I try to boot from a Live CD:
BusyBox ...etc...loads then
(initramfs) [70.503367] end_request: I/O error, dev sr0, sector 1431624
[70.503425] Buffer I/O error on device sr0, logical block 357906

It pretty much continues with [xx.xxxxxx] changing in the beginning. The sector and logical block numbers do not change. I'm at a complete loss as to what I should do.

BTW, all my equipment is fairly new (~1.5yrs old) and works perfectly fine. (ASUS M2N-32 Sli Deluxe, 9800gt, all seagate hdds, 4gig ocz reaper ram, amd 4600+)

---

### Post by caljohnsmith on 2009-01-04
How about when you get the main menu after booting the Live CD, press F6 to add booting options to the kernel line, and add:
```
noapic nolapic acpi=off
```
And then try to boot the Live CD. If that doesn't work, you might want to try downloading the Ubuntu Gutsy Live CD or some other version/distro. I guess it's a trade-off between whether you want to put some more effort into troubleshooting your situation, or to simply reinstall Vista. Let me know if you have any success getting a Live CD to work though, and I can help you troubleshoot if you want.

---

### Post by lswest on 2009-01-05
> **ceverhar said:**
> OK, well the check disc didn't come up with any errors.  bootrec /fixmbr worked, bootrec /fixboot still shows "Element not found".

bootrec /rebuildbcd finds my windows install and asks "add installation to boot list?" I hit yes and it says "element not found".

I just tried the auto recovery, only errors are "system partition table ... fixed" I'm assuming thats the linux install. It seems my problem is with the bootloader. I would rather not re-install vista, but if push comes to shove, I'll do it.

My only fear is that reinstalling Vista won't fix the bootloader. Is that ligitimate?

Fixing the partition table might have solved the problem for Vista, or it may at least be found again (Vista recovery stuff won't touch ext3).  And if this doesn't work I would unhook the hard drive, take it to a different PC, plug it in, and backup whatever information you need to keep, and then re-install Vista (I can't see how that wouldn't fix it, I have the feeling that some of the boot sector is corrupt on Vista).

Also, if you want some more info about your hard drives, I would suggest you try to boot the [gparted liveCD]("http://gparted.sourceforge.net/livecd.php").  And about Ubuntu, trying the alternate install CD might help, I've had cases where it worked when the liveCD didn't (it's not much harder to use than the liveCD).

Sorry for the delay in reply, I was asleep (it's 10:57am in Germany now).

Good luck and let me know how it goes,
Lswest

---

### Post by ceverhar on 2009-01-05
A quick update on the situation. I was able to boot the 8.04.1 Live cd and launch the terminal and do the commands listed in the first post. All of that was succesful (no random errors). Now I'm getting Error 21, but I'm going to try Super Grub Disk and try to fix that.

---

### Post by lswest on 2009-01-05
> **ceverhar said:**
> A quick update on the situation. I was able to boot the 8.04.1 Live cd and launch the terminal and do the commands listed in the first post. All of that was succesful (no random errors). Now I'm getting Error 21, but I'm going to try Super Grub Disk and try to fix that.

Okay, good luck and fill us in later again!

---

### Post by ceverhar on 2009-01-05
By randomly using the various options in SGD, I got to the error "BOOTMGR is missing". So I put in the Vista boot disc and it asked me to "Press key to boot from CD" and I didn't so now I am currently in Ubuntu installing updates.

Next step is going to be to try to restore the Vista boot loader. At least I have A working OS atm.

Danke Schon lswest!

---

### Post by lswest on 2009-01-05
Gern geschehen :)

Glad I could help, good luck with restoring Vista.

Keep me posted!
Lswest

---

### Post by ceverhar on 2009-01-05
OK well, some progress. Used the info on this thread: [http://ubuntuforums.org/showthread.php?t=828862](http://ubuntuforums.org/showthread.php?t=828862) but I'm still getting "The volume does not contain a recognized file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted."

Looking for answers now. Trying the info in this guide: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Tried doing the Vista bootrec commands, messed up ubuntu, great....more I/O errors :( Well, once I get linux running again, I'm gonna try

```

Otherwise, edit your grub.conf (/boot/grub/menu.lst if using a debian alternative) file located in /boot/grub/ and add the following lines:

title Windows
root(hd0,0)  - You will need to update the hd0,0 part here to be relevant to your current setup.
makeactive
chainloader + 1
boot
```
Be sure to add the info above AFTER everything in the menu.lst

Update: Well that didn't work, but I did get back into stable Ubuntu 8.10 Wine is working properly (amazingly) and I'm able to access my Vista drive, all my files are there so I know it's not corrupted. Gonna check to see if there's a way to edit my boot loader another way. Pretty sure my problem is with the MBR.

Update 2: Fiddled with the menu.lst and Windows shows up as an option! Won't boot because......I'm not sure why lol.

Update 3: Ended up using gparted to delete my linux partition. BOOTMGR still isn't present, loading the Vista recovery to try to fix the problem with the steps mentioned at the beginning.

Update 4: Still stuck. I think if I found a boot loader that could be installed off a live cd, it would fix my problems.

Update 5: Ran the Vista repair option with the linux drive unplugged. For the FIRST TIME it recognized my Vista installation. Did an auto repair, nothing. Ran the /fixmbr and /fixboot and they BOTH worked (needless to say I ran a lap around my house cheering because I've spent 2 days trying to get /fixboot to work), but alas, still nothing. Trying the auto repair option now, hopefully that fixes my problems.

Update 6 (5 min later): HUZZZAAAAHHHHHH!!!!!! I FIXED IT! (lots of yelling, jumping and cheering was in order) I ran the Auto Recovery in the Vista setup and fixed my problem.

Summary of how to fix linux installed over Vista on separate hard drives:
1) Removed linux with gparted
2) Unplug all hard drives but the one containing Vista
3) Run
```
bootrec /fixmbr
bootrec /fixboot
```
4) Restart, run Auto Repair Utility
5) Restart and let it start normally

---

### Post by lswest on 2009-01-06
Congratulations!  Glad you got it sorted.  I've had a dual setup on my computer for years (2 hdds) and no problems with restoring XP, so it never even crossed my mind to try to remove Ubuntu.

Glad you got it working again,
Lswest

---

### Post by Tosa on 2009-01-07
I've busted my XP and have to reinstall it. I run Kubuntu 8.10 but I don't have 8.10 Live CD, I've got 7.10 I think.
So my question would be could I use 7.10 Live CD to fix grub on an 8.10 installation?

---

### Post by lswest on 2009-01-07
If you use supergrubdisk you should be able to restore GRUB.  7.10 uses an older version of GRUB (I think).  It would be a temporary solution to get back to Kubuntu and to run the grub commands from your installed Kubuntu system.

Feel free to ask any more questions you may have,
Lswest

---

### Post by halovivek on 2009-01-08
Thank you so much for posting since using your thread idea only i have recovered the ubunutu and vista ultimate.

---

### Post by lswest on 2009-01-08
I'm glad you found it useful!

---

### Post by dspisak on 2009-01-08
Hello.  I have a single hard drive with XP, ubuntu 8.10 32-bit, and ubuntu 8.10 64-bit.  I want to remove the  ubuntu 32-bit OS and its partition.  Ubuntu 32-bit is the last system loaded, so its GRUB appears at startup.  Running sudo fdisk -l returns:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3442    27647833+   7  HPFS/NTFS
/dev/sda2            4463       14691    82164442+  83  Linux
/dev/sda3           14692       14946     2048287+  82  Linux swap / Solaris
/dev/sda4            3443        4462     8193150   83  Linux
Partition table entries are not in disk order

The actual disk order is:
sda1 (XP)
sda4 (ubuntu 32-bit)
sda2 (ubuntu 64-bit)
sda3 (linux swap).

Thus, I want to delete sda4.  Can I simply use GParted to remove sda4 (and GRUB for the 64-bit OS "appears") or do I have to restore the XP booloader?  I prefer to use GRUB.  TIA.

---

### Post by ceverhar on 2009-01-09
Try using GParted to remove sda4. You should also be able to reformat that partition into the format that you want (ie NTFS, etc). If your GRUB is working now, then it shouldn't be a problem.

---

### Post by lswest on 2009-01-09
You'll need to remove sda4, then either resize the partition or do what you want to do with the new free space, and then you should just have to restore GRUB for your Ubuntu 8.10 64-bit system using the instructions posted at the beginning of this thread.

Then, once that's done, you may need to set up an entry for your XP system, so I would recommend saving your current menu.lst onto a USB drive or the other partition, so you can merely copy and paste the XP entry to your new menu.lst on the 64-bit system.  If you try to boot to it and it reports errors, let us know.

Good luck,
Lswest

---

### Post by halovivek on 2009-01-09
> **lswest said:**
> I'm glad you found it useful!

Really thanks for the post and i took print out and i have this.
otherwise i could not able to do some office work in vista.

---

### Post by dspisak on 2009-01-09
Your instructions worked without any drama.  Thank you.

To be safe I used KGRUBEditor to delete any reference to the 32-bit OS in each partition (Each partition appeared to have a separate GRUB).  Then I used GParted to remove the 32-bit partition.  Upon reboot I used the "try ubuntu without changing your computer" option on the ubuntu install CD to open a terminal and apply your code.  It worked like a champ.  I re-allocated the space to the 64-bit OS and both ubuntu and XP can be booted.

---

### Post by lswest on 2009-01-10
Glad that my instructions were useful for you as well!

And thanks to anyone who has thanked me in this thread, it's nice to know I've been helping :)

---

### Post by Tosa on 2009-01-11
> **lswest said:**
> If you use supergrubdisk you should be able to restore GRUB.  7.10 uses an older version of GRUB (I think).  It would be a temporary solution to get back to Kubuntu and to run the grub commands from your installed Kubuntu system.

Feel free to ask any more questions you may have,
Lswest

Thank you.

I did use 7.10 CD and got kernel panic when rebooted. Well, I was in panic too! 
After rebooting in recovery mode everything went fine.

---

### Post by lswest on 2009-01-11
> **Tosa said:**
> Thank you.

I did use 7.10 CD and got kernel panic when rebooted. Well, I was in panic too! 
After rebooting in recovery mode everything went fine.

I wasn't sure if it would work, but I'm glad you were able to get it working again!

---

### Post by LasseNC on 2009-01-11
I had Kubuntu and XP running with GRUB, worked fine.

Then I reinstalled XP so the GRUB loader is gone. How is that restored? I couldn't see how that was done.

---

### Post by lswest on 2009-01-11
On the first post the section that you would need is this:
> **lswest said:**
> For GRUB restore to MBR:
boot to the LiveCD (this is the easiest way IMHO) and then start a terminal (applications-->accessories-->terminal)and type
```

sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit

```
where the (hd?,?) and (hd?) corresponds to the output of find /boot/grub/stage1 (first time round the (hd?,?) stands for the drive (hd?) and the partition (,?) at which Ubuntu (or any Linux) is located, and then the second time round (hd?) just stands for the drive, for the MBR).

---

### Post by thismango on 2009-06-08
I'm having similar problems. It's driving me up the wall.
The situation is as follows: no version of Linux I've tried will install successfully on my machine (I've tried Ubuntu 8 and 9, and Linux Mint). I'm trying to restore XP so at least I have an OS of some kind.

I don't have an XP CD, only my ASUS restore CD which doesn't have the recovery console. So I can't use *fixmbr*.

I can run the Jaunty Live CD but can't connect to the Internet so I can't get ms-sys.

The only option I seem to have is an MS-DOS prompt from my Windows restore CD. Does anyone know how to restore Windows boot sector from MS-DOS?

---

### Post by lswest on 2009-06-08
The MS-DOS prompt should let you use fixmbr.  I can't understand why ASUS wouldn't have that on a command prompt on a recovery disk.

Have you tried it?

---

### Post by hackersmovie on 2009-08-01
So, I was editing my GRUB menu after the latest Ubuntu update and now when I boot all I get is a GRUB command line!

When I use "find" to find my Linux kernel it reports back with 

```
(hd0,5)
```

When I try to boot that device it reports back with a kernel panic and instructs me to edit the 


```
"root="
```

entry with and appropriate partition. It reports back these possible partitions:

```
sda6
sda5
sda1
sda2
```

Not in that particular order. By size of partition, I suspect Ubuntu is on sda6 but when I edit "root=" to boot from sda6, it still gets a kernel panic.

Now, I also have XP SP3 install on this machine and was able to boot xp with:

```
unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot
```

This is most important as I use XP for company use and have very sensitive information.

So as it stands XP is working and Ubuntu is not.

My question is:

How can I restore GRUB to be useful in selecting my OS's again?

Thanks in adavance,

"Newbie" - Hackersmovie

---

### Post by bodhi.zazen on 2009-08-02
Grub is easy to restore, but you need to know which partition is your Ubuntu root.

I suggest you boot the live (desktop) ubuntu CD and first identify the root partition.

Then you can restore grub from the live CD as well

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by pro003 on 2009-08-02
another easy way is to download and use super grub disk, it's image about 4mb and you simply burn it to cd and boot from it, the procedure is simple, it guides you all the way...

---

### Post by lswest on 2009-08-08
I agree with the above two posts, but offer one last suggestion.  If the error firmly states the root= section, it will be in the kernel entry, and it should be either root=UUID=<UUID of root disk> or root=/dev/sdaX (where X is the correct number).  At least, I believe the UUID entries are like that in Ubuntu, in Arch it reads root=/dev/disk-by-uuid/<UUID>, so maybe another ubuntu user could post which of the two is used by grub.

Hope that helps,
Lucas

---

### Post by pleoscalete on 2009-10-12
thought it'd be polite to say hi everyone! since this is my first post on the forum. 
i suppose all of you heard about windows messing up grub at install. well i have a different version. i had an older ubuntu, 8.. something, don't really remember. i installed a windows xp 64 version and naturally it messed up my ubuntu. because the windows also got messed up i decided to reinstall it. formated everything, nice and clean. so i set up my windows nicely and than decided to reinstall ubuntu as well. downloaded the 9.04 version and set it up un the old ext3 partition which i also formated so that everything'd be clean. now my problem is that even though the boot menu has a windows xp 64 entry when i click it it says that, and i quote: 
<WINDOWS ROOT>\system 32\ntoskrnl.exe is either missing or corrupt. please reinstall the specified file.

i've looked it up and i supppose it's about a messed up the mbr or something. i'm guessing i can't manually reinstall the specified file from the windows cd somehow and since i couldn't find a topic regarding my issue arround here i was curious if you guys ever came across anything like this. any help is greatly appreciated thanks

---

### Post by pro003 on 2009-10-12
i would advice you to reinstall i.e repair win xp first and then reinstall grub, by leaving ubuntu installation intact. you can both do fine and there are loads of instruction available throughout the internet.

your winxp installation is definitely gone, that's for sure.

---

### Post by lswest on 2009-10-12
> **pleoscalete said:**
> thought it'd be polite to say hi everyone! since this is my first post on the forum. 
i suppose all of you heard about windows messing up grub at install. well i have a different version. i had an older ubuntu, 8.. something, don't really remember. i installed a windows xp 64 version and naturally it messed up my ubuntu. because the windows also got messed up i decided to reinstall it. formated everything, nice and clean. so i set up my windows nicely and than decided to reinstall ubuntu as well. downloaded the 9.04 version and set it up un the old ext3 partition which i also formated so that everything'd be clean. now my problem is that even though the boot menu has a windows xp 64 entry when i click it it says that, and i quote: 
<WINDOWS ROOT>\system 32\ntoskrnl.exe is either missing or corrupt. please reinstall the specified file.

i've looked it up and i supppose it's about a messed up the mbr or something. i'm guessing i can't manually reinstall the specified file from the windows cd somehow and since i couldn't find a topic regarding my issue arround here i was curious if you guys ever came across anything like this. any help is greatly appreciated thanks

You should be able to copy the file by entering this command from the recovery console of the XP install disk:
```
copy d:\\i386\\ntoskrnl.exe c:\\windows\\system 32\\
```

I am assuming here that d:\ is your dvd drive.

Two things:
1) not sure anymore if it needs to be dual backslashes, try it both ways (single and double), if double fails to work.
2) You may need to look for the cd's location of ntoskrnl.exe by using cd and the dir command (dir=ls for windows systems), as I doubt very much the 64bit CD would store the files under I386 (but I've got no 64bit disk to check on).

Also, you can just repair the bootloader using what was explained above and then restoring GRUB after that (it's more work though).

Hope that helps,
Lswest

P.S. If you do get it to boot again, I recommend, once logging in, to open the run window and enter:
```
sfc /scannow
``` which will check all windows files for consistency, and if corrupt, copy the files from the XP CD.

---

### Post by alcapone-g on 2009-10-13
Thanks for the information.
I had a problem where I had ubuntu restored without grub boot loader. I did not know how to reinstall only boot loader and I lost a lot useful information by rebuilding ubuntu from installation disk which erased my original ubuntu partition.

---

### Post by lswest on 2009-10-14
To the above post: if you make a separate partition for /hone you won't lose that info if you re-install, just set the partition to the /home mount point without formatting it.

Glad you found the info useful,
Lswest

---

### Post by Gen2ly on 2010-02-27
> **bodhi.zazen said:**
> Very cool thread.

If I may , this is how to restore the WINDOWS boot loader **[color=blue]FROM LINUX[/color]**

From the Ubuntu Live CD:

[list=number][*]Boot live CD, open a terminal.


[*]Enable The Universe repositories (System->Administation->Software Sources : tic "Community maintained Open Source software (universe)"


[*]Install  ms-sys
		```
sudo apt-get update && sudo apt-get install ms-sys
```


[*]Restore MBR

[list][*]Set up your windows partition :
		```
ms-sys -p /dev/sda1
```
[indent]_Note_: change /dev/sda1 and /dev/sda to your windows partition and MBR

```
ms-sys -p /dev/<drive>
```
<drive> = your windows hard partition (/dev/hda1 or /dev/sda1)[/indent]

[*]Write to MBR :

	[list][*]2000/XP/2003 :

				```
ms-sys -m /dev/sda
```

		[*]DOS/Windows 98/NT : 

				```
ms-sys -w /dev/sda
```[/list]

[indent][color=darkred]ms-sys -p = write to windows partition[/color]

[color=green]ms-sys -w = write Microsoft DOS/Windows NT to MBR[/color]
[color=blue]ms-sys -m = write Microsoft 2000/XP/2003 to MBR[/color][/indent][/list][/list]


How to : [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)
man page : [http://linux.die.net/man/1/ms-sys](http://linux.die.net/man/1/ms-sys)

----------

From Knoppix :  

boot Knoppix, open a terminal and enter :

sudo install-mbr /dev/hda

[color=blue]I know the[/color] [color=brown]Ubuntu[/color] [color=blue]method works with every version of windows **EXCEPT VISTA** (it may work with Vista, I have not tested it), I have not tried Knoppix[/color]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]*bodhi.[/color][color=darkgray]zazen[/font][/size][/color]*

Just thought I'd add here.

The reason that this works is because these commands will add the Windows bootloader **and** the partition table.  For a successful boot, the BIOS will look at the first recognized (or specified) disk for a bootloader program and also the partition table.  Both of these can either be on the first sector of the disk (MBR), or on the first sector of the first partition (most BIOS's are only able to detect them in these two places).  For the most part, using these two commands you will likely be able to restore your Windows partition boot capability and have your disk recognized again.  The only thing to add here is that sometimes boot sectors can become corrupted.  This can happen in numerous types of circumstances but I most often see it when one accidentally installs GRUB to the Windows partition (where **Windows** installs it's bootloader and partition table).  I've seen this mostly with Windows XP installs so I think that later versions of NTFS may help avoid this.  If the boot sector is corrupt, you will need to repair it.  This repair can be done with the Vista Recovery Tool (not sure about others), or (if you don't have the disks around) TestDisk is a good possibility.  If you need to do this with TestDisk, read more [here](http://ubuntuforums.org/showthread.php?p=6716154#post6716154)).

Good post bodhi.

---

### Post by aqk on 2010-03-04
Regarding your advice about booting off the XP CD, and entering the Recovery Console:
Many of us (including me!), alas have that moronic E-machines "PC Angel" recovery method, and it does not let us perform this sort of recovery.
  I have even browsed the *%#* e-machines install CDs (count: FOUR of them!)
and cannot locate fixboot.ex* anywhere.
I believe they have removed this valuable utility.
If you can point me to any site that has  the genuine "fixboot" and "fixmbr" utilities for DLing, I'd appreciate it.

---

### Post by pcdock on 2010-03-17
I had XP on C: and Win7 on D:
Wiped D: and ran XP's Recovery console then "fixmbr" then "fixboot"
XP booted just fine
Went to install 9.10 Karmic to D: and it lists that partition as "Windows 7 Boot"
I dont understand? Is this because Win7 stamped D: as nt60 format or whatever?

---

