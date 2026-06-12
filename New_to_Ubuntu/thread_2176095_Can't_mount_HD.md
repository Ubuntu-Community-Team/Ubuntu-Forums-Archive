---
title: "Can't mount HD"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by faisal2 on 2013-09-22
Hello, 

I hope you guys will be able to help me with my problem. Today I was using windows 7 in my vaio laptop and it crashed suddenly with a blue screen , then everytime I tried to restart the os, the problem appear at the startup and restart in a continues loop .I couldnt backup my personal data. I used Ubuntu via usb to try and copy all my personal data from the HD drive to format the os and install Linux as I was fed up with windows. I want first to make sure that my personal data is safe thats why I was planing to backup everything than install ubuntu. 
However, when I tries to mount the HD , An error appears.

> Unable to access “486 GB Volume”

Error mounting /dev/sda3 at /media/spada/987EAE1C7EADF2E4: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda3" "/media/spada/987EAE1C7EADF2E4"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Please, help me. I will really appreciated.

---

### Post by squakie on 2013-09-22
A quick search on the net turn up [this]("http://www.ehow.com/how_6827933_check-ntfs-partition-linux.html").  You may want to try it while running off a livecd or other live media such as a usb flash.  You can do df -h from the terminal to determine where your device is and if it is mounted.  If that doesn't work, try blkid from the terminal and see if it shows your disk.  The link will at least check the disk for errors and tell you what they are.  With that information, perhaps we can find something else on the net regarding those ntfs utilities that will recover the disk so you can use it.

I haven't run into this before so I'm just going by what I found.  Some other expert may have other and better ideas and post back to you.

---

### Post by squakie on 2013-09-22
Well, I just tried that to check one of my drives, and it came up with no package to install.  I checked in synaptic package manager and found the followng packages you could try:

scrounge-ntfs:  "Data recovery program for NTFS file systems"

testdisk:  "Partition scanner and disk recovery tool"

You may want to boot from a live media (like the livecd/dvd), install those 2 packages (use apt-get in a terminal window) and then read the docs or help to see how to use them.  I'm sure they will require you know "where" your disk is.  Since it didn't mount it probaly won't show in df -h but I would try that first.  You can also use blkid to see the disks your system knows.

Wish I could help you more but I've never used those tools.

---

### Post by faisal2 on 2013-09-22
I tried df -h but it didnt show the drive. I tried to use blkid but nothing happened,
I downloaded testdisk but I am not sure how to install it.I used this command 'sudo apt-get install testdisk-6'.
 but it didn't work. I couldnt find where to download the other pakages. Sorry but bear with me I am a complete ubunto newbie, I used to work with windows logic :(.

Thanks a bunch man. I really appearciate taking the time trying to help :).

---

### Post by squakie on 2013-09-23
Do this first in a terminal window:

sudo apt-get install synaptic

When that finishes you will have the synaptic package manager installed.  Go to the unity menu and type in syna and it should show up - click it.

Once this starts, go the search box and put in ntfs - you'll find both of those packages there where you can click on the box in front of each, select "Mark for installation" for each.  When both are clicked and ready to install just click "Apply" and wait for it to finish installying both.

When it is finished, I would try something like:

sudo scrounge-ntfs --help

If nothing is returned from that, try:

sudo scrounge-ntfs ?

If still nothing is returned, you'll probably need to search the net with a search string something like:

ubuntu 13.04 scrounge-ntfs

Hopefully something will be found where you can read either instructions or at least how to run it.

You can also do all of the above with the testdisk package as well.

I have never used either, but I will try installing them to see if I can figure out how to make them run, then I'll post back later.

---

### Post by squakie on 2013-09-23
Well, just installed those packages and tried to test them.  There was a time when it would have been old hat, but that knowledge is gone and I really don't think you should even try those.  Hopefully someone else will have some ideas.

BTW - can you start Windows at all, say perhaps in Safe Mode?

---

### Post by coffeecat on 2013-09-23
@faisal2, my advice would be to use a Windows tool to repair damage to a Windows filesystem, specifically chkdsk. scrounge-ntfs sounds like a useful app but from what I can tell from googling around is that it was created by a single developer and hasn't been updated in a while. 

