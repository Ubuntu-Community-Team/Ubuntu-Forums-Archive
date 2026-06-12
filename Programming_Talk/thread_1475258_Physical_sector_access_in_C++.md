---
title: "Physical sector access in C++"
date: 2010-05-06
forum: Programming Talk
---

### Post by erhicks on 2010-05-06
I am a new user of this forum and an experienced programmer in asm, c, c++, and c#.  We are jsut now starting to support Linux in our environment.  I have a tool that I wrote in C++ in Windows that reads and writes private data stored in the hidden sectors inthe first track of the hard drive.  The problem is that I need to recompile this tool to run in Linux Ubuntu 10.04.  The program compiles and runs (sort of) but I could not find any way to access the hidden sectors.  Specifically, I could not find a replacement for CreateFile(), ReadFile(), WriteFile(), or SetFilePointer() that I use to create a file of the //./PHYSICALDRIVE.  Does anyone know how to read and write physical sectors in Ubuntu.
 
Thanks
- Evan

---

### Post by Iowan on 2010-05-06
Moved to Programming Talk...

---

### Post by srs5694 on 2010-05-06
You need to access the Linux physical device file, such as /dev/sda or /dev/sdb. You can do this with ordinary Unix C or C++ file access commands, such as open(), close(), etc. If you want to see some actual code, you could download the source tarball for my [GPT fdisk.](https://sourceforge.net/projects/gptfdisk/files/) The diskio-unix.cc file has the Unix file I/O code, while diskio-windows.cc contains equivalent Windows code. There are other ways to do this, of course; I used the commands I did because they support 64-bit file pointers, which are critical for GPT.

Incidentally, anything that stores data in the sectors immediately following the MBR will fail miserably, and perhaps cause serious damage, on any computer that uses the GUID Partition Table (GPT) partitioning system. Although GPT is still fairly rare, it's likely to become extremely important fairly soon, once disks bigger than 2TiB are released. Even on MBR disks, the Linux GRUB boot loader sometimes stores data there, so a tool that mucks with those sectors is risky on Linux, unless perhaps it's another boot loader that can do what GRUB does.

---

### Post by erhicks on 2010-05-07
Thank you for your response and link to your code.  I have downloaded the source and am currently examining the files.  There is no fear of bumping into GRUB because Linux and GRUB are installed into partition 3 on a drive with 3 primary partitions and 1 extended partition.  The sectors I use are 3 and 5-9 on the first track of the drive.
 
Thanks again
-Evan

---

