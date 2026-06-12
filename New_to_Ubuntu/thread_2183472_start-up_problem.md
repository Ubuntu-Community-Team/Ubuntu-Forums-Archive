---
title: "start-up problem"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by zaanta2 on 2013-10-25
Hi all,
I need some help/advice please!
I have a Dell inspiron that came with w8. (less than 18 months old)
2 weeks ago I did a complete ubuntu 12.04 install as the sole OS
Everything went fine - just perfect! I installed a few "safe" pieces of software....I've done nothing "unusual" with
anything - I don't know how anyway!!
Then yesterday I suddenly had a problem starting the laptop:
I got a whole lot of scrolling text of which I didn't understand a word! I did manage to catch this:
"Media test failure...check cable"
and then later:
ata3: link is slow to respond
ata3: COMRESET failed
Now I have to start & close down & then do the F12 thing to get into boot, switch to 'hard drive' then I get the option screen. I choose recovery &, eventually, everything works.
But I notice the system is a tad slower now????
I'd be really happy if someone can tell me I have nothing to worry about & how to get the start-up back to the (fast) way it was.

Oh - there was one thing I did: I disabled Bluetooth - but that couldn't be the reason, no??

Many thanks for any help..........

---

### Post by fantab on 2013-10-25
What version of 12.04 is that? 
Did you install 12.04 or 12.04.2 or 12.04.3. 

12.04.2 onwards 12.04 got support for newer hardware.
If you installed 12.04 or 12.04.1 then upgraded to latest, which I think is 12.04.3 then you don't get this newer hardware support. If this is the case then I suggest you reinstall with latest Ubuntu 12.04.3.
However if you downloaded and installed 12.04.2 or 12.04.3 then you are good.

Look at hinted errors I seems as though there is some loose connection with the cables... look into it or get someone to look into it for you.

---

### Post by zaanta2 on 2013-10-25
Hi,
thanks for replying

I have 12.04 LTS - that's what it says :) - no other numbers
I don't understand about the cables because it's a laptop!

---

### Post by fantab on 2013-10-25
Sometimes there can be loose wire inside if you had dropped the laptop or for some strange reason. Get it checked.
Boot with Ubutnu DVD/USB and 'Try Ubuntu without installing". Open the application 'Disks', select your HDD and from the gear icon run SMART tests on your HDD and see what it has to say.

---

### Post by sandyd on 2013-10-25
> **zaanta2 said:**
> Hi all,
I need some help/advice please!
I have a Dell inspiron that came with w8. (less than 18 months old)
2 weeks ago I did a complete ubuntu 12.04 install as the sole OS
Everything went fine - just perfect! I installed a few "safe" pieces of software....I've done nothing "unusual" with
anything - I don't know how anyway!!
Then yesterday I suddenly had a problem starting the laptop:
I got a whole lot of scrolling text of which I didn't understand a word! I did manage to catch this:
"Media test failure...check cable"
and then later:
ata3: link is slow to respond
ata3: COMRESET failed
Now I have to start & close down & then do the F12 thing to get into boot, switch to 'hard drive' then I get the option screen. I choose recovery &, eventually, everything works.
But I notice the system is a tad slower now????
I'd be really happy if someone can tell me I have nothing to worry about & how to get the start-up back to the (fast) way it was.

Oh - there was one thing I did: I disabled Bluetooth - but that couldn't be the reason, no??

