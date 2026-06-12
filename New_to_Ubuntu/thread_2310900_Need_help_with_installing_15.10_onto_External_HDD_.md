---
title: "Need help with installing 15.10 onto External HDD/ Partition Offset"
date: 2016-01-22
forum: New to Ubuntu
---

### Post by syzygy2 on 2016-01-22
Hi Guys,

I am working on a project that requires linux, so I recently bought a seagate 1TB External HDD to install ubuntu onto. I've been following this guide: [http://linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/](http://linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/)

Everything is fine until I click install now where I get this (picture from phone, very large):

[http://i.imgur.com/jPyfUTl.jpg](http://i.imgur.com/jPyfUTl.jpg)

I've tried googling this problem, I keep finding the following link: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

But it just explains the problem, and any proposed solution is to run programs on terminal but I do not know how to do that from here. Does anyone know the easiest way to make it so it fixes this? 

The picture I posted above shows I wanted to use 700GB for ubuntu and a 10GB swap (I know this is a lot, my friend did this too with his 1TB external hdd.)

Also is there anyway to use the remaining free space 290 gb for regular storage?

Thanks for any help.

---

### Post by Herdo on 2016-01-23
Can you type out the full error message, or take another picture?  It's cut off and I can't read the left side of it.

It seems that your hard drive uses 4096 byte sectors rather than the standard 512 byte sectors.  From what I've read though, Linux has supported this for quite some time, so I'm not entirely sure what is happening here.

Have you tried simply recreating the partitions?  Try it again, but this time create the swap partition first, and make sure "Beginning of this space" is selected.  Then the "/" folder, and again "Beginning of this space" selected.

---

### Post by syzygy2 on 2016-01-23
Hey, thanks for your response.

I have tried remaking the partitions and even remade them with trying different sizes, but nothing worked.

I just tried your suggestion of changing the order in which i make them, but it didnt help/

Here is an image of the full error message, but I think you already filled in the blanks

[http://i.imgur.com/i3blQF1.jpg](http://i.imgur.com/i3blQF1.jpg)

I'm going to bed now, I'll check back in the morning

---

### Post by oldfred on 2016-01-24
From live installer use gparted to view & possibly create partitions.
Also if drive will be external or never boot Windows you can use the improved gpt partitioning scheme not the 35 year old MBR(msdos). But that requires an additional small 1MB unformatted partition with the bios_grub flag to let grub install correctly to sdb drive.

       If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

Was this sold as a backup drive? Some of those have hidden partitions, with Windows backup software or other special/non-standard features. If a bare drive in a caddy, it should be ok.

---

### Post by syzygy2 on 2016-01-24
My helped me use gparted, it works now, thanks.

---

