---
title: "Unable to boot into either system after Ubuntu installation"
date: 2018-12-25
forum: New to Ubuntu
---

### Post by machtzu2 on 2018-12-25
Merry Christmas!


I had been running a dual boot system, with windows 7/16.04. This was working, but I am still pretty inept at Ubuntu. I was a experiencing an unusual issue(system memory was decreasing rapidly on the ubuntu side, seemingly without cause, from what I was able to determine). I opted to do a new install of Ubuntu(18.04)(I'm not sure if this was really stupid). The install completed successfully, but after restart I receive the following message:

```
error: no such partition
Entering rescue mode...
grub rescue>
```

ls gives the following output:

```
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1) (hd2) (hd2,msdos1) 
```

"ls (hd[n],[k])" gives "Filesystem is unknown.", except for (hd0, msdos7), (hd0, msdos6), which return "Filesystem is ext2."

I'd appreciate any help! Let me know if I can provide you with any pertinent information. I lack any Windows install media. I can choose to boot into ubuntu running off a flash drive, so the machine is useable that way.

---

### Post by yancek on 2018-12-25
More detailed information will be needed to get help.  The best way to get that is with boot repair which you can download using the Ubuntu DVD/USB you used to install Ubuntu.  Go to the site below, select the 2nd option under Getting Boot Repair and follow the instructions to download and then run it.  When you run boot repair, do NOT try to make any repairs but select the option to Create BootInfo Summary.  When it finishes, it will give a link which you can post here for members to review and hopefull offer a solution or point you in the right direction.

   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ra7411 on 2018-12-25
Another way of doing what yancek advised is:

-plug in your install disk, you may have to mess w/ bios startup to get it to boot using it versus going to your problem drive. Tapping F8 during power up  works on some machines to get a menu of boot options from which you can select your install disk.

-select TRY Ub

-you will get a generic ub screen

-open a terminal (Ctrl+Alt+T), with the machine connected to the internet, enter:

$ sudo add-apt-repository ppa:yannubuntu/boot-repair
$ sudo apt update
$ sudo apt install boot-repair
$ boot-repair

-then get the data he asked for.

---

### Post by machtzu2 on 2018-12-25
Thank you for the help!

Here is a link to the output of boot-repair:

[http://paste.ubuntu.com/p/XFdJzzScWq/](http://paste.ubuntu.com/p/XFdJzzScWq/)


Please let know if there is anything else I can do to provide you with more information

---

### Post by yancek on 2018-12-26
The boot repair shows that Grub is looking for boot files on sda3 which does not exist.  This is at the very top of the page.  If you scroll down to the bottom of boot repair it indicates the suggested repair would be to install Grub2 of sda7 to the MBR.  Since sda7 is where your Ubuntu 18.04 is installed, that should work.  Not sure if partitioning changed as there is no sda3 but you do have another Linux partition (sda6).

---