Many thanks for any help..........
sounds like [http://comments.gmane.org/gmane.linux.kernel/1247563](http://comments.gmane.org/gmane.linux.kernel/1247563)

---

### Post by fantab on 2013-10-25
Yep, it does look like what sandyd pointed out. 
If you have any older kernel installed then boot to it. You can find additional older kernels installed from Grub Menu- Advanced options. Not sure if 12.4 uses Advanced options. But the kernels will be listed in the Grub menu.
Or Try installing latest ubuntu 13.10. If you want save any important data then boot with Ubuntu DVD/USB and Back it up.

---

### Post by zaanta2 on 2013-10-27
Well, thanks to all for the advice/suggestions but I'm afraid it's all a bit too technical for me! All this about "kernels" and "grub" etc....might as well be sanskrit!!
I have understood, however, that one soltion could be to upgrade to the latest release?
I have also read that "upgrading" should be done 'step-by-step' i.e. from one release to the next - not straight from 12.04 to 13.10 for example.
My question now is: by "upgrading" will I lose data? I understand that by doing a new install with 13.10 requires I do a full back-up first, but is that also necessary with upgrading?
Which method would you recommend?

Sorry for my "newbieness" but I'm trying to learn as much as I can with my limited intelligence ;)

Thanks again

---

### Post by fantab on 2013-10-27
Instead of "upgrading" re-install 13.10 from DVD/USB. About losing DATA: this would depend on how you've installed Ubuntu and how you are going to re-install it. It will be good idea to BACKUP ALL YOUR IMPORTANT DATA.

If you can boot from Ubuntu DVD/USB, then "Try Ubuntu Without Installing", open Terminal [Ctrl + Alt + T], run the following command and post its output:

```
sudo parted -l
sudo fdisk -l
```

These commands will tell us how your Hard Disk is set up. And looking at the info we can help you install Ubuntu without losing data.

---

### Post by zaanta2 on 2013-10-27
OK fantab, thanks

I did what you suggested in terminal & got this:
from sudo parted -l
Model: ATA WDC WD10JPVT-75A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ext4            boot
 2      992GB   1000GB  8458MB  extended
 5      992GB   1000GB  8458MB  logical   linux-swap(v1)

and from fdisk -l:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000338b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1937002495   968500224   83  Linux
/dev/sda2      1937004542  1953523711     8259585    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1937004544  1953523711     8259584   82  Linux swap / Solaris

---

### Post by zaanta2 on 2013-10-27
I have now downloaded 13.10 & burned a DVD
I have saved all data
Do you think, if I now do a complete install with 13.10 it will make a difference or is there, in fact, something amiss with my computer?
thanks

---

### Post by fantab on 2013-10-27
Don't you want to install Windows for dual boot? You have only 2 partitions for Ubuntu.

---

### Post by zaanta2 on 2013-10-27
OK, now I'm starting to panic......just a little!
I just inserted my external drive which I used to save all my data on, just to make sure it was all there!
And I got this:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Please help!!

---

### Post by fantab on 2013-10-27
Was this external disk part of any RAID setup? Check your BIOS SATA mode to see what mode it is set in. AHCI, IDE or RAID. If you don't know what it should be then set it to AHCI.

I would say first of all you install your Operating Systems. Then we'll see what is with External HDD. Mostly its a minor thing, unless its a Hardware fault.

---

### Post by asmiha on 2013-10-27
> **fantab said:**
> Don't you want to install Windows for dual boot? You have only 2 partitions for Ubuntu.

Actually no!!!
I really never want to use windows again, but if I cant get this problem sorted I hate to say I might have to.
Please not!
Any ideas what happened to my external drive?
Im writing on 13.10 trial and Im really impressed!!

---

### Post by asmiha on 2013-10-27
> **fantab said:**
> Was this external disk part of any RAID setup? Check your BIOS SATA mode to see what mode it is set in. AHCI, IDE or RAID. If you don't know what it should be then set it to AHCI.

I would say first of all you install your Operating Systems. Then we'll see what is with External HDD. Mostly its a minor thing, unless its a Hardware fault.

So theres no chance of losing the date saved thereon?
and I have to say Ive used this external drive 100 times without such a problem

---

### Post by fantab on 2013-10-27
Now I am confused. Is **zaanta2** and **asmiha** same person? If it is then please use only one account and expect a lecture by mod.

If you have access to a windows machine then connect the ext hdd to it and see if it works. If it wants to run 'chdsk' then let it. If not you can run it yourself on the the said disk. [URL="http://www.w7forums.com/threads/how-to-use-chkdsk-check-disk.448/"]http://www.w7forums.com/threads/how-to-use-chkdsk-check-disk.448/
[/URL]And after this boot windows a couple of times with this Ext HDD connected.

If I were you I would partition my HDD like this:
For Dual-Boot-
75GB Primary NTFS Windows
30GB Primary EXT4 Ubuntu / (for Ubuntu system files)
30GB Primary Ext4 Free (if I want to install another version or flavor of Ubuntu in future or some another distro)
All the remaining GB Extended Partition
4GB Logical SWAP
All the remaining GB Logical Ext4 (for data)

For UBuntu only:
30GB Primary Ext4 Ubuntu /
30GB Primary Ext4 Free
4GB Primary SWAP
All the remaining GB Extended
All the remaining GB Logical Ext4 for data 

You can format Data parttion as /home or keep is simple without any mountpoint.

---

### Post by Iowan on 2013-10-27
> **fantab said:**
> Now I am confused. Is **zaanta2** and **asmiha** same person? If it is then please use only one account and expect a lecture by mod.

I'm confused, too.
Closed for review...


Re-opened while we sort out username problems.

---

### Post by zaanta2 on 2013-10-27
Hi Fantab,
ok we can continue thanks to the tolerance of Iowan :)
So do I understand you correctly:
I can go ahead & do a complete install of 13.10 and where it asks me about partitioning I do as you suggest:
manually partitioning as:

