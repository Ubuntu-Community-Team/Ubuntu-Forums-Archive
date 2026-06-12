---
title: "install ubuntu 16.04 in a win 7 laptop but want to use windows drives"
date: 2017-08-19
forum: New to Ubuntu
---

### Post by nabilnur on 2017-08-19
Hi all,

I'm using win 7 currently. Now i want to install ubuntu 16.04 LTS version. But in existing system i have 4 partition like C,D,E,F. What my desire is i want to install ubuntu in C drive. But want to keep D,E,F drive intact so that there will be no data loose. I don't want to keep double OS in my laptop, rather i want to keep the ubuntu using C drive. Please let me know if it's possible or not.

---

### Post by westie457 on 2017-08-19
Hello nabilnur and welcome to Ubuntu Forums.

To answer your question. Yes it is possible.

The recommended way for what you want is to use a virtual machine, one example of virtual machine software is VirtualBox. There are others however I have never used them so cannot comment on them.

You can get VirtualBox from here. [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by Impavidus on 2017-08-19
A virtual machine if you want to run Ubuntu inside Windows.

If you want to get rid of Windows, you can install Ubuntu on the partition currently known as C. Run the installer, when it asks what you want to do (use whole disk, install alongside, ...), choose "something else", which is manual partitioning. Then install on the C partition, which will not be known as C to the installer. Look at the partition sizes and order.

However, this is all a bit tricky and when you make an error, all stuff on your current D, E and F partitions may be gone. So make sure you've got backups on a different and unplugged drive. And although Ubuntu can read and write NTFS partitions, it isn't good at fixing them so it's not recommended to use NTFS when you don't use Windows.

---

### Post by nabilnur on 2017-08-19
Hi,
Actually i want to get rid of that. Thus, i followed one dual boot tutorial in youtube which creates another problem. My goal is-

1. Just use current C drive for ubuntu without hampering any data or you can say i don't want to loose any data
2. Don't have data back up option so need to keep my d,e and f drive intact
3. while trying dual boot options i  did shrink and make some space which named unusedspace not freespace shown as in tutorial. And when trying to use that for installing getting error.

Looking for all helpful suggestion.

---

### Post by Autodave on 2017-08-19
You NEED to get everything backed up FIRST!  I have installed Linux probably over 100 times and I never do it before backing up. I rarely have problems. I said "rarely", not "never". There is always that chance. And since you have never done this before, you need to back up everything first.

---

### Post by Autodave on 2017-08-19
When you shrunk a partition, the space that you created: did you create a partition in that space?  Is "fast boot" disabled in your BIOS? Was your Win7 on legacy or UEFI boot?

---

### Post by yancek on 2017-08-19
The "C" drive on windows is the windows system partition.  You can't install Ubuntu or another Linux OS on a windows fileystem partition.  There was a program called "Wubi" which did that, installing Ubuntu as a program within windows.  It has not been supported for years so if you want Ubuntu on a windows system you will need to use some type of virtual software, VirtualBox, VMWare, etc.

In your last post you indicate that when you try to install Ubuntu you get an error but do not say what that error is?

---

### Post by nabilnur on 2017-08-19
The error is "No root fie system defined. Please correct this from partitioning menu". Sorry i don't find any image attachment option here. For this error i don't even find any partition menu as well. Aside, i used "RUFUS" portable version to create bootable USB. Hope it gives some idea about where i'm doing it wrong.

---

### Post by oldos2er on 2017-08-19
> **nabilnur said:**
> Sorry i don't find any image attachment option here. 

Use the advanced editor, click the paper clip icon to attach an image.

> Just use current C drive for ubuntu without hampering any data

Not possible. Linux needs to use a native file system such as ext4; NTFS doesn't support Unix file permissions (among other reasons) so it can't be used.

---

### Post by nabilnur on 2017-08-19
hi this is the error i'm receiving. u can see when i'm clicking on "unusable space" there is no option coming to make partition with ext4.
aside i found in tutorial the space is rather named as "freespace" while i'm getting here "unusablespace" so i'm worried about that also.
[ATTACH=CONFIG]276451[/ATTACH]

---

### Post by vocx on 2017-08-19
> **westie457 said:**
> 
&#8203;To answer your question. Yes it is possible.

The recommended way for what you want is **to use a virtual machine,** ...


> **yancek said:**
> 
The "C" drive on windows is the windows system partition.**  You can't install Ubuntu or another Linux OS on a windows fileystem partition**...


> **oldos2er said:**
> 
**Not possible. **Linux needs to use a native file system such as ext4; NTFS doesn't support Unix file permissions (among other reasons) so it can't be used.


Guys, I think you are misunderstanding. He does not want to install Ubuntu inside the "C drive". He wants to replace completely Windows in the C drive.

> **nabilnur said:**
> Hi,
**Actually i want to get rid of that.** Thus, i followed one dual boot tutorial in youtube which creates another problem. My goal is-

1. **Just use current C drive for ubuntu** without hampering any data or you can say i don't want to loose any data


> **nabilnur said:**
> hi this is the error i'm receiving. u can see when i'm clicking on "unusable space" there is no option coming to make partition with ext4.
aside i found in tutorial the space is rather named as "freespace" while i'm getting here "unusablespace" so i'm worried about that also.

Basically, you have five partitions. One of the partitions is an extended partition, which only works to contain one of the real partitions.

```

/dev/sda1   This seems to be the Windows boot partition, maybe drive D
/dev/sda2   This seems to be the Windows C drive
/dev/sda3   This could be the Windows E drive
/dev/sda5   This could be the extended partition containing the Windows F drive
/dev/sda6   This could be the actual Windows F drive

```

To know which is which exactly, you need to check in Windows the sizes of each "drive" C, D, E, F, and then check the Ubuntu installer, and verify the sizes of the partitions. In Ubuntu, you don't refer to them as "drives", or C, D, E, F, etc. They are "partitions", and each partition has a "mount point", which is the directory where that information will be placed in your installed system.

If you want to install Ubuntu on top of the C drive, you don't need to create "free space". You can just select the second partition "/dev/sda2", and choose "Format". Then the installer will overwrite Windows there, and format the partition from the NTFS file system to ext4 file system, which is what Ubuntu uses. **Double check this step!** If you format the wrong partition, you will erase the data that you don't want to erase.

You also have to select the "root mount point". The error message tells you you have not chosen this mount point. This refers to the root of the file structure hierarchy.

You click where it says "Mount point" and select the forward slash, or "/".

This symbol is the "root mount point" or base of your directories. Every other directory becomes a "branch" of that "root" mount point.
```

/
|
|--/home/user
|
|--/media
|
|--/mnt/driveD
|--/mnt/driveE
|--/mnt/driveF

```

The other partitions, those that you don't want to erase, can have themselves a mount point. They do not need to be formatted. The mount point can be chosen freely, for example, as I did above.
```

/dev/sda2    /mnt/driveD
/dev/sda3    /mnt/driveE
/dev/sda6    /mnt/driveF

```

---

### Post by Impavidus on 2017-08-20
> **nabilnur said:**
> 
2. Don't have data back up option so need to keep my d,e and f drive intact

Then get a backup option. External hard drives aren't free (usually), but not overly expensive either. One day you will need those backups.

sda1 seems to be a boot partition, possibly hidden by your Windows tools. sda2, sda3, sda5 and sda6 are your C, D, E and F partitions, not necessarily in that order. sda5 and sda6 are logical partitions, located in the extended partition sda4 (not listed by the partitioning tool of the installer). You can have at most 4 primary partitions, which are sda1, sda2, sda3 and sda4, so if you want to make any more partitions, they have to be logical partitions, which can only be made adjacent to your current sda5 or sda6. That explains why your unallocated space between sda2 and sda3 is unusable.

So first make backups. Then, from that posted screenshot, you can select your current C partition. Change partition type to ext4, make sure it's marked to format and set the mount point to /. That defines your root file system. Also make sure the other partitions are not marked to format. Then you should be able to install Ubuntu while keeping your files on D, E and F. But keep in mind that having NTFS data partitions on a Linux-only computer is not really recommended.

---

### Post by kurt18947 on 2017-08-20
I will echo the requirement to have functional backups of at least your important files/folders. High capacity flash drives are pretty cheap these days. DVDs are cheap but slow, it depends on how much data you have. It's all too easy to confuse the partitions and delete or overwrite the wrong partition. How do I know this? Well.......... :oops:

---

### Post by JKyleOKC on 2017-08-20
I note that you're in the USA -- firms such as Office Depot/OfficeMax sell external drives such as the Western Digital Passport series at ridiculously low prices. I paid less than $100 for the 1-terabyte (1,024 gigabytes) drive I got to protect my wife'sw Win10 system. They come with built-in software (runhs on Windows only though) to do the backup, and can back up your entire hard drive in just a few hours. As others have said, you WILL eventually need the backup copy of your essential data files.

---

### Post by nabilnur on 2017-08-20
Dear All,
Thanks for all of your advise. But unfortunately i'm still stuck on the same position. Hope you u will help me further to resolve this issue.

---

### Post by oldos2er on 2017-08-20
I believe you would right-click on the "unusable" space, choose 'Edit' or 'Change' (sorry, I forget the exact wording), then from a drop-down menu select / as the mount point, and format is as ext4. This WILL destroy any existing data on the partition.

---

### Post by Impavidus on 2017-08-21
The unusable space is indeed unusable in the sense that you can't create a new partition there. It's not in or adjacent to the extended partition and OP has hit the 4 primary partition limit. It is possible to expand sda2 or sda3 into the unusable space.

What's the problem with my post #12, third paragraph? Select the partition, click the "Change..." button. If you have difficulty identifying your C partition, use the Windows disk management utility to see the order of the partitions on the disk. You can also compare the sizes, but 3 of the 4 partitions have the same size, so that may not be enough. The installer seems to report sizes in MB and GB, the Windows tool might use MiB and GiB (but may call them MB and GB nonetheless), so you may have to convert units. 1MiB=1.048576MB, 1GiB=1.073741824GB.

But I repeat that you should first make backups and that it's not recommended to use NTFS partitions on the internal drive of a Linux-only computer. It's possible, but less reliable.

---

