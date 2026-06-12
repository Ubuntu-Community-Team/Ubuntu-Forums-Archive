---
title: "Re-Install and Clean Install tutorial"
date: 2014-10-06
forum: New to Ubuntu
---

### Post by czgirb on 2014-10-06
Dear all,
1. would you mind to do a favor for showing me to the URL/webpage, which I able to learn how to do an appropriate re-installation?
2. If I want to laeve the previous OS and want to install a new one, is it possible for being not changing my current /home ... how to do it?

---

### Post by mastablasta on 2014-10-06
same as installation procedure only without formatting the disk.

depends - if home is on separate partition then yes, otherwise just back it up install and restore form backup. you should have backups anyway regardless of the OS you use.

---

### Post by czgirb on 2014-10-06
my partition is:
040GB = /
020GB = /swap
207GB = /home
So, what you mean is before I format **/** partition, I should set **which one is /home** and **which one is /swap**?
Or what? Please guide me ...

---

### Post by mastablasta on 2014-10-06
ah you have separate home. you can install / and assign /swap, then just select home and don't reformat. : [http://askubuntu.com/questions/285212/keeping-the-same-home-partition-after-a-clean-install](http://askubuntu.com/questions/285212/keeping-the-same-home-partition-after-a-clean-install)
use the manual setup of course. 

otherwise: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

and also rather than having separate home what I do is keep /home on root (/) and use data partition for all data. so in case I mess up some config or something I could just reformat & reinstall. since data is separated nothing really important get's overwritten. 

note that various configurations of your programs are kept in /home it's kind of like my documents in windows and most people do not separate those on separate partition.

---

### Post by ajgreeny on 2014-10-06
It is essential when reinstalling to choose the "Something Else" option at partitioning or you may well lose the whole of the disk contents due to a reinstallation bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by grahammechanical on 2014-10-06
I have been trying to find some images for you. We have to be careful following online tutorials as they are not always applicable to us. Here is my advice.

You already have your partitions. That reduces the complexity a little bit.

1) Load the live session and at the page that offers Try Ubuntu - Install Ubuntu select Install Ubuntu. See image

[http://www.tecmint.com/wp-content/uploads/2014/04/image002.png](http://www.tecmint.com/wp-content/uploads/2014/04/image002.png)

2) At the Installation Type page select the Something Else option. See image.

[http://ubuntuhandbook.org/wp-content/uploads/2013/06/Ubuntu-create-partition.png](http://ubuntuhandbook.org/wp-content/uploads/2013/06/Ubuntu-create-partition.png)

3) The partitioner will load showing the partition layout of the hard disk. Note the location of the / partition; the /home partition and the swap partition.

[http://www.tecmint.com/wp-content/uploads/2014/04/image0101.png](http://www.tecmint.com/wp-content/uploads/2014/04/image0101.png)

4) Select the / partition and click change

5) a dialog will appear with the following options

a) resize partitions (up and down arrows)
b) Use As (drop down box)
c) format partition (a tick box)
d) mount point (a drop down menu)
e) buttons for Cancel and OK

See, the second answer in this link and look at image 3 in that answer for an example of this dialog box.

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

5) Change Use As to Ext4; tick the box to format the partition; select the mount point as /; click OK. We will get a message warning about lose of data from resizing the partitions. We will get this message even if we have not changed the size of the partitions. Do not worry about it.

6) you will now be back at the partitioner which will refresh and show your changes.

7) Now select the partition of /home and click change

the same dialog will appear but this time we will do things differently

a) Change Us As to Ext4
b) Do NOT tick the box format the Partition. Otherwise you will loose everything on your /home folder. Repeat - Do NOT tick the box to format the /home partition.
c) select mount of /home and click OK

8) you will be returned to the partitioner page which has refreshed itself. Confirm that you have chosen the correct partitions.

9) Look at the panel labelled Device for boot loader Installation. It defaults to the MBR of sda. If we have only one hard disk then that setting will be acceptable. If we have two hard disks (sda and sdb) and are installing onto sdb, then we may choose to install the boot loader into the MBR of sdb by using the drop down menu.

10) The partitioner will recognise the existing swap partition and use that. So, there is nothing we need do about swap.

11) Click Install Now. There is no going back from that decision. So, make sure that everything is as you want it to be. Do not stop the installation as you will end up with a broken OS.

That is about it, really.

Regards.

---

### Post by czgirb on 2014-10-06
Thank you very much for all of your guidance.
Cos it will be my guidance in order to OS moved.
Currently, I still choosing which one is preffered.

If when I do a re-install, **I forgot to stated which partition is swap**.
Am I now **allowed to set which partition is swap**? via GParted?
Would you mind to give me a guidance ...
**Thank you**

---

### Post by deadflowr on 2014-10-06
If you already have a swap partition, then the system will always find it.
But, yes, you can always use gparted( or another partitioning tool (to make a swap partition, if you do not have one).
But if you do make one, because you did not have one, it'll most likely be set as the highest partition number, regardless of where on the disk it is made.
(example, if you already have partitions, sda1, sda2,and sda3, if you make the swap between sda2 and sda3, it'll probably be marked as sda4)


That said, in terms of installing with the partitions as laid out, with /, /home, and swap, when reinstalling use the same username and password so the system doesn't make a totally new user. 
(Though I don't think using the same password is as important as setting the user to be the same name as the existing user)

---

### Post by czgirb on 2014-10-06
thank you @deadflowr
just check via gparted. as you said ... the system is found out already ... thank you.

---