For UBuntu only:
30GB Primary Ext4 Ubuntu /
30GB Primary Ext4 Free
4GB Primary SWAP
All the remaining GB Extended
All the remaining GB Logical Ext4 for data 

But I'm still worried that I'm going to lose all my data that I saved on my external drive??
In the meantime I've tried to get as much as possible saved onto DVDs but there's too much for just 1 or even 2!!!
You think I can get the data back somehow?
thanks

---

### Post by sandyd on 2013-10-27
> **zaanta2 said:**
> Hi Fantab,
ok we can continue thanks to the tolerance of Iowan :)
So do I understand you correctly:
I can go ahead & do a complete install of 13.10 and where it asks me about partitioning I do as you suggest:
manually partitioning as:

For UBuntu only:
30GB Primary Ext4 Ubuntu /
30GB Primary Ext4 Free
4GB Primary SWAP
All the remaining GB Extended
All the remaining GB Logical Ext4 for data 

But I'm still worried that I'm going to lose all my data that I saved on my external drive??
In the meantime I've tried to get as much as possible saved onto DVDs but there's too much for just 1 or even 2!!!
You think I can get the data back somehow?
thanks
unplug your external drive before installing - then do a disk check in windows. Linux cannot repair NTFS volumes

---

### Post by zaanta2 on 2013-10-27
I don't have windows!

---

### Post by zaanta2 on 2013-10-27
....will installing "dmraid" from the software center help???

---

### Post by fantab on 2013-10-27
If your External HDD is NTFS then it needs to connect to a Windows machine to correct file-system errors, if any. Only Windows can do that for ya.
I don't think that it is a RAID issue, yet.

If you want to consider my recommendation, let me tell you to do a Windows and Ubuntu dual-boot for some more time. Even if you don't want use Windows keep for some more time on machine to avoid such beginner's frustrations. Later when you are quite comfortable with Linux you can remove Windows.
I still have Windows 7 on my machine, though I haven't touched it for more than a year.
When dual-booting Windows and Ubuntu, its a good idea to install Windows first. You MUST reformat the windows partition with NTFS with Windows installer.

---

### Post by zaanta2 on 2013-10-28
Hi fantab,
OK thanks
As I understand it, the ONLY way to free up my external drive is to open it with a windows pc?
So - I have a neighbour with w7 - I can use his.
What do I do EXACTLY when it opens? And is it certain that it will open? What must I do if it doesn't?
Sorry to be so dumb ;) .......and do you think all the data on it will be accessible?
I really want to install 13.10 but I cannot until I'm sure I have all my files safe somewhere!
I suppose I could upload everything to Ubuntu One but that would take forever since it seems I can only load files at a time and not folders?
Or have I missed something here as well??!!!

---

### Post by fantab on 2013-10-28
I had posted this link earlier:[ http://www.w7forums.com/threads/how-to-use-chkdsk-check-disk.448/]("http://www.w7forums.com/threads/how-to-use-chkdsk-check-disk.448/") it tells you how to run 'CHKDSK' (check disk for filesystem errors) once you've connected the Ext HDD to a windows machine.
These file system errors are not uncommon, especially with USB pendrives and Ext HDDs. I never lost any data to these errors so far.

---

### Post by zaanta2 on 2013-10-28
ok fine....I'll try to do this later today & let you know what I find
thanks again

---

### Post by zaanta2 on 2013-10-28
OK...I did that and I've connected the drive once more to my ubuntu but cannot open it? I get the option to mount but nothing happens!
I haven't lost anything - like you said :)
But I still would like to be able to open the drive on ubuntu before I go any further

---

### Post by zaanta2 on 2013-10-28
so.....many many many thanks to all who contributed to this poor man's learning curve!!!
I just installed ntfs-config & mounted my external drive.....then Voila! It opened and everything is there.
That's all I was waiting for....now to install 13.10 & enjoy the latest wonders of Ubuntu.
I'm sure this is not the last you've heard of me, though ............lol

My favorite quotation is one by Dag Hamersköld (1st. man to hold the presidency of the UN for 3 years)
"Never measure the height of the mountain (you're climbing)
When you reach the top, look back & see just how small it really is!"

---

### Post by sandyd on 2013-10-28
If you think the thread is solved, please click Thread Tools -> mark thread as solved

Thanks!

---

