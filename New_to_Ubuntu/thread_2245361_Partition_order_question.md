---
title: "Partition order question"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by kira-yamato-2008 on 2014-09-23
A very simple question. This only applies during the Windows installation, Specifically for Vista Home Premium.

In the installation window, are the partitions in the same order as they appear in Lubuntu/other linux distros?

I ask because this laptop has a cracked screen and the part where I could identify the partitions by their size or name isn't working. Plus for some odd reason the external monitor refuses to work naively on boot for this machine, when it doesn't have that problem on any other computer I've used it on.

---

### Post by yancek on 2014-09-23
If you mean is windows C:\ equivalent to sda1 on Linux.  I don't know but I would doubt it from my limited experience.  If you are trying to identify drive partitions, they should all have a UUID number and in Linux you can get it by using the command:  blkid
This will show the device:  /dev/sda1 UUID="long combo numbers/letters"

I'm sure there is a way to get this on windows that I am not aware of and you could compare them.

---

### Post by oldfred on 2014-09-23
Windows does not correctly see Linux partitions, so I also doubt that partitions would look the same. It may just show unallocated or nothing.

Also Windows may rewrite partition table on its install. And we have seen many cases where Windows in not seeing the Linux partition rewrites partition table without the Linux partition. Usually recoverable with testdisk but much better to create a backup of just the partition table after you have made all changes and then you could restore that if necessary.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by kira-yamato-2008 on 2014-09-23
All three partitions show as Partitions 0-2 on hard drive 0 on the set up screen. The unfortunate thing you pointed out to me oldfred is they might not be displayed properly. Which may or may not be the case, but I can't tell, because the part of the screen where I could read that is busted. So I'm either going to have to slap the HDD into the Toshiba which does boot to the external monitor and install on that, or wait, save all my files to an external hard drive when I can afford it, and just reformat the whole hard drive and start from scratch.  Thanks anyways.

---

### Post by nerdtron on 2014-09-23
And when dealing with hard drive partitions, I always refer to the partition sizes and not their names. That said, I don't make the same 2 partition with almost identical size so that when I go and choose partitions whenever I install an OS (windows or Linux) I know which partition I need to assign to each.

---

### Post by Pelvur on 2014-09-24
I had a similar problem with broken screen some years ago, and for external monitor to work on boot, I disconnected the laptop screen from... whatever it is connected to with this wide grey flat cable. Then connected laptop to TV through VGA, and it worked fine, I was able to see the screen from boot start.

---

### Post by kira-yamato-2008 on 2014-09-24
What type of computer was it? Mine is a HP G60-120US and I haven't heard of any successful attempts at this.

---

### Post by Mark Phelps on 2014-09-24
> In the installation window, are the partitions in the same order as they appear in Lubuntu/other linux distros?

While the partitions are in a fixed order on the drive, the order in which they are displayed depends on the app being used.

What will show them in the same order as they are physically is the Minitool Partition Wizard Boot CD.  This is a Windows-based partitioning tool you can download for free and burn to CD.  When you boot from that, you will see all the partitions on the drive, including the Linux filesystem partitions.

---

### Post by oldfred on 2014-09-24
You can always run the bootinfoscript to have a copy.
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or run Boot-Repairs summary report which also uses bootinfoscript as part of its report.
      
       
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kira-yamato-2008 on 2014-09-25
Disconnecting my laptop's built-in monitor allowed windows install to boot to the external monitor, but now I have an entirely different problem...

---

