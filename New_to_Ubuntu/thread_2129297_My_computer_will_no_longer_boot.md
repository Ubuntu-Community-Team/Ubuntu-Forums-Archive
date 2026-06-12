---
title: "My computer will no longer boot"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by jrbrooks on 2013-03-25
I have a dual boot (Windows 7/Ubuntu) system and I recently accidentally  formatted a 500GB partition on a 1TB hard disc (see thread "Lost Data after formatting hard disc"). I could not recover the original partition but recovered the important files I had lost. Then I tried to format the partition back to how it was originally (500GB NTFS). After my disastrous accidental formatting the 500 GB had broken into about 5 sections - 3 large ones of circa 410 GB, 50 GB and 9 GB and two small ones (MBs). I used GParted but I could not see a way to put the Humpty Dumpty 500 GB back together. I then decided to boot up into Windows and use the Windows utility. I think I could have done it right but I ended up formatting each of the 3 large sections into separate NTFS partitions (More, Spare 1, Spare 2. Extra is the [original, untouched] 500 GB partition on the 1 TB disc). All seemed OK then I rebooted. I never got the chance to select an operating system. Black screen with
Error no such device: 801be6c2-cabc-49f8-a74f-fa06b7167cbf
grub rescue >

I then used Boot-Repair Disk.
Before repairing I saved the report  [http://paste.ubuntu.com/5645194](http://paste.ubuntu.com/5645194)
Then I repaired (2 or 3 times) but it did not work.
The last report made is   [http://paste.debian.net/244553](http://paste.debian.net/244553)

I looked at the latter report and even my dumb brain can see that what I did was stupid (I should have formatted dev/sdc2) but I am surprised that a fault on a disk that does not contain the OS means that the computer will not boot.

Help!

---

### Post by fantab on 2013-03-26
If you don't have any important data to loose on you Hard Disk then, I suggest delete all partitions and reformat. Boot with Ubuntu LiveCD/USB and use Gparted to delete all your partitions. If you want NTFS then use Windows Install disk to recreate the NTFS partitions. 
If you have data to save then Use Ubuntu LiveCD to save all that you want to on another HDD or USB or DVD and then delete, recreate and reformat partitions.

If you have installed Grub on the HDD that "you worked on" then while formating and deleting you must have damaged the Grub.

If you have two HDD then I suggest you install Windows on One and Ubuntu on another. Just change the BIOS settings to boot the Ubuntu HDD first... That ways you can have pristine Windows safe on its own HDD.

---

### Post by newb85 on 2013-03-26
+1 to fantab's advice/assessment

---

### Post by jrbrooks on 2013-03-26
So, using GParted I deleted all of the partitions on sdc2 however I never had any menu option to format the unallocated volume. I booted into Windows and could format the 500GB space. In Windows, all looked OK and I shutdown. But the system will not reboot - coming up with exactly the same error. I ran the Boot-repair disc and the report is [http://paste.debian.net/244994/](http://paste.debian.net/244994/). 
Looking at the report from Boot-Repair I see that GRUB2  is indeed installed on /dev/sdc (and /dev/sdb). So it is obviously corrupted on sdc. However, remembering that we are in the Absolute Beginners section I have no idea how to repair it or, indeed, much idea what it means. However I also do not see any sign of Linux/Ubuntu.
A couple of years ago I installed Ubuntu on to my Windows PC and selected the Dual-Boot option and, until 2 days ago, that is exactly what I got when I powered up the PC. 
I think, unknown to me Ubuntu was installed on the 1 TB disc and has been wiped when I accidentally formatted "that" partition
Do I have to re-install Ubuntu?

---

### Post by sandyd on 2013-03-26
Somethings not right here.
```
=> Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at [B]sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for /boot/grub[/B].
```
```

sdb1: __________________________________________________________________________

    File system:       **ntfs**
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       **ntfs**
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:

```

---

### Post by sandyd on 2013-03-26
> **jrbrooks said:**
> So, using GParted I deleted all of the partitions on sdc2 however I never had any menu option to format the unallocated volume. I booted into Windows and could format the 500GB space. In Windows, all looked OK and I shutdown. But the system will not reboot - coming up with exactly the same error. I ran the Boot-repair disc and the report is [http://paste.debian.net/244994/](http://paste.debian.net/244994/). 
Looking at the report from Boot-Repair I see that GRUB2  is indeed installed on /dev/sdc (and /dev/sdb). So it is obviously corrupted on sdc. However, remembering that we are in the Absolute Beginners section I have no idea how to repair it or, indeed, much idea what it means. However I also do not see any sign of Linux/Ubuntu.
A couple of years ago I installed Ubuntu on to my Windows PC and selected the Dual-Boot option and, until 2 days ago, that is exactly what I got when I powered up the PC. 
I think, unknown to me Ubuntu was installed on the 1 TB disc and has been wiped when I accidentally formatted "that" partition
Do I have to re-install Ubuntu?

That would be my thought as well - the partitions are currently gone (shows up formated ast NTFS)
```
sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
```

However, in your first post, all your partitions were NTFS [http://paste.ubuntu.com/5645194/](http://paste.ubuntu.com/5645194/)
so Ubuntu was gone already.

You would need to reinstall Ubuntu in this case - as Ubuntu is gone.

---

### Post by jrbrooks on 2013-04-01
Now my system is working fine - but I only have Windows installed.
On re-installing Ubuntu V12.04 using the Windows Installer I found it was totally unstable - freezing up and then going to a blacvk screen with the following error messages being continually updating
"Failed to idle channel 1
Failed to idle channel 2"
Switching off the computer was the only way out. 
I have a 64 bit dual processor system 

There is some history to this as I originally had installed V10.04 and this ran without any problems. Then I upgraded to V12.04 and it quite often used to freeze up. I suppose I should start a new relevant thread.

---

### Post by AntiBodies on 2013-04-01
testing

---

### Post by Jonno303 on 2013-04-02
I posted a question on Ask Ubuntu, haven't received an answer yet - the problem seems similar to jrbrooks'. Does anyone have any answer? 

[COLOR=#333333][FONT=Ubuntu Beta]I am new to Linux and have recently set up a dual boot with Windows 7 on my Lenovo W530 (8gb RAM). During the partitioning phase of setting up my dual boot I noticed there was a 8gb partition set aside for Hibernation. Apparently this is a regular situation faced by those wishing to partition a SSD.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Anyway, the installation of Ubuntu 12.04 64bit went ahead and everything had been relatively smooth over the last few days whilst I downloaded and installed the software I required. I must admit as a noob, I felt I was copying and pasting a lot of terminal commands that might have altered the internal dynamics of the computer in ways I could not comprehend. However, this process was mostly successful.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]After setting up most of the software I turned my attention to the hibernation function, as I thought it would be a waste of 8gb on my SSD if it was not utilised on Ubuntu. After reading the forums, I found that the function for hibernate had been hidden due to instability issues. I pressed ahead and followed the instructions to reenable it. This was successful. However, I noticed that on shutdown or restart, the computer would hang on a black screen in the final stages of the shutdown process. It required me to long press the power button to turn off the machine.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]This morning I tried to boot the computer and found that the computer now hangs on a black screen after selecting Ubuntu in GRUB. Long pressing the power button loads the Ubuntu shutting down screen (loading dot animation), but sometimes this also leads to another black screen.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]After this I booted the machine and selected the recovery menu, and after trying to boot it as a 'regular' session, the machine does not recognise my login (or maybe I am mistaken??). My first attempt at selecting the recovery menu showed a message: ata_id [878]:hdio_get_identity failed for '/dev/sbd': invalid. Although the problem persists, this message is not shown anymore.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I tried Boot Repair however this also failed to resolve the issue. FYI the message after completing Boot Repair was: [http://paste2.org/p/3482165](http://paste2.org/p/3482165)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Feeling very lost right now! Please help![/FONT][/COLOR]

---

### Post by JagdishMistry on 2013-04-02
hi, if you not have any important data in your PC then, delete all your partition and reboot it again..

---

### Post by Jonno303 on 2013-04-02
Unfortunately, I have some software that has been installed that I won't have access to again if I wipe the PC. That will be my last resort if there is no other way of approaching this issue...

---

