---
title: "Missing OS: I've done a silly thing..."
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Mark_Sony on 2014-05-01
Building up a new computer I took the spare hard drive out of my old PC to use as a spare in my new computer. The problem is that the old computer was set up to dual boot between Ubuntu and Win8. Whilst Win8 is still present on drive C, Ubuntu was installed on the drive I removed so now, when the **old** PC boots, GRUB can't find Ubuntu and stops everything at the command prompt. I had, somewhat optimistically, hoped that Grub would simply boot to the only OS available: Win8. No such luck. So the old PC is temporarily unusable.
 
The question is this: how do I get into Grub, remove references to Ubuntu and force it to boot into Win8? Perhaps I need to get rid of Grub altogether and repair the Win8 install? One slight complication here is that the Win8 install was done as a paid, on-line upgrade so I don't have disks that would help me remove grub and repair Windows 8. (I'm going to read up a bit more on doing this just in case it is my only option).
 
M

---

### Post by Bashing-om on 2014-05-01
Mark_Sony; Hi ! Welcome to the forum.


We can and will help !
Maybe not as dismal of a situation as you think - maybe.

IF on that old system you set up as a true dual boot - Windows on the 1st hard drive ( ubuntu speakeze -> sda), and the 2nd hard drive (sdb) held ubuntu; Then, I would expect that Windows was UN-touched on sda.
'IF' that is the case, I would expect that resetting in the EFI boot sequence to that of the 1st hard drive should find the Windows boot loader.
'IF' this is an older system, EFI does not apply and we are looking at the legacy partitioning, then 'bios' booting  applies.
Else boot up from an ubuntu liveDVD and let's get a look at what the partitioning is to see if in all actuality a Windows' fixmbr is in order:
liveDVD -> terminal ; Terminal codes:
```

## bios booting do: ##
sudo fdisk -lu
## EFI booting do: ##
sudo apt-get install gdisk
sudo gdisk -l /dev/sda
## in either case do: ##
sudo parted -l
sudo parted /dev/sda unit s print

```
Hope for the best

[INDENT][INDENT]but, maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mark_Sony on 2014-05-02
Thanks for this. I will get a chance to try some things later today. Reading up on Win 8.1, if I can get that OS to boot, there are built in tools for repairing the boot processes. So that is another option to investigate. I know that Win8.1 is still there and good to go once I have solved the boot issues.

---