Before your Windows 7 stopped working, did you create a Windows repair disc? If not, do you have access to another Windows 7 system - a friend/relative - to make a repair disc? I'm talking about the Microsoft utility that you can make from Windows 7, not any recovery DVDs that you might have made from the Vaio utility. Last time I used Vaio recovery DVDs, they did not have the repair tools you need.

If you can get to another Windows 7 system, type "repair" in the start menu search box, or follow this short tutorial:

[http://pcsupport.about.com/od/windows7/ht/system-repair-disc-windows-7.htm](http://pcsupport.about.com/od/windows7/ht/system-repair-disc-windows-7.htm)

Once you have the repair disc burnt, boot up with it in your Vaio. There is a simple GUI interface with some repair tools, including dropping to a command prompt where you could try running chkdsk. Some useful instructions here:

[http://www.dummies.com/how-to/content/how-to-use-a-system-repair-disc-to-restore-windows.html](http://www.dummies.com/how-to/content/how-to-use-a-system-repair-disc-to-restore-windows.html)

I know you don't necessarily want to repair Windows 7 to make it usable again - you just want to recover files - and the repair disc is primarily intended to make Windows usable again, but it does have the tools to make your Windows partition readable from Ubuntu - hopefully.

**EDIT**: by the way - and this is only relevant if you have a Windows/Ubuntu dual-boot which from a second reading of your OP seems not to be the case - take care if you want to run the first option from the recovery disc - system restore. It may very well overwrite the bootloader with the Windows mbr code, which will prevent you from booting Ubuntu from grub. That's easily fixable - if you know how - but a complication you don't want. I suggest you research how to use chkdsk from a command prompt which is really what you want to use.

---

### Post by varunendra on 2013-09-23
Something worth considering here -

Repair tools like chkdisk try to make the partition usable again and tend to make changes to the file-system (if errors are found) to achieve that. These changes (if occurred) often cause some data loss (in the erroneous area) due to lost chains being converted to new independent files or discarded altogether. In windows, most, but not all of such lost data can be found in the hidden system folders named as "found<some number>" after chkdisk has done its job. This data is almost always scattered randomly across different independent files and as such, unusable.

On the other hand, Data Recovery tools like testdisk (my favourite one) tend to recover as much data as possible, without making any change to the file-system. Even if a change is suggested and implemented (for example in cases of recovering lost partitions), it is done only on the partition table and not in the data area.

As such, I'd recommend to try testdisk first. If it also fails to read the partition, then probably the repair tools will fail too, but keep them as the last option.

To install testdisk, make sure you are connected to internet while in Ubuntu live session, then open a terminal (Ctrl-Alt-T) and do -
```
sudo apt-get update
sudo apt-get install testdisk
```
Then run it in the same terminal with -
```
sudo testdisk
```
..and follow this step-by-step guide to list and copy your data (if possible) to an external drive : [www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
In any stage (before or after deeper search), if you can list the partition and their contents, you can copy them too.

If testdisk fails, the last thing I can suggest in the course of data recovery would be photorec, which is part of testdisk.

Of course nothing is going to help if it turns out to be a physical error on the drive in question.

---

### Post by squakie on 2013-09-23
Thanks for jumping in guys.  When I tried to test these so I could post back to the OP I actually got lost - too much knowledge down the drain with age ;)  I'm glad you guys are here to help the OP.  BTW - I'll have to try testdisk again myself with those instructions.  When I tried it came up with several now-cryptic messages ;)

---

### Post by faisal2 on 2013-09-23
Thank you !! thank you !!, No really , many thanks go to you guys for taking the time to help me :).

I wasn't able to access safe mode before. but I run windows repair and the screen goes blank and I thought it froze but I left it for an hour or 2 anyway because I was a busy with something else. It turns out windows repair works but it was extremely, extremely slow in procedure and response but I left at its own base and it fixed the problem  after  several of hours (about 4 to 5 hours)and I was able to access windows and backed up my important data and left the rest. I am relived that my university information and all my unreplaceable data is safe. Now I can make my PC dual-boot with Linux safely.
I am really thankful for you guys helping me out, you kept me from taking my laptop to PC repair shop where I could risk losing all my data.

@Squakie, Thank you !!. @coffeecat, Thank you. @varunendra, Thank you.
I really can't thank you enough for the help.
I am really grateful, Thank you guys.

---

### Post by squakie on 2013-09-28
just thank coffeecat and varunendra - I didn't give you anything that worked.

---

