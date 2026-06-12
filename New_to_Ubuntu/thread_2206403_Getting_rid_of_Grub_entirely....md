---
title: "Getting rid of Grub entirely..."
date: 2014-02-18
forum: New to Ubuntu
---

### Post by gabe2 on 2014-02-18
So I decided to get rid of Ubuntu completely as I don't really ever use it. It was more homework than anything else for re-purposing my mother's ancient Dell, and that's done now. I had it on a second hard drive, so I erased and formatted the drive, but Grub appeared to still be active and every time I start up, it would say "error file not found" or something to that effect and give me a grub rescue command line.

Now, in my Disk Management window, I do see an E: drive that's only 100mb big and I'm willing to bet that this is the boot partition. The C: drive has my Win7 OS in it and has the boot info in that, so...if I delete and extend my C: into E:, that should get rid of Grub altogether, right?

Thanks in advance!

---

### Post by Bucky Ball on 2014-02-18
First question, is this an EFI install? IF you have a pre-installed Win8 it is. If it is, then E is probably the EFI partition (is it a FAT partition?). If it is and you delete it you have opened the door to hell. You won't be booting Windows or anything else. 

Next, if you installed in legacy mode, unless you specifically told it otherwise, grub will install to the MBR which at the beginning of the first disk, sda.

---

### Post by gabe2 on 2014-02-18
No, it's Windows 7 and I installed it myself when I built my rig. I'm trying to remember how I installed Ubuntu and Grub as a result to dual-boot. Worked like a charm except it took forever to enter into the Grub screen. Now, I just want it back to the way it was pre-Ubuntu.

Also, the E: drive is NTFS, but System Reserved. Like you said, I don't want to unintentionally delete something and never be able to get back into Windows 7 short of re-installing everything all over again.

For the record, I tried the bootrec /fixmbr and /fixboot from my Windows repair disk and it didn't do anything.

---

### Post by Bucky Ball on 2014-02-18
System reserved? I'd leave it. That is generally a Win thing. Grub doesn't exist on a partition unless you create one and put it there or, as I say, put it on an existing partition during install intentionally. 

To find out where grub and everything else is you could try running boot repair from a live CD, creating and posting the boot info script. You can create a bootable Boot Repair live CD or you can install when you are running from a Live Ubuntu session (booted from CD/DVD/USB). 

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by evan8 on 2014-02-18
Yes because careful about the EFI stuff. I had a fun 2 days of figuring it out. Couldn't load any OS etc. Ended up running live CD and fixing GRUB somehow then reformatting. I also had my BIOS on ahci for SSD. And I guess you can't boot discs that way..

---

### Post by gabe2 on 2014-02-19
Thanks, I'm gonna have to figure it out again one of these days soon. It's getting old having to hit F12 every time I start up to boot into Windows.

I did try the boot repair disk and ran the program, but didn't seem to fix the problem. I think maybe it's because I completely wiped and reformatted my 2nd hard drive that had Ubuntu and its boot info on that and GRUB couldn't find it, so it errored. I'll post the script when I get around to it.

---

### Post by gabe2 on 2014-02-22
All right, finally have some time to kill and try and fix this little but annoying problem. Ran boot repair and had it output a summary, which is here: [http://paste.ubuntu.com/6975962/](http://paste.ubuntu.com/6975962/)

I thought I saw an option in the advanced menu of boot repair that might fix the issue. The partition booted by the MBR is currently listed as the Windows boot partition only as opposed to the main Windows partition (I think it was sda1 vs sda2). If I switched that and ran it, would it work?

*Edit* Why would there be two Windows boot partitions? Since I already have a boot record on my main Windows, I can just get rid of the boot partition and be fine, can't I?

I would prefer to get rid of GRUB entirely, of course, and just have it boot into Windows normally.

Thanks again.

---

### Post by Mark Phelps on 2014-02-22
There's two Windows partitions because one contains the boot loader, while the other contains the OS and apps. If you remove or corrupt the 100MB partition, that trashes the Windows boot loader and Win7 will then NOT start.

If sda1 is the small partition, and sda2 is the OS partition, you need to have the boot flag on sda1.  So, don't go around switching these.

You typically have to do three passes of Windows Startup Repair to get it working again, you only did two.  Try running it some more.

---

### Post by gabe2 on 2014-02-22
More than once? Hmm, ok. I'll give it a shot.

*Edit* Tried Windows repair, tells me there's no problems. So I run the fixmbr and fixboot commands again. No go...still getting the grub rescue> command prompt. Ran boot repair again and here's the summary: [http://paste.ubuntu.com/6976742/](http://paste.ubuntu.com/6976742/)

---

### Post by gabe2 on 2014-02-22
Okay, so I'm feeling like a colossal idiot now. I went into BIOS and, guess what, the boot order was set to my 2nd hard drive first, where my Ubuntu used to be (and, presumably, GRUB). Switched the boot order and that fixed that issue.

Still a very minor thing, though, as it takes my 'puter a good while to boot into Windows when I get the OS loading screen and it goes . . . . . . . . . for probably a good 20 seconds? It used to be just boom, right into Windows right away. Is there some lingering Grub crap floating around in my MBR or something? I'm considering rebuilding my BCD to clean it out, but don't want to waste the effort if that won't do anything.

---

### Post by oldfred on 2014-02-22
You have a Windows boot loader in sda and grub in sdb.
The only way you get grub to boot is if in BIOS you have set sdb or the 640GB drive as default or first to boot.

You also have boot flag on sda2 not sda1. But it looks like boot files have been copied to sda2 so it may still boot, but you would not be able to get into Windows recovery(repair). But better to have a Windows repairCD or Flash drive anyway as even if booting from sda1, you may not always be able to get to a repair console.

---

### Post by gabe2 on 2014-02-22
> **oldfred said:**
> You have a Windows boot loader in sda and grub in sdb.
The only way you get grub to boot is if in BIOS you have set sdb or the 640GB drive as default or first to boot.

You also have boot flag on sda2 not sda1. But it looks like boot files have been copied to sda2 so it may still boot, but you would not be able to get into Windows recovery(repair). But better to have a Windows repairCD or Flash drive anyway as even if booting from sda1, you may not always be able to get to a repartee console.

Yeah, ha ha, I just saw that like 10 minutes ago. *facepalm* See my most recent post, I beat you to it, lol!

---

