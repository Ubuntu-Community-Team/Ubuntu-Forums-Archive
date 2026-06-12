---
title: "Identifying a SPECIFIC Partition"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by fracas on 2012-04-02
Ladies and Gentlemen:

I’m an ancient fellow with minimal computer expertise who would like to try Ubuntu 10.10.  I have searched extensively and have found various posts which talk around my problem, but do not specifically address it.  I hope you can help.

My PC (running WinXP Home) has two (2) HDDs each of which have three (3) partitions.  I want to install Ubuntu to a _specific _partition.  When I get to the installation selection screen, I see entries like /dev/sda1, /dev/sda2, /dev/sda3, etc. (these are not the exact entries, only examples – I did not want to go through the futile installation process again to copy my list).  I used Partition Magic to note the used and unused MBs on each partition of my HDDs – but the figures do not match those displayed by Ubuntu!

The bottom line is this – how in the world do I identify partitions C through I when viewing “/dev/sda1, /dev/sda2, /dev/sda3, etc.”?  Is there a “trick” I have missed? 

Thanks in advance for your response.

---

### Post by santosh83 on 2012-04-02
> **fracas said:**
> Ladies and Gentlemen:

I&#8217;m an ancient fellow with minimal computer expertise who would like to try Ubuntu 10.10.  I have searched extensively and have found various posts which talk around my problem, but do not specifically address it.  I hope you can help.

