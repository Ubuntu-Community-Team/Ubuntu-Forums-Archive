---
title: "&quot;GRUB Hard Disk Error&quot; after installing 8.10 and rebooting"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by chevweez on 2008-11-09
I am relatively new to Linux and decided to install the new version of Ubuntu today (good bye XP).  Before burning the Ubuntu CD I checked the md5 hash and before installing I checked the burned CD using Ubuntu.  Both were fine.  

Before installing, I ran DBAN ([http://www.dban.org/](http://www.dban.org/)).  The install of Ubuntu went smoothly I chose to keep the default partitioning scheme, which is the whole drive running just Linux - no dual booting - nothing fancy.  After the install completes, I take the CD out, and it restarts.  After my POST, I am left with just:

GRUB Loading stage1.5.
GRUB Hard Disk Error

That's it.  Doesn't boot into Linux.  Figuring something quirky went wrong during the install, I decided to redo it from the start (not like I have any data to lose).  So I DBANed and installed again.  Same results.

Searching online I found here: [http://en.wikipedia.org/wiki/Western_Digital_Raptor#WD740](http://en.wikipedia.org/wiki/Western_Digital_Raptor#WD740)  that the newer version of my HD is "Linux libata drive blacklist[ed]" but I have the older WD740GD, so I don't think that's it.

Thinking it's a GRUB issue I followed the main instructions given here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)  Everything went fine - said it succeeded, but when I try to boot to the HD same results above with the Grub error.

What should I do? :confused: Should I try out a different boot loader, like LILO, and if so HOW?  Should I redo the install but manually make the partitions using some special guidelines?  If I really don't want to have to put Windows back on.  Advice would be greatly appreciated.  Thanks!

---

### Post by alienexplorers on 2008-11-09
First off reload, but don't run dban.  Let Ubuntu take care of formatting the partitions.  Make sure you select ext3 partition type. When it is done completely it will tell you to remove the CD from your drive and hit a key to reboot.  See what happens.  If you still get the grub error then you can boot the live CD and use it to download super grub disk.  This disk can fix most grub errors.  Burn it to disk using gnomebaker.  Gnomebaker should be in the repository.  Use sudo apt-get install gnomebaker to get it.  Run the super grub disk by rebooting your system. Select to repair the MBR.  Reboot and see if Ubuntu loads.

---

### Post by caljohnsmith on 2008-11-09
How about booting your Live CD, opening a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by chevweez on 2008-11-09
Since it's quicker than reinstalling, I've done what caljohnsmith said to do.  After running 
```
sudo fdisk -lu
``` 
the output was:
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000520b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   139219289    69609613+  83  Linux
/dev/sda2       139219290   145211534     2996122+   5  Extended
/dev/sda5       139219353   145211534     2996091   82  Linux swap / Solaris
```
After running
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
the output was:
```
GRUB
```
And after running
```
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
the output was:
```
0000000 ff00                                   
0000002
```

As far as reinstalling without first dban-ing, I can do that but it shouldn't make much of a difference since all dban does is write over the HD with random bits [but it doesn't hurt to try I suppose].  The other suggestion from alienexplorers about using super grub disk does sound like a potentially good idea but my Ubuntu CD is a CD-R not a CD-RW, so I'd have to go buy a CD-RW and then redownload and burn it (which I'm not opposed to if it comes down to it)...it's just that I live out in the boonies (not near a store) and the last time I downloaded the iso it failed after 2 hours and, after choosing a different mirror, it took 3 hours to download.

Thanks so much for the help so far!

---

### Post by caljohnsmith on 2008-11-09
According to those "dd" commands you ran, Grub appears to be correctly installed to the MBR (Master Boot Record) of sda, but getting a "Hard disk read error" on start up I believe means that the Grub stage1 file in the MBR is not even loading the stage1.5 file after the MBR. So just to make sure Grub is properly installed to sda, please post the output of the following commands:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then reboot, and let me know if you get the same Grub error.

---

### Post by chevweez on 2008-11-09
Here are the results:
```
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
```

I'll reboot now and let you know what happens.  Just so you know, I have previously run that series of commands (it was the directions I noted in my first post through a link to another Ubuntu forums thread).

---

### Post by chevweez on 2008-11-09
Ok, I rebooted.  Same results.  After POST I just get:

GRUB Loading stage1.5.
GRUB Hard Disk Error

:(

---

### Post by chevweez on 2008-11-09
Dp you think this is a hardware error or a software(grub) error?

It seems like grub is present and accounted for, but just not able to run...leading me to think it's a hardware problem.

BUT, when I had Windows on it I was able to defrag, dban ran fine, and the ubuntu partitioning, formatting, and installing never complained (which I think some or all of those would say something if there was a physical problem with the HD)...leading me to think it's a software/grub problem.

Seems so weird...

---

### Post by caljohnsmith on 2008-11-09
Since reinstalling Grub still gives that Hard disk read error, I think you might have an issue with how your HDD is set up in BIOS. Also, how old is that HDD? It's only 75 GB, so I wouldn't be surprised if that's an older drive. It would probably be a good idea to run a HDD diagnostic test on it to make sure its not failing. 

Do you have internet access from your Live CD? If so, how about doing the following from your Live CD:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
sudo smartctl -H /dev/sda
```
And please let me know the results. :)

---

### Post by chevweez on 2008-11-09
The HD self-test is going right now.  Says it will take 37 minutes.  I bought the HD in Feb. of 2004 and it is a WD740GD not the WD740ADFD.  At the time, it was the highest capacity SATA drive available at 10K rpm and I wanted the best for the computer I was building...now 74GB seems so small, LOL.

I'd have to take the HD out to be able to see the actual date it was manufactured, though.  

I'll post the results when it's done running all the commands.

Thanks so much!

---

### Post by chevweez on 2008-11-09
Ok, I've attached the files for the HD status before and after the test.  The last time I checked it while it was running the self-test using the command 
```
sudo smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
it returned:
```
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever
```
When I ran the command
```
sudo smartctl -H /dev/sda
```
it returned:
```
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

So the HD is ok, right?

---

### Post by caljohnsmith on 2008-11-09
OK, that's good news, looks like your HDD is fine. I think your problem may be BIOS related, but I have one more idea we can try to see if it makes any difference:
```
sudo grub
grub> root (hd0,0)
grub> install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst
grub> quit
```
Please post the output of the above commands. What those commands do is install Grub to the MBR again but without installing the stage1.5 file; instead Grub will point directly to your stage2 file. Let's see if that makes any difference. :)

---

### Post by chevweez on 2008-11-09
Ok, when I ran those commands it didn't print any output afterwords, just returned the prompt.

This time when I tried to boot to the HD, right after the POST, it said:

GRUB Loading stage2...
GRUB Hard Disk Error

So, basically the same error before but a different file.  I don't know what I could change in the BIOS (if anything).

---

### Post by caljohnsmith on 2008-11-09
I read in another thread once where someone fixed their Grub "Hard drive read error" by upgrading their BIOS; if you can do that, that would probably be the best thing to try at this point. If that's not possible, then I would recommend going into your BIOS and looking for settings related to your HDD like "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. and changing them one by one, rebooting, and seeing if that makes any difference. I would also recommend writing down whichever settings you change so you can always revert back if necessary. Good luck, and let me know how that goes.

---

### Post by chevweez on 2008-11-09
Well, I don't have many options in the BIOS regarding my HD.  The only setting I have for it is to enable or disable "OnChip Serial ATA".  In fact, it won't even display what my HD is.  The first page that would be the page to list that info only includes the data on the IDE channels' master and slave (which are my 2 CD drives) and the floppy drive.  I'm guessing it's just too old to show data on a SATA HD.  Other than the enable/disable SATA option, I have the option to enable/disable either IDE channel, but that is independent of the SATA option (so it's not like it's one or the other).

I will be looking into upgrading my BIOS.  I never done that before but I have MB with Dual BIOS, so if something goes horribly wrong the other BIOS will be intact.

Fingers crossed...I'll let you know how it goes.
Thanks for your help :)

---

### Post by chevweez on 2008-11-09
Well, I found the webpage from my MB manufacturer that lists the BIOS upgrades (and there are some there) but they are all exe files.  I downloaded the latest one and tried double-clicking it to run (hoping wine was on there an would figure it out) but it just gave me an error and didn't run.  So I'm going to put the exe on my external HD, boot the computer with a Windows 98 SE boot disk, try to access the external drive, and run the exe.  I'm not optimistic it will work....

If it does, I'll find it somewhat humorous (you know, needing Windows to be able to run Ubuntu).

---

### Post by caljohnsmith on 2008-11-09
Is that .exe a full GUI program, or just a DOS type command line program? If it's just a command line program, you could download a Windows XP Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip") and see if maybe you can run that .exe from the "recovery console", a.k.a command line from that CD.

---

### Post by meierfra. on 2008-11-09
Maybe this helps:

[http://ubuntuforums.org/showthread.php?p=6133093]("http://ubuntuforums.org/showthread.php?p=6133093")

---

### Post by chevweez on 2008-11-09
Ok, well it turns out that I can't see my USB-connected external HD, but I can see the CD drives.  So I went rummaging through the basement and found an old CR-RW disk with stuff I don't need on it anymore.  I'm erasing it right now (since I can't seem to add to it) and then will but the exe on it and see what happens.  I don't know if it is GUI-based or not.  This is what I'm working with:
[http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1667](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=1667)

If this doesn't go then I'll start using the suggestions that have recently been posted.  Thanks!

---

### Post by chevweez on 2008-11-09
I'm having problems with formatting the CD-RW.  I'm gonna have to dig through the basement to find another CD (I don't have blanks lying around) and I'm going to take a break (food!).

I haven't given up yet!

---

### Post by chevweez on 2008-11-09
I don't know for sure but I think the exe is a GUI program.  When I try to run it from the command prompt inside the Windows 98 SE boot disk, I get:

This program must be run under Win32

So if it must be through a GUI and double-clicking the file in Ubuntu only returns an error, then I can't do it through Ubuntu?  I mean is there another way to invoke wine? (I assume it is included on the live CD but I don't see it listed under Applications)

---

### Post by caljohnsmith on 2008-11-09
Have you tried the link that meierfra gave? That tutorial gives a method for either making a floppy or CD capable of flashing your BIOS. I really doubt that the .exe you got from the manufacturer's website is a GUI program, but maybe it is. You might be able to tell just by its size, because if it is really small, I doubt it has a GUI.

---

### Post by chevweez on 2008-11-09
Ya, I was just following what the link from meierfra said to do.  The link in that thread takes you to a page to download bios.rar which I did but when I try to open it in Ubuntu using Archive Manager it says "Archive Type Not Supported."  I assume that if I could open the rar file that there would be a place for me to include my exe file in there???

The exe is 384 KB in size.

---

### Post by chevweez on 2008-11-09
I see now that the first post to the thread meierfra gave talks about making that floppy or CD for flashing your BIOS.  I'm just not sure I get how it will work.  I mean if I follow those directions for making a CD to do it, then will the CD be bootable; do I boot to that CD?  Also, it talks about running it using the commands given by BIOS manufacturer, but I don't have any commands?  Should I have commands?  I've previously given a link to page for my MB, which is made by Gigabyte, and the BIOS is by Award.

---

### Post by glennric on 2008-11-09
If flashing your bios doesn't help, or if you just want to try another idea let me know.  I had a problem similar to yours, and I just had to use some of Hardy's grub stage1_5 files to fix the issue.  The Intrepid files will not work for me no matter what I do.

---

### Post by chevweez on 2008-11-09
Ok, I've been following these directions for creating a CD to flash my BIOS:
[http://ubuntuforums.org/showpost.php?p=1871362&postcount=1](http://ubuntuforums.org/showpost.php?p=1871362&postcount=1)
But when I run the command to unzip the exe file I get:
```
Archive:  /home/ubuntu/Desktop/motherboard_bios_ga-7vt6001394_f7.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/ubuntu/Desktop/motherboard_bios_ga-7vt6001394_f7.exe or
        /home/ubuntu/Desktop/motherboard_bios_ga-7vt6001394_f7.exe.zip, and cannot find /home/ubuntu/Desktop/motherboard_bios_ga-7vt6001394_f7.exe.ZIP, period.
```

I have to say this is rather frustrating.  Glennric, I think it might be a could idea to try want you said and use Hardy's files, but I don't know where to begin with doing that.  Do you mind telling me where I need to go to the files and which files I need?  Thanks!

---

### Post by glennric on 2008-11-09
Yeah, just a sec and I will locate the deb link for you.

---

### Post by glennric on 2008-11-09
Actually it is easier to just give them to you.  I have attached a tar ball below.  Then we have to get these into your boot/grub directory.  Are you working from a live cd?

---

### Post by glennric on 2008-11-09
If you are in a live cd you will need to mount your root partition.  To do this do
```
sudo mkdir /mnt/root
sudo mount /dev/sda1 /mnt/root
```
Then extract the previously attached files where they need to go with
```
sudo tar xzvf stages.tar.gz -C /mnt/root/
```
Then reinstall grub with
```
sudo grub
grub> root (hd?,?)
grub> setup (hd?)
```
I think you did that last part before so you should know how to fill in the ?'s.

---

### Post by chevweez on 2008-11-09
Ok, I've extracted the folder/files.  Yes, I'm working off a live CD.  I also have a secondary PC (not mine) running XP if I need it.  So do I just copy paste those files over the ones on the HD?

---

### Post by glennric on 2008-11-09
Yeah, replace the existing files in /boot/grub with the ones from the tar ball.  You can do that with the commands I gave you in the last post.

---

### Post by chevweez on 2008-11-09
Sorry, when I was typing that post you must have posted the list of commands, so I missed that.  I just ran the commands and will be restarting to see what happens.  Oh, the suspense!!!

---

### Post by chevweez on 2008-11-09
:( Nope, that didn't fix it.  I got the same error of:

GRUB Loading stage 1.5.
GRUB Hard Disk Error


Maybe I should try a different bootloader???....or another way to flash my BIOS???


...I could put XP back on just to flash the BIOS but it seems a bit ridiculous.

---

### Post by glennric on 2008-11-09
You could try installing lilo.  I don't know much about how to do that though.  Someone else could probably help you.  Sorry my idea didn't help.

---

### Post by chevweez on 2008-11-09
No no, thank you so much.  You were very helpful.  I was thinking of installing the previous release of Ubuntu, but if those are the grub files from it and they don't work then you saved me the headache of going through another install that wouldn't succeed in the end.

I also thought about using LILO, which I don't now how to get, install, and work on Ubuntu, but some of things I was seeing online made it seem like people who tried to replace grub with lilo had problems with files or settings from grub still being present making lilo not work.  I think I might need someone who has gotten LILO to work properly on Ubuntu specifically, not another distro.

---

### Post by chevweez on 2008-11-09
To satisfy my curiosity and possibly solve the problem.  I'm going to put XP back on, flash the BIOS, do a quick dban, reinstall Ubunto 8.10 and see what happens.  It's going to be awhile before I'll have news to post, but I'll be back.

In the meantime, if anyone out there reads this thread and knows how to safely get LILO on Ubuntu, please post to or keep track of this thread...PLEASE...THANK YOU!  :)

---

### Post by barney385 on 2008-11-09
Here's a thread:

INSTALL LILO BOOT LOADER TO UBUNTU PARTITION

[http://ubuntuforums.org/showthread.php?t=96920](http://ubuntuforums.org/showthread.php?t=96920)

---

### Post by chevweez on 2008-11-10
Well well well, quite a lot has developed for me since my last post and none of it is very good.  I put XP back on just to be able to flash my BIOS.  When in XP, I tried running the newest upgrade for my BIOS (version 7), which mind you I got from my MB manufacturers webpage for my MB, it does open a utility but gives the error that my chipset is not supported (wtf :mad:) then I hit enter for the error and it says to make sure my flash is not protected, and I hit enter and it says it is unable to flash.  So then I systematically tried every single BIOS upgrade in descending order from the newest.  Same results with every one.  

Hmmmm, so maybe their is some way to "write/flash protect" my BIOS.  Checked the MB, didn't see anything.  Dug out the MB's manual, nope no jumper for that.  But the manual mentions using a software tool given on the CD for the MB called @BIOS.  So I install that and follow the manual's directions for updating the BIOS via the internet but it doesn't list any servers to retrieve an update from. (weird)  So I tried running it again, this time telling it to browse locally for the file to flash the BIOS.  I gave it the newest version, which finished 100% according to the software.  I restart and during the POST I notice it printed the version ending in F7 (so it took the update) and in bold letters that an error occurred and mentions my CMOS settings.  So I press 'Delete' to go into setup, where I am prompted for a password (like always, I have it set to ask for the password on every boot and setup).  But I typed in my password four types and every time it said it was incorrect.

Ok, something is WAY messed up.  To reset the password, I took the CMOS battery out for a bit.  Plopped it back it, restarted, and this time the version says it's F1 and I go into XP like nothing ever happened.  Well, that means it's using the backup BIOS cuz I fried the main BIOS with the update.  According to the manual (if taken literally) I can't reflash the corrupted BIOS with it's previous version (which I saved to the desktop in XP before fooling around) because it is set to always flash the non-corrupted BIOS.  There is so much bad English in the manual that it could be interpreted differently, but I am SO done.  I'd rather have an outdated BIOS with no grub than my only PC turned into a big brick.  So flashing the BIOS is out of the question now.

I haven't put Ubuntu 8.10 back on yet since I know grub won't work, I'd like to use LILO instead, and I'd rather to it "correctly" the first time (i.e. don't install grub only to remove it later).   Thank you barney385 for providing that link.  Since my circumstance has changed, though, it doesn't apply as well to me.  In case it can help someone else later reading this, I found these (seemingly great, yet I haven't tried) directions for going from grub to lilo in 7.04:
[http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html](http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html)

From what I see online, it appears the only way to install Ubuntu with LILO (never any grub) is with an "Alternate CD", but I don't see anyone go into further detail on the matter.  Is it so straightforward when installing via the Alternate CD, that I wouldn't need directions to get LILO on?

Anywho, I'm downloading the iso now (2.5 hours to go) and I'm going to bed.  Thanks for everyone's help so far!!!!

---

### Post by caljohnsmith on 2008-11-10
I'm really sorry to hear you didn't have any success upgrading your BIOS despite all the trouble you went through, and it's a shame the whole thing has turned into such a complicated saga to get Grub working. If you haven't yet wiped your Windows off the HDD, I would recommend that we try "Grub4DOS" within your Windows and see if that works, because Grub4DOS is a lot more robust than the legacy Grub that Ubuntu uses; Grub4DOS is also still being developed and improved, whereas the legacy Grub project stopped development back in 2005 or so. And unlike what its name implies, you can use Grub4DOS from a linux ext3 partition, and not just an NTFS partition, so you could easily use it within the Ubuntu partition. I think it's at least worth a shot.

How about downloading the [Grub4DOS package]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip") and also the ["Grubinst" package]("http://internap.dl.sourceforge.net/sourceforge/grub4dos/grubinst_1.0.1_bin_win.zip") into Windows, unzip them, and put the "grldr" from the Grub4DOS package (don't use the one from the Grubinst package) into your Windows root directory C:\. Then run the grubinst_gui.exe to install Grub4DOS into the MBR. And lastly, save the following menu.lst to your C:\ root directory also:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

#splashimage=(hd0,1)/boot/grub/splashimages/firework.xpm.gz
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL 

title		Windows XP
root (hd0,0)
chainloader /ntldr

```
After that, reboot, and see if it works. :)

---

### Post by chevweez on 2008-11-10
Aww, thanks caljohnsmith for all the help, but I've already wiped the drive.  It currently has no partitions, no formatting, and no OS.  But when I installed XP it forced me to overwrite Ubuntu anyways, since it wasn't formatted in Fat32 or NTFS.  I really don't want to give up on Ubuntu - it seems like a great OS all around.  I've decided if I can't get Ubuntu working with LILO then I'll try another Linux distro before giving up completely and reverting to XP.

I really appreciate all the help you have provided.  I'm sure if my "grub issue" was more normal that your suggested commands would have fixed it. :)

---

### Post by chevweez on 2008-11-10
Well, I'm exceeding pissed at the moment.  Following the online directions for installing Ubuntu using the Alternate CD resulted in never getting prompted for choice of bootloader, so it went with grub which didn't work (of course).  Tried it one more time, this time choosing to manually partition the drive in hopes of getting asked to pick a loader there.  Never was I asked.  Never did it say what bootloader it was going to use.  Realizing I shouldn't go farther, I chose 'Go Back' in the install and it showed me like a table of contents of what it was going to do (never previously seen by me).  I see down the list it has Install Grub above an entry for Install LILO - I go down and select Install LILO and then it goes back to making partitions.  When the install finished, after the reboot, LILO loaded seeming successfully but then asks for my login and password, which I wasn't prompted for this time.  Yes, every other time I installed Ubuntu I entered that in but this time I was asked during the install.  Maybe I ****** it up by selecting 'Install LILO' when I did but I didn't think I'd ever get the chance to later.  It would have been amazing to have directions for how to get LILO on using the Alternate CD (yes, I googled).

I'm going to try Mandriva next (need to figure out what bootloader it uses by default first).  Thanks to those helping me through my grub problems.  I truly hope no one new to Ubuntu ever tries getting LILO on without grub first...all I can say is 'Pain in the a**!'

---

