---
title: "live installation query"
date: 2024-04-24
forum: New to Ubuntu
---

### Post by Dave.E on 2024-04-24
Hi.
I have a spare empty hard drive in my system which I want to use to try out UBUNTU.
So I booted from a live USB stick and from the install option used the 'something else' option to specify my disk.
I set a partition for a 16GB swap and the rest ext4 for the system.
I selected the same drive for the bootloader information, and then I clicked continue.

This is where the warning comes before the actual installation.

The partition of the following devices are changed:
SCSI3 (0,0,0) (sdb)  [which is the drive I want to install on]

The following partitions are going to be formatted:
Partition #7 of /dev/nvme0n1 as swap
Partition #1 of SCSI3 (0,0,0) (sdb) as swap
Partition #2 of SCSI3 (0,0,0) (sdb) as ext4

The thing is I never meantioned anything about wanting to use the already existing swap on nvme0n1 !!!!
How come it thinks it's going to format that? Especially when I've already assigned a swap for it to use???

So I didn't dare let it continue unless it damages an existing system.

All help gratefully received.

---

### Post by guiverc on 2024-04-24
You mention Ubuntu, but not which Ubuntu product (Server? Desktop? Core?) nor which release you're using, nor if using a release that has ISO choices at download which you opted to use.

Ubuntu 23.10 Server uses one installer for example (`subiquity`); Ubuntu 23.10 Desktop has two ISO choices that use different installers (*you select which you'll use at download time by which ISO you download; either `ubuntu-desktop-installer` or `ubiquity`*).

You've not said which *installer* you're thus using. You're not expected to know the name, but its helpful if you give us enough details that we know which you're talking about, and we can't really *guess* given we don't know what Ubuntu product, nor release details. Whilst "*Something else*" makes me think of an `ubiquity` installer,  you maybe using a different one.  It's best if you just tell us what are you using.

Are you asking about Ubuntu 23.10 Server?   Ubuntu 23.10 Desktop? etc.

FYI:  You can use multiple swap partitions, and even swap partition + swapfile.

---

### Post by Dave.E on 2024-04-24
The USB drive says it's Ubuntu 22.04.4 LTS amd64
If you let me know how I find out any other information you want I'll be happy to get it..

Or maybe I should download a different live boot?
The way I found it was to google search for "Download Ubuntu"
Which took me to a page where the live ISO was. 
I didn't see lots of differing options.
I saw :
"[COLOR=#000000][FONT=&quot]The latest [/FONT][/COLOR]LTS[COLOR=#000000][FONT=&quot] version of Ubuntu, for desktop PCs and laptops. LTS stands for long-term support &#8212; which means five years of free security and maintenance updates, extended to 10 years with [/FONT][/COLOR][Ubuntu Pro]("https://ubuntu.com/pro")[COLOR=#000000][FONT=&quot]."[/FONT][/COLOR]
I'm happy to be advised.

I'm not deliberately holding anything back from you. 
I don't know what is OK and what isn't OK. I just don't want to damage my existing systems.

You said : "[COLOR=#000000]FYI: You can use multiple swap partitions, and even swap partition + swapfile."
[/COLOR]
I'm just concerned that I wanted to keep this UBUNTU OS away from all my other systems and as I'd not mentioned any other systems AND used the option 'something else' which is supposed to allow me to specify what to use rather than UBUNTU choosing what to use, why is it looking to format a partition on a different system that I've not mentioned in my choices?

---

### Post by tea for one on 2024-04-24
> **Dave.E said:**
> I don't know what is OK and what isn't OK. I just don't want to damage my existing systems.
Isolate, de-activate or physically remove disks, which you do not want to be "damaged"
Only have the _target_ disk visible.
Allow the Ubuntu installer to create the necessary partitions (inc a swap file rather than a swap partition)

Hopefully, your existing systems are UEFI mode?

---

### Post by Impavidus on 2024-04-24
Unless you use hibernation (which isn't recommended), the swap isn't used when the system isn't running. It's normal to share one swap partition among multiple operating systems (and one reason to use a swap partition instead of a swap file). In fact, the live system may use the swap partition as soon as it detects one. If you really care, you can prevent an OS from using a particular swap by editing the /etc/fstab after installation. But normally, you shouldn't care.

BTW, 16GB is huge for swap.

---

### Post by Dave.E on 2024-04-24
You're a mind reader 'tea for one'
I sorted it myself by removing the SSD card from the PC so UBUNTU couldn't see it during the installation process.
That solved the problem!
But it's good to know others think alike!

---

### Post by MAFoElffen on 2024-04-27
I know a few things...

The definitive way to tell if an Ubuntu ISO image is Desktop or Server...

Mount the ISO image > Open Folder ".disk" > read file "info"...

The text contained in that file is a one liner. If the first column value is "Ubuntu ", then it is a Desktop Edition ISO. If the first column value is "Ubuntu-Server ", then it is a Server Edition ISO.

The last column is the build-date. In between those is the release info, "-" separator, and arch.

EDIT -
There are other ways to interpret which ISO type it is, from what is there, but that file just plainly "tells you" what it is.

It's my understanding, that the installer uses that info from that file in the ISO, during the install, to populate the /var/log/installer/media-info file to tell it which ISO a system was installed by.

---