My PC (running WinXP Home) has two (2) HDDs each of which have three (3) partitions.  I want to install Ubuntu to a _specific _partition.  When I get to the installation selection screen, I see entries like /dev/sda1, /dev/sda2, /dev/sda3, etc. (these are not the exact entries, only examples &#8211; I did not want to go through the futile installation process again to copy my list).  I used Partition Magic to note the used and unused MBs on each partition of my HDDs &#8211; but the figures do not match those displayed by Ubuntu!

The bottom line is this &#8211; how in the world do I identify partitions C through I when viewing &#8220;/dev/sda1, /dev/sda2, /dev/sda3, etc.&#8221;?  Is there a &#8220;trick&#8221; I have missed? 

Thanks in advance for your response.

You can usually work it out from observing the order of the partitions that a partition manager within Windows (including the default Microsoft supplied one in MMC) displays and correlate this with what Ubuntu displays. Factors you can use for correlation are partition size, partition ID, filesystem type, used/free space (though this is an unreliable metric), and volume label/ID.

Its best to note these down on a piece of paper, first as displayed by Windows itself, then what Ubuntu installation/LiveCD shows. If there's a volume label, then that by itself is usually enough to uniquely identify all the formatted partitions.

Way back around 2004 I used to triple or quadruple boot Windows, Red Hat, Mandrake and FreeDOS with over 15 partitions. It's a bother to keep track of all these, especially around installation/re-installation periods, but you can do it with a little patience. :-)

---

### Post by sudodus on 2012-04-02
> **santosh83 said:**
> ... If there's a volume label, then that by itself is usually enough to uniquely identify all the formatted partitions...
+1 for labels

You can boot from your Ubuntu install drive and run ***gparted*** to make human readable labels on all partitions (except the swap partition, I don't think it works on that one).

for example: winxp, ubuntu, data, ...

By the way, Ubuntu 10.10 is getting old and close to end of support. I suggest that you try either 10.04 LTS (long time support), 11.10 or 12.04 LTS (which is now 'Precise beta', to be officially release before the end of this month April 2012).

---

### Post by santosh83 on 2012-04-02
> **sudodus said:**
> +1 for labels

You can boot from your Ubuntu install drive and run ***gparted*** to make human readable labels on all partitions (except the swap partition, I don't think it works on that one).

for example: winxp, ubuntu, data, ...

By the way, Ubuntu 10.10 is getting old and close to end of support. I suggest that you try either 10.04 LTS (long time support), 11.10 or 12.04 LTS (which is now 'Precise beta', to be officially release before the end of this month April 2012).

But swap does support UUID, though I don't know if a Linux created UUID is recognisable under Windows tools.

Yes Meerkat is nearing mummification! But I'm loath to update it for a variety of reasons, chiefly the hardware itself is nearing its end, so I'd prefer beginning with 12.04 on new hardware, but that is still a few months away! I'm looking to upgrade when 12.04's first point release comes out during July.

---

### Post by sudodus on 2012-04-02
> **santosh83 said:**
> But swap does support UUID, though I don't know if a Linux created UUID is recognisable under Windows tools.

Yes Meerkat is nearing mummification! But I'm loath to update it for a variety of reasons, chiefly the hardware itself is nearing its end, so I'd prefer beginning with 12.04 on new hardware, but that is still a few months away! I'm looking to upgrade when 12.04's first point release comes out during July.
Yes, Ubuntu identifies the swap partition by UUID. And I think it is enough to label all the other partitions, so it will be obvious which partition is the swap one, and Windows doesn't use it or mount it anyway :-)

---

### Post by flemur13013 on 2012-04-02
[quote] I used Partition Magic to note ... [\n]

Partition Wizard is better - and they have a boot/partitioning disk (all free).  If you ever get things going, don't use the linux tools for changing/editing Windows partitions;  use Partition magic or P-Wizard.

Anyway: [B]label all your partitions!  
[/B]
I know you have to know what they are before you can give them meaningful labels, but it sure makes things easier. 

If you boot from a Windows install/repair CD or Bart CD, the windows drive letters will likely be different; what would normally be your C: drive could be called F:  Using labels helps you keep it all straight.

The labels will show up in both windows and linux (tho windows normally can't deal with linux ext partitions).  And in linux if you mount a drive (USB disk or whatever) that's not in /etc/fstab, it'll mount to /media/disk_label.

---

### Post by critin on 2012-04-02
> **fracas said:**
> Ladies and Gentlemen:

I&#8217;m an ancient fellow with minimal computer expertise who would like to try Ubuntu 10.10.  I have searched extensively and have found various posts which talk around my problem, but do not specifically address it.  I hope you can help.

My PC (running WinXP Home) has two (2) HDDs each of which have three (3) partitions.  I want to install Ubuntu to a _specific _partition.  When I get to the installation selection screen, I see entries like /dev/sda1, /dev/sda2, /dev/sda3, etc. (these are not the exact entries, only examples &#8211; I did not want to go through the futile installation process again to copy my list).  I used Partition Magic to note the used and unused MBs on each partition of my HDDs &#8211; but the figures do not match those displayed by Ubuntu!

The bottom line is this &#8211; how in the world do I identify partitions C through I when viewing &#8220;/dev/sda1, /dev/sda2, /dev/sda3, etc.&#8221;?  Is there a &#8220;trick&#8221; I have missed? 

Thanks in advance for your response.

Windows uses NTFS, so a partition that shows this is  Windows.  Don't use this one.

Does the second hard drive have an operating system on it or what?  The specific partition is one you have prepared especially for ubuntu, or is it unallocated/empty space?  If it's empty it will say that and you can find it easily.

On the screen where you choose to install, these things will show so you can choose.

The first hard disk is usually dev/sda,.  The partitions are dev/sda1, dev/sda2, 

 the second hd is dev/sdb, with partitions as  dev/sdb1 dev/sdb2  (on linux)    [COLOR=Red]Notice the change from a to b. [/COLOR] The numbers are each separate partition on its hdd. 

The installer will show your disks then you choose the one you want, then click the partition you want.

---

### Post by flemur13013 on 2012-04-02
My Free Advice about installing: **put windows and linux on separate physical DISKS.**

If you look thru these forums you'll find a LOT of posts about "ubuntu ate my windows installation" or "I fixed my windows boot and now linux is gone" and such.  Grub(2) is not really friendly to use, and windows pretends linux doesn't exist.

Here's what I do, and I find it very preferable to having windows and linux on different partitions on one disk:

0 - Backup your data.
1 - Connect one physical disk, disconnect all others.
2 - Install OS1 on it.
3 - Connect a different disk, disconnect all others.
4 - Install OS2.
5 - Connect both disks, boot and select OS1 or OS2 disk from BIOS.

Or, if you already have windows installed, shutdown the machine, disconnect the disk with windows, and install linux to the other disk.  After you know it's working, connect both disks (don't forget about possible master/slave settings).
Linux will be able to see your windows partitions.

With separate disks Windows can't screw up grub and hence the linux boot, and linux doesn't have to know anything about Windows.

Now you choose your boot OS via BIOS by selecting the boot disk.

---

### Post by santosh83 on 2012-04-02
> **flemur13013 said:**
> My Free Advice about installing: **put windows and linux on separate physical DISKS.**

If you look thru these forums you'll find a LOT of posts about "ubuntu ate my windows installation" or "I fixed my windows boot and now linux is gone" and such.  Grub(2) is not really friendly to use, and windows pretends linux doesn't exist.

Here's what I do, and I find it very preferable to having windows and linux on different partitions on one disk:

0 - Backup your data.
1 - Connect one physical disk, disconnect all others.
2 - Install OS1 on it.
3 - Connect a different disk, disconnect all others.
4 - Install OS2.
5 - Connect both disks, boot and select OS1 or OS2 disk from BIOS.

Or, if you already have windows installed, shutdown the machine, disconnect the disk with windows, and install linux to the other disk.  After you know it's working, connect both disks (don't forget about possible master/slave settings).
Linux will be able to see your windows partitions.

With separate disks Windows can't screw up grub and hence the linux boot, and linux doesn't have to know anything about Windows.

Now you choose your boot OS via BIOS by selecting the boot disk.

Just adding to what you said, in this setup you still need to setup grub to boot Windows as an option I suppose. Switching through the BIOS each time your system starts is cumbersome. Therefore you have to install Linux with the Windows HD connected to system, or Linux installer will not be able to add the appropriate option to grub config file, or you must update-grub after connecting both disks and booting into Linux.
:-)

---

### Post by oldfred on 2012-04-02
You can run several command that give clues. NTFS is a Windows formated partition, so Windows will have to be in a NTFS (or if really old maybe FAT32).

sudo fdisk -lu

If you have mounted partition either directly with fstab or just by clicking on it in Nautilus this will show use:
df -H

If you have labeled partitions this gives UUID & label

sudo blkid

If you really want to know all the details at once, but may be too much info, boot info script essentially runs all the above commands and parses MBR and partition boot sectors and outputs a formated report. It will show the Windows boot files in the Windows parititon.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by fracas on 2012-04-03
Folks:

Thanks for all the input.  I was serious when I said I was old and less than an pc expert.  I have read and re-read all of your comments and some of it is still &#8220;rocket science&#8221; to me. I liked flemur13013&#8217;s procedure for disconnecting HDDs until I noted that I would have to go into the BIOS to access either OS.  I haven&#8217;t read enough to have noted that Ubuntu &#8220;eats&#8221; Windows &#8211; I absolutely do not want to risk having to reinstall XP unnecessarily!  Critin&#8217;s comment helped &#8211; at least I can tell which HDD is which, but identifying the partitions still eludes me (see comment re sizes below). Thus, I have a few additional questions:

Will installing Ubuntu on the HDD that DOES NOT contain XP positively prevent Ubuntu from harming my Windows installation?

My partitions are labeled (&#8220;named&#8221;).  How do I make Ubuntu display the labels?  I appears that I input a command(s).  If that is so, where & how do I input the command(s) to display the partition labels and other information ?

Just an observation, not really an Ubuntu question, but somewhat disturbing.  I used XP&#8217;s Disk Mgmt., Partition Magic and Partition Wizard and each program reported different GB counts, some differences were major.  This is not very helpful&#8230;

Again, thank you all.

---

### Post by santosh83 on 2012-04-03
> **fracas said:**
> Folks:

Thanks for all the input.  I was serious when I said I was old and less than an pc expert.  I have read and re-read all of your comments and some of it is still “rocket science” to me. I liked flemur13013’s procedure for disconnecting HDDs until I noted that I would have to go into the BIOS to access either OS.  I haven’t read enough to have noted that Ubuntu “eats” Windows – I absolutely do not want to risk having to reinstall XP unnecessarily!  Critin’s comment helped – at least I can tell which HDD is which, but identifying the partitions still eludes me (see comment re sizes below). Thus, I have a few additional questions:

Will installing Ubuntu on the HDD that DOES NOT contain XP positively prevent Ubuntu from harming my Windows installation?

Yes it should be safe, provided during the partitioning stage you do not give any instructions to Ubuntu to format anything on the Windows HDD. Setting it up to be automatically mounted (i.e. connected) to your Linux system will not harm it in any way though.

But writing to NTFS partitions from Linux is still not a 100% foolproof thing yet, but merely reading is okay.


> My partitions are labeled (“named”).  How do I make Ubuntu display the labels?  I appears that I input a command(s).  If that is so, where & how do I input the command(s) to display the partition labels and other information ?

The graphical partitioning program Ubuntu uses (GParted) will display the label of each partition (among other details) when you right-click on it and select 'Information' from the menu.

> Just an observation, not really an Ubuntu question, but somewhat disturbing.  I used XP’s Disk Mgmt., Partition Magic and Partition Wizard and each program reported different GB counts, some differences were major.  This is not very helpful…

Again, thank you all.


While small differences are expected, they shouldn't differ by gigabytes or more I think!

Anyway, since partitioning is always a bit challenging to everyone, installing Linux onto a separate HDD is good, if its possible for you, otherwise have you considered [WUBI]("https://wiki.ubuntu.com/WubiGuide") as an alternative option?

---

### Post by fracas on 2012-04-04
Folks:

I bit the bullet and learned and used gparted to identify my partitions by labels.  Attempted _again _to install Ubuntu to the desired HDD and specific partition.  I selected the same HDD and specific partition for the boot loader.  What happens?  I&#8217;m told &#8220;no root file defined &#8211; correct from partitioning menu&#8221;.

Sorry, but this is too much for my skills.  I guess that installing this OS along side of XP would be easier than what I wish to do &#8211; but there it is.  Maybe down the road a new version will simplify a non-standard installation.  Right now, however, this is frustrating me to the point of abandonment.

I am grateful for all of the assistance, but I think I&#8217;m a little to far behind the curve &#8230;

---

### Post by sudodus on 2012-04-04
> **fracas said:**
> Folks:

I bit the bullet and learned and used gparted to identify my partitions by labels.  Attempted _again _to install Ubuntu to the desired HDD and specific partition.  I selected the same HDD and specific partition for the boot loader.  What happens?  I&#8217;m told &#8220;no root file defined &#8211; correct from partitioning menu&#8221;.

Sorry, but this is too much for my skills.  I guess that installing this OS along side of XP would be easier than what I wish to do &#8211; but there it is.  Maybe down the road a new version will simplify a non-standard installation.  Right now, however, this is frustrating me to the point of abandonment.

I am grateful for all of the assistance, but I think I&#8217;m a little to far behind the curve &#8230;
Don't give up yet, I think you are close to success :KS

You should select the specific partition for your root file system **[COLOR="Red"]/[/COLOR]** but the boot loader (grub) should be installed to the drive 'head', not to a partition. For example if you have only one internal drive it is /dev/sda.
Let us say you use /dev/sda5 as your root partition **[COLOR="red"]/[/COLOR]**. Then you should ***not*** use that for grub. Instead install grub to /dev/sda (the drive, not to a partition).

---

### Post by fracas on 2012-04-05
Sudodus:

I tried all of the options for installing the boot loader except the one where XP is resides.  I assume this is where I would have to install &#8216;grub&#8217;.  I fear installing anything here.  Additionally, it is no doubt obvious that my knowledge of partitions and partitioning is almost nil.  What I think I will feel most comfortable with is exploring Ubuntu from my disk and continue to educate myself concerning partitions and Ubuntu.

I really appreciate you sticking with me through this.  This thread ought to be labeled &#8220;Incomplete Installation Due To Operator Anxiety&#8221;&#8230;

Thanks again.

---

### Post by sudodus on 2012-04-05
> **fracas said:**
> Sudodus:

I tried all of the options for installing the boot loader except the one where XP is resides.  I assume this is where I would have to install &#8216;grub&#8217;.  I fear installing anything here.  Additionally, it is no doubt obvious that my knowledge of partitions and partitioning is almost nil.  What I think I will feel most comfortable with is exploring Ubuntu from my disk and continue to educate myself concerning partitions and Ubuntu.

I really appreciate you sticking with me through this.  This thread ought to be labeled &#8220;Incomplete Installation Due To Operator Anxiety&#8221;&#8230;

Thanks again.
No, you should not install grub to any partition at all!!!

[COLOR="SeaGreen"]Install it to the drive: **/dev/sda**,[/COLOR]

[COLOR="Red"]not[/COLOR] to any partition /dev/sda[COLOR="red"]1[/COLOR], /dev/sda[COLOR="red"]2[/COLOR], /dev/dev[COLOR="red"]3[/COLOR], /sda/sda[COLOR="red"]4[/COLOR], ...

---

