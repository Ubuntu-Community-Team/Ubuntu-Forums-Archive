---
title: "Vista/Ubuntu dual boot partitioning help"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Doran_Eirok on 2008-10-14
So I'm just about ready to try and set up a dual boot system on my HP laptop that currently has Vista. I want to dual boot both Vista and Ubuntu 8.04.1 64 bit on there, but I'm getting a bit stuck on how to go about partitioning the disks. As it is right now the laptop has a 250 GB hard disk partitioned into one large main secion that has about 60 GB free right now, and a a small Windows Recovery partition that I'm leaving as is. I want to make a 30 GB partition for Ubuntu and leave the rest free for Vista and otherwise leave my current data as is.

So far I've been looking over this page:

[https://help.ubuntu.com/8.04/switching/installing-partitioning.html]("http://help.ubuntu.com/8.04/switching/installing-partitioning.html")

..but have a few points of confusion. The options for partitioning and the wording used in the actual installer don't match up with the above page. Also, I'm pretty sure it was just a typo but the page also says the disk "will be re-partitioned and all existing data stored on it will be lost," which does not sound right in the case of dual booting but still makes me nervous. Given that I reeeeeeally want to do this right and not screw something up and mess up the disk and my data on there, I'm a bit uncertain and nervous, so I'm particularly wondering if anyone can either describe here or point me to a better page that details exactly how I'd want to do what I need to do and what options to choose. If there's a tutorial page like the above but that actually has screenshots of the installer that would make me feel better. The specific process of resizing my current disk's main partition down by roughly 30 gigs and making new partitions out of that for Ubuntu and its swap file remain kind of confusing and unclear to me, so any specific guidence would be much appreciated.

Thanks!

---

### Post by nhasian on 2008-10-14
i would do these steps:

1) scandisk your drive with windows
2) defrag your drive with windows

then boot from the liveCD.  after ubuntu finishes loading in the menu go to system/administration/partition editor to shrink your windows partition.

you will need to create a / (root) partition with the EXT3 filesystem and a swap partition you can make the swap partition the same size as your ram.  if you have 2 gigs of ram you would put 2048M for the swap file.  optionally you can make a /home partition as well for your data.  it makes it easier to backup your stuff in the future.

after you've set up the partitions the way you want you can start installing ubuntu.

---

### Post by zvacet on 2008-10-14
I hope [this]("http://psychocats.s465.sureserver.com/ubuntu/dualboot") will be helpful to you.

---

### Post by bobnutfield on 2008-10-14
I would caution you to get all the information you can about resizing Vista partitions with anything other than Vista itself.  I have read in many places that Vista does not like being resized by other OS partion editors.

---

### Post by nhasian on 2008-10-14
anytime you resize a partition you are taking a small risk of data loss.  i forgot to mention you should always backup any critical files before continuing :)

personally i've installed ubuntu 8.04 on about half a dozen machines that had vista NTFS drives with no problems.  I dont think XP or Vista come with any partitioning software.  you can expand their filesystem onto new partitions/drives but you cant shrink them.

> **bobnutfield said:**
> I would caution you to get all the information you can about resizing Vista partitions with anything other than Vista itself.  I have read in many places that Vista does not like being resized by other OS partion editors.

---

### Post by shabs on 2008-10-14
I agree with bobnutfield. Infact this tutorial is very simple and will guide you step buy step on how to go about using the paritioning tool in vista and installing ubuntu. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
My friend used this one, he first defragmented his drive and then partitioned it. He didn't lose any data. But making a backup is always ALWAYS a good idea. Hope the tutorial helps.

---

### Post by shabs on 2008-10-14
> **nhasian said:**
> anytime you resize a partition you are taking a small risk of data loss.  i forgot to mention you should always backup any critical files before continuing :)

personally i've installed ubuntu 8.04 on about half a dozen machines that had vista NTFS drives with no problems.  I dont think XP or Vista come with any partitioning software.  you can expand their filesystem onto new partitions/drives but you cant shrink them.

Vista does allow you to shrink a partition.
:)

---

### Post by bobnutfield on 2008-10-14
While I do not use Vista anymore, I can tell you that it does have a partitioning utility, and I would stronly recommend using that to resize the Vista partition.

---

### Post by Paqman on 2008-10-14
If you're really scratching your head about partitioning then there's always the option of skipping it at this stage. Ubuntu has an installer called Wubi that can install the system to a virtual partition located on your Windows NTFS partition. Otherwise it works almost exactly the same as a normal install. 

You can migrate a Wubi-installed copy of Ubuntu to a dedicated partition later if you so desire. 

Just boot into Windows and pop your LiveCD in to start Wubi.

---

### Post by nhasian on 2008-10-14
doh i learn something new every day.  while windows XP doesnt have the built in tools, Vista does allow you to grow/shrink partitions.  Good to know.  probably safer than using Gparted to resize NTFS partitions.  one would hope anyways...

