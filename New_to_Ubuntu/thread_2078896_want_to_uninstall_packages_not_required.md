---
title: "want to uninstall packages not required"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by issacnewton on 2012-10-31
Hi

I am using ubuntu for past few months. I have windows XP and I installed Ubuntu inside VirtualBox. I mostly use it for programming assignments. But when I used the df -h command last week, I found the following.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  3.3G  3.9G  47% /
udev            241M  4.0K  241M   1% /dev
tmpfs           100M  776K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M  152K  248M   1% /run/shm
share            98G   32G   67G  33% /media/sf_share
```

Since I am using the Ubuntu for basic programming in fortran,
python (i installed numpy scipy etc), octave, R, I am wondering
why so much space is used. There are lot of software which
I don't use at all. Like software to play mpg etc (i forgot the name). So I would like to remove these unused softwares. But first I need to find out which softwares are absolutely required and which are add ons. I am more comfortable with command line option , so I don't want any GUI applications for sys admin stuff. I just editors like gedit, pico, few compilers like gcc, gfortran, python etc. So can people here guide me ? 

thanks

---

### Post by newb85 on 2012-10-31
32GB in /media/sf_share is the shared folder with Windows (i.e., not Ubuntu or applications). Aside from that you're talking about less than 3.5GB.  How much more do you really expect to slim that down?

---

### Post by sandyd on 2012-10-31
> **issacnewton said:**
> Hi

I am using ubuntu for past few months. I have windows XP and I installed Ubuntu inside VirtualBox. I mostly use it for programming assignments. But when I used the df -h command last week, I found the following.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  3.3G  3.9G  47% /
udev            241M  4.0K  241M   1% /dev
tmpfs           100M  776K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            248M  152K  248M   1% /run/shm
share            98G   32G   67G  33% /media/sf_share
```

Since I am using the Ubuntu for basic programming in fortran,
python (i installed numpy scipy etc), octave, R, I am wondering
why so much space is used. There are lot of software which
I don't use at all. Like software to play mpg etc (i forgot the name). So I would like to remove these unused softwares. But first I need to find out which softwares are absolutely required and which are add ons. I am more comfortable with command line option , so I don't want any GUI applications for sys admin stuff. I just editors like gedit, pico, few compilers like gcc, gfortran, python etc. So can people here guide me ? 

thanks
The space usage above looks fine to me - this is around the size of a default ubuntu installation.

If you are more comfortable with the command line options, you can install either 

[LIST]
[*]Ubuntu Server
[*]Mini.iso
[/LIST]

Ubuntu server has a option during installation to select the options that you want to install. Just make sure the GUI and other options are unchecked, and it will use much less space.

---

### Post by issacnewton on 2012-10-31
thanks for chipping in guys.

So why /dev/sda1 is using 47 %. That seems a lot for the linux machine. Yesterday I was trying to join 279 png files (total size 66 MB) using graphicsmagick software to convert them into a single pdf. I got message that system doesn't have enough space. So I deleted all those files after transferring them to win xp. Thats why I started to worry about the space utilization. 

Sandyd, I would prefer GUI for time being. But I want to get rid of many softwares which I might not need at all. So my task is to first find out which softwares are installed on my system and then to see if they are indeed needed. As I said, I need gedit and the programs like python, gfortran, gcc, R , octave etc, and other components which are absolutely necessary to run the Ubuntu in GUI.

---

### Post by newb85 on 2012-11-01
By default, VBox limits your total virtual HDD to 8GB.  (This is part of the setup wizard, and you could have made it larger.)  You'll notice in the figures you initially provided it says sda1 is 7.9GB.  47% means you're using 47% of that 7.9GB.  Apparently, the operations you're trying to carry out require more than the space you have left.

I don't know about expanding the current HDD, but I know you can add another virtual HDD to your VM.

---

### Post by issacnewton on 2012-11-01
thanks newb85

---

### Post by offgridguy on 2012-11-01
You may not want to go this route, but have you considered lubuntu, the
lightweight, streamlined , bare bones and ultra fast version of ubuntu .

---

### Post by issacnewton on 2012-11-02
offgridguy

yes, I think thats what I am probably looking....  I downloaded
LUbuntu minimal yesterday and will try to out that in VirtualBox and see

---

### Post by Elfy on 2012-11-02
You'll find that if you stay with the default 8Gb that installing Lubuntu won't make all that much difference and you will be wondering why you are using 35% (a guess ... ) instead.

You would be better off making the virtual drive larger and not worrying about which version you are using.

---

