---
title: "multi-boot system questions on an 120GB ssd + 1TB hdd (Windows 7, Ubuntu, Slackware)"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by HappyFishFace on 2013-04-13
Hello, I am planning on building a new computer over the summer (or early fall), and want to design a multi-boot system.

I would like to install: 
Windows 7 home premium- for gaming and windows only programs
Ubuntu 13.04- for use as a main OS
Slackware 14.0 (or the next release)- for learning console only based linux

My planned system:
cpu- i5 3570k/ i5 4570k
motherboard-z77, or haswell equivalent (both with UEFI)
8GB of ram(with room to upgrade to 16GB)
Gtx 660/ Gtx 760 (with room for 2-way sli)
1 120GB ssd
1 1TB hard drive
cd burner is included

What i would like:
to install all three OS's on the 120GB ssd, using the hdd as storage for everything
a comprehensive guide to partitioning both storage devices
any suggestions to make this better in any way (will accept any solutions for problems, that could arise,
     so one or two OS's on the hdd is okay, but not great)

Because i have not purchased any of the key components, i can change this build to accommodate the multi-boot,
as long as it stays within a reasonable budget range of the original plan

I have searched the internet for a forum thread that answers all of my questions, did not find one, and was forced 
to make my own. As a complete noob to linux, i am asking you to give me specific solutions, spelled out as step by
step as possible. That being said, any help in any form is appreciated to the fullest extent. Thanks, Ubuntu forums!

---

### Post by oldfred on 2013-04-13
You do have to plan ahead. New motherboards are now UEFI with BIOS or CSM.
 Compatibility Support Module (CSM), which emulates a BIOS mode.

Windows only boots from gpt partitioned drives with UEFI. UEFI requires gpt partitioning.
Ubuntu will boot from gpt partitioning with either UEFI or BIOS if you have the correct partitions.

UEFI is the new way to boot, not as well understood, yet. But if you have your own build, you should not have all the secure boot issues that users with pre-installed Windows 8 have.
Windows 7 installer will boot with UEFI, but not from DVD you will have to convert to flash drive.
How you boot install media UEFI or BIOS mode for both Windows or Ubuntu is how it installs.

      
 Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

Windows in BIOS mode will read a gpt partitioned NTFS formatted partition, so you can make data drive gpt. Also gpt is required if drive is over 2.2TB.

---

### Post by zrdc28 on 2013-04-13
One suggestion let Slackware be the second distro due to the fact that it uses lilo instead of grub, grub2 will then pick up windows and slackware for 
the mbr.

---

### Post by DuckHook on 2013-04-13
1. Consider simplifying your boot setup (always a good thing in my opinion) by running Slackware as a VM inside Ubuntu. The additional ability to roll back to a snapshot makes learning (and breaking) the OS far less stressful. Since you are putting together new hardware, it will likely be more than powerful enough to run such a VM, and a CLI is not particularly resource intensive in any case.

2. If you go the VM route, also consider *arch*, *gentoo* (now there's a challenging one) and even *Ubuntu Server* to learn the command line. As VMs they would be a piece of cake to manipulate and administer and will expose you to the ways in which distros differ from each other.

---

### Post by HappyFishFace on 2013-04-14
> **DuckHook said:**
> 1. Consider simplifying your boot setup (always a good thing in my opinion) by running Slackware as a VM inside Ubuntu. The additional ability to roll back to a snapshot makes learning (and breaking) the OS far less stressful. Since you are putting together new hardware, it will likely be more than powerful enough to run such a VM, and a CLI is not particularly resource intensive in any case.

2. If you go the VM route, also consider *arch*, *gentoo* (now there's a challenging one) and even *Ubuntu Server* to learn the command line. As VMs they would be a piece of cake to manipulate and administer and will expose you to the ways in which distros differ from each other.

Okay, so if i do go the VM route, would that affect performance of either OS? 
Would i need to have more space for Ubuntu if i'm otherwise following a partitioning setup for a user with just Ubuntu and Windows?
And, i have looked at both arch and gentoo, and i think that slackware still does a bit more of what i'm looking for. Gentoo seems really complicated to set up(I'm not quite ready for that, and arch has set up stuff to have to know as well.), basically i want the stability slackware has, no rolling releases or stuff like that, so that i am the only thing that can mess up my Linux, and if it messes up it's my fault, i can find a reason for it messing up, and not do that again(better for learning).
Also, are there any other  cons to this that i should consider?(or more pros, for a more informed decision)

---

### Post by DuckHook on 2013-04-15
> **HappyFishFace said:**
> ...would that affect performance of either OS?

VMs will always run slower than bare metal. It's the nature of a VM. You are asking the system to do some pretty intense stuff running a virtual machine on top of an OS inside a real machine--so you have to expect some performance degradation. This is very noticeable on lower end HW, but you intend to build a pretty decent system, so I don't think you will have any issues unless you are trying to do things like gaming on your VM. A VM will not work well with really intensive graphical tasks. Stick to your dual booted Windows partition for that.

The host OS on which the VM runs will not be degraded except to the extent of the memory and CPU cycles that you carve off to the VM. However, a typical modern game is far more taxing on system resources than an idling VM, so the VM won't likely cause you any concerns on the host.

> Would i need to have more space for Ubuntu if i'm otherwise following a partitioning setup for a user with just Ubuntu and Windows?

You will definitely need to dedicate more space to Ubuntu if you intend on running VMs, but you will actually realize a net savings over your multi-boot alternative. This is because:

1. VMs are far easier to resize because they reside on files inside Ubuntu and are not installed onto their own separate and inflexible partition.
2. VM virtual disks can be created as a dynamic entity so that they take up as little room as possible initially and incrementally grow their size only as you add more data.
3. Due to their versatility, you can install as many OSes as you like and it's easy to delete those you no longer want. No partitioning required.

> ...i think that slackware still does a bit more of what i'm looking for. Gentoo seems really complicated to set up(I'm not quite ready for that, and arch has set up stuff to have to know as well.), basically i want the stability slackware has, no rolling releases or stuff like that, so that i am the only thing that can mess up my Linux, and if it messes up it's my fault, i can find a reason for it messing up, and not do that again(better for learning).

Now I see what you are looking for. I have the following VMs installed on my box--all using approximately 10 GB of HDD each:

Ubuntu minimal, Ubuntu 12.10, Bodhi, Debian, CrunchBang, Gentoo, Sabayon, Arch, Chakra, openSUSE, CentOS, Knoppix, Fedora, Slackware, Puppy, FreeBSD, Solaris, Minix and WinXP...

...(and I'm still collecting) all running on a rock-stable Ubuntu 12.04 host that I make absolutely no changes to except for updates and carefully reviewed upgrades. The whole lot takes up less than 300 GB of HDD, which is not much considering that I get to play with, learn and try to break almost 20 different OSes. For your stated purposes, I would recommend an Ubuntu minimal client because the commands you will learn are applicable to administering your host as well, but Slackware or Debian will do just fine. The point is: I couldn't possibly play with this many OSes if I had to install them into separate partitions.

When I intend to try out something really outrageous on an OS, I take a snapshot of my VM before jumping off the cliff. The 50% of the time that I bork my VM, I roll back to my previous snapshot and it's as if it never happened. Try doing that with a real OS installed on a partition.

BTW, you are correct. Arch is difficult and Gentoo is only for gurus, as the latter requires you to compile its kernel--not for the faint of heart. But, man, you won't learn more than you will trying to wrestle with it. And remember, salvation is only a snapshot away (which I've resorted to dozens of times).

In my opinion, the pluses far outweigh the minuses, but each person's circumstances are different. VMs are more complex, require better HW (which you have) and don't run as fast (which is a non-issue if they are to be used for learning), but they are insanely versatile, robust and safe and they don't involve monkeying around with your host, which is what most of the pleas for help on this forum arise from.

---