### Post by Mark_Sony on 2014-06-15
Hi, it's been some time and I have only just had space to look again at getting this computer running. To recap, when I power thing on it gets as far as the Grub rescue prompt and stops. Most commands are rejected as unknown and, after following various threads around this forum, I cant' get it to find a bootable drive. So what I just tried is to create an fresh Ubuntu DVD with the latest ISO on it. This works fine in the computer I am using to write this note but it doesn't seem to work in the computer that has the problem. This has a brand new DVD drive fitted and the boot order has been set to select the DVD first. The DVD starts up and runs for a while before returning to the rescue prompt with the message: no such device xxxx-xx... This is odd cuz I would have expected the dvd to boot and take me through the Ubuntu installation process.
To check the DVD drive, I inserted an original MS Win 7 DVD. It runs and displays the message 'Press any key to boot from CD or DVD' (the Ubuntu DVD I created doesn't post that message). When I press a key, I am taken straight back to that Grub rescue error - no such device etc. So I am going around in circles. 
I have also created a bootable USB drive with the latest Ubuntu ISO on it and again, after directing the BIOS to select this I get sent back to the Grub rescue prompt.
I am now worried because my next option was to create a 32bit Win8.1 rescue/ recovery disk and try using that to get the MBR reinstated but I am beginning to doubt whether that will work. If the Win 7 installation DVD won't work then why would anything else? 
What is going on here and why can't I find a way around the Grub rescue prompt? What are my options now?

It's worth restating the events that led to this situation:
Computer A was upgraded online (no DVD!) from win 7 to win 8. It had 2 hdds installed: hdd0 was used for windows; hdd1 was a data drive with a small partition set up for Ubuntu (64bit). Grub was set up to select win 8 as the default OS.

Computer B superseded computer A and in the process hdd1 was transplanted into computer B as a second hdd. The Ubuntu partition was deleted. All OK except...

Computer A now won't boot and halts at the Grub rescue prompt as described above.

---

### Post by Bashing-om on 2014-06-15
Mark_Sony; Sheeeshh,

We are still at my post #2. Show us what we are dealing with ...
Maybe, perhaps, could be .. that the situation is UEFI and/or GPT partitioning and attempting to install grub as the legacy msdos ( NOT MicroSoft Disk Operating System at all or any relation). No workie, msdos on GPT partitioned disk(s).

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Mark_Sony on 2014-06-16
The opinion here amongst colleagues who have some experience of Linux is that the problem booting from a DVD isn't necessarily connected with the grub rescue prompt or missing Linux partition. We're building a win8.1 (32bit) image to attempt recovery of the installed OS and MBR but will have to overcome the DVD booting problem first. It seems that DVDs are being read but that some problem occurs preventing them from executing code beyond a certain point whereupon the system drops back to the grab rescue prompt. 

I will let you know if I make any progress.

---

### Post by Mark_Sony on 2014-06-16
...also, I am going to swap out the USB keyboard for a standard PS/2 model. When I first installed Ubuntu and used Grub to select which OS to boot to (Ubuntu or Win8) I had to make changes in the BIOS so that the USB keyboard worked with grub. Using a standard PS/2 keyboard will eliminate any potential for problems here.

---

### Post by yancek on 2014-06-16
From the information you posted originally, two drives on the computer - one with windows 8 and one with Ubuntu, it appears that you were using Grub to boot both.  So, you had Grub installed to the master boot record of the windows drive.  You do know that almost ALL grub files needed to boot are on the Linux/Ubuntu partition!  The master boot record is tiny.  You removed almost all the Grub boot files so obviously it won't boot that way.  You need your windows 8 medium to repair the bootloader so that you can boot windows.  Reading your more recent posts, it appears that you are now aware of this.

With regard to the new DVD drive, can you check in the BIOS to see if it is recognized?  Do you still have the old one attached - 2 CD/DVD drives?

---

### Post by Mark_Sony on 2014-06-16
Thanks for your input. I will check this later. The old DVD drive failed and I replaced it only a day or two ago ready to look at this problem. I am confident the issues can be solved with a Win8.1 image providing I can get it to boot from the DVD correctly. :D

---

### Post by Bashing-om on 2014-06-16
Mark_Sony; Hey, hey;

Also be aware Windows8 may = UEFI = GPT partitioning, and then the legacy partitioning scheme for MBR is out the window and no longer applies.
We are then talking EFI for the means to boot, and all kinds of other hoops to jump over - perhaps even "secure boot". However you boot up Windows the method to boot will have to be matched in ubuntu. Once the booting is set up, ubuntu's installer will take care of it's self - just make sure you know where ubuntu is going to install grub. With 2 hard drives, often best to install Windows on that 1st hard drive with it's boot code, and install ubuntu onto that 2nd hard drive with grub installed independently of Windows, boot that 2nd hard drive and have grub chainload Windows.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by Mark_Sony on 2014-06-18
Hi all, thanks for your advice and guidance on this. The problems have now been solved and, as is often the case, it turned out to be quite easy. 

Firstly, using a PS/2 keyboard in place of a USB variety enabled me to boot from a DVD. It seems that drivers for the USB keyboard weren't being loaded and when I was prompted to 'Press any key to boot from CD/DVD - nothing was getting through so the system timed out and dropped back to the grub rescue prompt. 

Having got past that obstacle, I was then able to use a Win 8.1 image to repair the MBR and everything was good. The computer now boots directly into Win8.1 and no harm seems to have been done. 

Thanks again. :D

---