---

### Post by kansasnoob on 2008-10-14
> **shabs said:**
> I agree with bobnutfield. Infact this tutorial is very simple and will guide you step buy step on how to go about using the paritioning tool in vista and installing ubuntu. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
My friend used this one, he first defragmented his drive and then partitioned it. He didn't lose any data. But making a backup is always ALWAYS a good idea. Hope the tutorial helps.

Add me to that list!

Vista should only be resized by Vista's own tools! That APC dual boot guide has it right!

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

---

### Post by bodhi.zazen on 2008-10-14
> **bobnutfield said:**
> While I do not use Vista anymore, I can tell you that it does have a partitioning utility, and I would stronly recommend using that to resize the Vista partition.

> **nhasian said:**
> doh i learn something new every day.  while windows XP doesnt have the built in tools, Vista does allow you to grow/shrink partitions.  Good to know.  probably safer than using Gparted to resize NTFS partitions.  one would hope anyways...

Yes there are tools in Vista that allow you to resize a partition. This is, however, a blunt instrument and somewhat limited.

Unless anyone can document it is safer I would have no qualms using gparted, either from the Ubuntu CD or from the Gparted live CD.

Yes indeed, in resizing a partition there is a small risk of data loss and as such you should back up first. I am not aware of any objective data that one tool is safer than another and IMO the idea you should use only the Vista tool is, well, FUD.

---

### Post by kansasnoob on 2008-10-14
> **bodhi.zazen said:**
> Yes there are tools in Vista that allow you to resize a partition. This is, however, a blunt instrument and somewhat limited.

Unless anyone can document it is safer I would have no qualms using gparted, either from the Ubuntu CD or from the Gparted live CD.

Yes indeed, in resizing a partition there is a small risk of data loss and as such you should back up first. I am not aware of any objective data that one tool is safer than another and IMO the idea you should use only the Vista tool is, well, FUD.

It's fairly well explained here:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

And after a few times of having to figure out how to restore Vista (sometimes without a Vista DVD) I learned it was much, much better to use Vista's own tools to resize a Vista OS!

Then it's also easy to just choose the "Install to Largest Continuous Free Space" unless you want to get fancy.

Some things I'm unsure of - this isn't one of them!

---

### Post by M4rotku on 2008-10-14
When I was dualbooting my system along with Vista, I encountered a rather severe problem.  Vista refused to move; it has certain files spread out all over the harddrive and when I tried to shrink the partition, I could only get 4 gigs out of the 160 that were said to be free.

The only solution that worked for me was to reinstall Vista and then it successfully defragmented from the new installation as long as you defragment and partition it right away.

---

### Post by bodhi.zazen on 2008-10-14
> **kansasnoob said:**
> it's fairly well explained here:

[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

and after a few times of having to figure out how to restore vista (sometimes without a vista dvd) i learned it was much, much better to use vista's own tools to resize a vista os!

Then it's also easy to just choose the "install to largest continuous free space" unless you want to get fancy.

Some things i'm unsure of - this isn't one of them!

lol

---

### Post by Doran_Eirok on 2008-10-15
Thanks so much for all the feedback! Unfortunately I can't report completely success yet, but it's certainly being an entertaining detective story...

So, I started with this page:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
Which seems like a very good guide for exactly what I want to do. I've seen enough reports from people that while using Ubuntu or Gparted to partition will work for most things, if you try to -shrink- a volume running Vista with it, Vista will whine and complain and fall over dead. So I've wanted to shrink the partition within Vista first and then let Ubuntu take care of everything else with the install.

So this led me to this tutorial:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")
...on how to use Vista to repartition itself. I did all the steps and defragged and freed up enough space to shrink it by 30 GB to make room for Ubuntu, but then the plot thickened. Vista's Disk Management tool churns away for a few dozen seconds before helpfully telling me "Logical Disk Manager: Access is denied."

Extensive Googling on this hurdle led me next to this page:
[http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work#comment-3471]("http://www.vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work#comment-3471")
which introduces diskpart.exe, a command line way to do the same disk management stuff that's allgedly better and more robust. Except after figuring out how to do that and attempting, it churns away for a moment before spitting out "DiskPart encountered an error: Access is denied."

Googling extensively for THAT problem returned a few results with other people reporting the same problem, but I haven't been able to find any actual solutions to it. The detective work has been entertaining and educational but I feel like this problem has taken me to the end of the internet and unless anyone has a fantastic and awesome and simple solution to this that they know about, I'm probably going to give up and just install the Wubi of Ubuntu.

EDIT: Oh and I did run cmd as an administrator when running diskpart.exe as well. And I'm the only user on the computer, ergo the administrator, so I don't see how it could be an administrative privilege thing still.

---

