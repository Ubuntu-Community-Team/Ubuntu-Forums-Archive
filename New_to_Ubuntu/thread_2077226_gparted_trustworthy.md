---
title: "gparted trustworthy?"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by ginmardo84 on 2012-10-28
how trustworthy is gparted when it comes to hard disk checking. like using gparted for checking the hard disk drive's status, if it is failing or has any bad blocks or bad sectors. so far i have run several tests which gparted tells me that the old drives [1 sata, 1 ide pata drive] seem to be in good condition, no errors whatsoever and no bad blocks or bad sectors. 

any thoughts on gparted test results it gave you?

---

### Post by aabed91 on 2012-10-28
I'm using it several times for re-partitioning my hard disk.

It's nice and easy.

And not have any problem (at least when i use it).

I don't know if someone face any problem

---

### Post by jerrrys on 2012-10-28
You should be able to double check it with

[gnome-disk-utility]("http://packages.ubuntu.com/quantal/gnome-disk-utility")

---

### Post by JawsThemeSwimming428 on 2012-10-28
Very reliable, I have used it numerous times over the years.

---

### Post by Rex Bouwense on 2012-10-28
+1

---

### Post by sammiev on 2012-10-28
+1 for gparted as well but I will have to try gnome-disk-utility.

---

### Post by oldos2er on 2012-10-28
> **ginmardo84 said:**
>  like using gparted for checking the hard disk drive's status, if it is failing or has any bad blocks or bad sectors. 

Use **smartctl** to check health, bad sectors, etc. It's part of the package **smartmontools**.

---

### Post by amjjawad on 2012-10-28
From my first days with Linux until now, I use nothing but GParted and I don't remember it caused me any problem.

ALL what you need to do is:
1- Boot your machine from the LiveCD or the LiveUSB - of course make sure your system will boot first from one of those.

2- If this is a Lubuntu LiveCD/USB then
Menu > System Tools > GParted

3- On the top right of GParted's window, make sure to choose the correct HDD (for example: /dev/sda)

[http://i43.tinypic.com/34zc11s.jpg](http://i43.tinypic.com/34zc11s.jpg)

4- From GParted Menus, go to Device then Create Partition Table
[http://i44.tinypic.com/2whfaxw.jpg](http://i44.tinypic.com/2whfaxw.jpg)

5- Click Apply
[http://i40.tinypic.com/11qsumc.jpg](http://i40.tinypic.com/11qsumc.jpg)

6- Your HDD now should look like this:
[http://i43.tinypic.com/s4behe.jpg](http://i43.tinypic.com/s4behe.jpg)

7- If I'm not mistaken, in order to check the HDD now, you need to create at least one partition. You can do that very easily. Right Click on the unallocated space of your HDD and Click New ... then ... create one Primary Partition: [http://i39.tinypic.com/24gvfy8.jpg](http://i39.tinypic.com/24gvfy8.jpg)

Choose whatever type you want, we just want to check the integrity of the HDD, we are not installing anything at this stage.

8- That is all.

IF and ONLY IF this failed to fix whatever problems on your HDD then I suggest to use the 'dd' command to wipe the whole thing and write Zero on each and every block/sector/whatever you call it.

IF and ONLY IF the 'dd' command didn't fix and this approach was useless: [http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

Then I guess that is all what you can do, unless there is another idea that I missed here :)

Good Luck ;)

---

### Post by NikTh on 2012-10-28
> **ginmardo84 said:**
> how trustworthy is gparted when it comes to hard disk checking. like using gparted for checking the hard disk drive's status, if it is failing or has any bad blocks or bad sectors. 

Hi , 
> **oldos2er said:**
> Use **smartctl** to check health, bad sectors, etc. It's part of the package **smartmontools**.
+1 @oldos2er

I use smartmontools for checking the health state of my HDD. 

Install smartmontools from terminal (CTRL+ALT+T) 
```
sudo apt-get install smartmontools --no-install-recommends
```Run the test
```
sudo smartctl -a /dev/sda
``` where /dev/sda is the HDD as listed under the command ```
sudo fdisk -l
```Have a look for detailed explanation of the results
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

GsmartControl - Graphical front end for smartmontools
[http://gsmartcontrol.berlios.de/home/index.php/en/Home](http://gsmartcontrol.berlios.de/home/index.php/en/Home)
Install 
```
sudo apt-get install gsmartcontrol
```usage
```
gksudo gsmartcontrol
```Thanks

---

### Post by jerrrys on 2012-10-28
> **oldos2er said:**
> Use **smartctl** to check health, bad sectors, etc. It's part of the package **smartmontools**.

Disk Utility has smart built in.  Is there an advantage to using smartomntools instead?

---

### Post by oldos2er on 2012-10-28
Not knowing anything about gnome-disk-utility, I don't know.

---

### Post by jerrrys on 2012-10-28
> **oldos2er said:**
> Not knowing anything about gnome-disk-utility, I don't know.

And now I see the Kubuntu, but of course  :)

---

### Post by NikTh on 2012-10-29
> **jerrrys said:**
> Disk Utility has smart built in.  Is there an advantage to using smartomntools instead?

No, its just an alternative  :)

---

### Post by oldos2er on 2012-10-29
> **jerrrys said:**
> Disk Utility has smart built in.  Is there an advantage to using smartomntools instead?

Also, smartmontools contains the daemon smartd which can be configured in various ways to monitor one's hard disks.

---

### Post by jerrrys on 2012-10-29
> **oldos2er said:**
> Also, smartmontools contains the daemon smartd which can be configured in various ways to monitor one's hard disks.

nice touch

---

