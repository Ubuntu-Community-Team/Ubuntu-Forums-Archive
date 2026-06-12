---
title: "Boot issues with grub rescue?"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by galyna1 on 2012-06-25
I am a total newbie who is hella confused. I'll be as thorough as I can because I don't know which of the following is actually useful information!

I use an Acer netbook. I run Ubuntu Netbook 10.04, but left Windows Vista on too as a just-in-case. Today is the first time in like 2 years that I needed to use Windows - I had a job thing that required IE.

So I restarted my computer, selected "Vista" for the OS, and my computer turned itself off. Not what I was expecting, but o-kay. Start up again. At which point a Windows erecovery tool popped up that I've never seen before and wanted to make changes. That was just odd, so I closed that out and restarted again. I figured if it was just a glitch all would go back to normal, and if it popped up again I could work it from there. 

I got the first screen (with the "press F2" option?), but instead of the screen where I select my OS I got "no such partition" and a "grub rescue" prompt. Again, not helpful. So I started trying to figure out what was wrong and checked out the forums.

One of the first suggestions was to run ***sudo fdisk -l***just to see what I had. According to what I got from the site ([http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html](http://www.geekmitra.com/2011/06/recover-grub-live-ubuntu-cd.html)) one of the partitions should have listed "Linux" under "Systems". I had two that said "Linux Swap/Solaris", but not anything for "Linux" alone. From what I can tell, that means that I don't have Linux installed anymore?

That just didn't seem right, so I kept looking. Following another suggestion I created a LiveUSB and used that to run boot-repair (which gave me a reference of [http://paste.ubuntu.com/1059635/](http://paste.ubuntu.com/1059635/) if that helps). 

Now I can get to the OS Selection screen, but now it's saying that Windows Starter is the only OS on the system, but that it can't load it so I need to repair it. I can run a LiveUSB for Linux, which is great, but to fix what's wrong from that I think I need to chroot the system. Right? Except I don't think I can do that because I can't find what partition to set everything with! 

So what do I do now? Did Vista just erase Linux? What about my files? Should I just reinstall Linux from scratch, or is there something else I can do? Is my computer going to just explode from the stress?

I'm totally lost, really frustrated, and have no clue where to go from here (aside from avoiding Windows like the plague from here on out). Any help would be REALLY appreciated!

---

### Post by drs305 on 2012-06-25
For now I would only use a LiveCD so you don't write anything to the drive.

It looks like your partition table may have been corrupted. If you look at the RESULTS.txt file, there is a large area of the extended partition that is currently not accounted for.

> /dev/sda1                  63    25,173,854    25,173,792  27 Hidden NTFS (Recovery Environment)
/dev/sda2          25,173,855    25,382,699       208,845   7 NTFS / exFAT / HPFS
/dev/sda3    *     25,382,700   103,487,282    78,104,583   7 NTFS / exFAT / HPFS
/dev/sda4         **103,487,486   312,580,095**   209,092,610   5 Extended
/dev/sda5         **310,509,568   312,580,095**     2,070,528  82 Linux swap / Solaris


I can't recall if Boot Repair has an option to repair partition tables or not. I know Test Disk can but I'm going to leave it to others to suggest the solution.

---

### Post by galyna1 on 2012-06-25
Thanks so much for the reply! Knowing the partitions are damaged really helps.

I checked, and Boot Repair can repair partitions. It's one of the advanced options. Would this be safe to do, or could it make the problem worse?

---

### Post by drs305 on 2012-06-25
> **galyna1 said:**
> Thanks so much for the reply! Knowing the partitions are damaged really helps.

I checked, and Boot Repair can repair partitions. It's one of the advanced options. Would this be safe to do, or could it make the problem worse?

I believe BR has the option to back up the current partition table, so I'd do that first. I suspect any repair would do that first in any case but it wouldn't hurt to make a backup manually. The BR developer probably uses a procedure similar to Tesk Disk and would be much simpler.

---

### Post by YannBuntu on 2012-06-26
Hello

As suggested by Drs, you should first:
1) backup the documents that are still accessible
2) backup your partition tables (run Boot-Repair, click "Advanced options", click the "Backup partition tables" button)
3) better also do a bit-to-bit copy of your disk (eg via ddrescue) on another disk

Boot-Repair's "Repair filesystems" option does:
- "ntfsfix" for ntfs partitions (this forces Windows to perform a chkdsk next time you start Windows)
- "fsck -fyM" on other partitions


I don't know what TestDisk does exactly but I suppose it's more powerful for partition table fix/ filesystem fix. It can also do data recovery.

---

