---
title: "Partitioning in Ubuntu"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by linuxpenguin12 on 2013-02-19
Hi there. I am an absolute newb linux user and I was having issues with partitioning primary and extended partitions in Ubuntu.

What I am trying to do is to create an extended partition with three logical drives:

1) First logical drive is 300MB and type "Linux"

2) Second logical drive is 400MB and type "Linux"

3) Third logical drive is 500MB and type "Linux Swap"

I absolutely have no idea how I would do this, I have been  researching about how to do this for hours.

Could someone please help.

That would be greatly appreciated. 

Thanks   :)

---

### Post by carl4926 on 2013-02-19
Those figures don't make sense, least the sizes are v small.

You should post a screen of what you see in Gparted

---

### Post by grahammechanical on 2013-02-19
> [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Is this a blank unformatted disk? If not you should tell us what else is on the disk.

There are different file systems in Linux. So, 'file system Linux' is just a generic label. What is to go in these partitions?

Regards.

---

### Post by linuxpenguin12 on 2013-02-19
Hi there. I am an absolute newb linux user and I was having issues with partitioning primary and extended partitions in Ubuntu using the terminal and the command 'fdisk'

What I am trying to do is to create an extended partition with three logical drives:

1) First logical drive is 300MB and type "Linux"

2) Second logical drive is 400MB and type "Linux"

3) Third logical drive is 500MB and type "Linux Swap"

I absolutely have no idea how I would do this, I have been  researching about how to do this for hours.

Could someone please help.

That would be greatly appreciated. 

Thanks   :smile:
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12518416") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12518416")

---

### Post by linuxpenguin12 on 2013-02-19
I am using Ubuntu 10.04 LTS as a virtual machine (.iso) disk, using VMWare Workstation 9.1

---

### Post by Mark Phelps on 2013-02-19
> **linuxpenguin12 said:**
> What I am trying to do is to create an extended partition with three logical drives:
Then use Gparted -- it can be installed from the Software Center.

But ... those sizes are way too small to be of any use.  If you're trying to install Ubuntu using those partitions, you need several GB of file space, not a few hundred MB.

---

