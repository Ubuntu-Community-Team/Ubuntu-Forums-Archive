---
title: "The creation of swap space in partition #3 of SCSI1 (0,0,0) (sda) failed"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by gavin8 on 2014-08-30
Hello, the installation of ubuntu does not work, it says it is something to do with swap space. I don't know what that is, but I know it can be made through partitioning. Please tell me how to partition a drive :'( I also had a look at the "something else install type, but I didn't get anywhere with that, it did not allow me to partition it so please help me :(
[U][B]
What it says before install:

The creation of swap space in partition #3 of SCSI1 (0,0,0) (sda) failed[/B][/U]

My Specs are:

CPU: AMD FX-8350 8-core
[B]Motherboard: Gigabyte 970A UD3P (I am not sure whether Ubuntu will install the driver (Ethernet, ect.) for me or not)
[/B]Ram: 8gb Hyper X Beast 1600Mhz
GPU: Radeon R9 280 3gb
Storage: WD Caviar Sata 2 3gb/s

Somebody please help me fix this :(
Could anyone help, it does not install properly.

---

### Post by sbnwl on 2014-08-30
What Ubuntu version you trying ?

Does your machine already contain any other OS?

You need to post the output of command (boot into live Ubuntu OS):
```
sudo fdisk -l
```

---

### Post by sudodus on 2014-08-30
Welcome to the Ubuntu Forums :-)

The terminal windows and command lines may seem difficult (if you are a beginner), but it makes it much easier for us to understand what is the problem and what happens. The hotkey combination

 ***ctrl + alt + t***

will open a terminal window, where you can type the following commands

```
sudo parted -l
``` (... space minus ell, finish with the Enter key)

and

```
df
```

Please mark and paste the output of those commands into a reply here. Enter Advanced mode and try to put it within CODE tags (use the # icon above the window in advanced mode).

---

### Post by fantab on 2014-08-30
Is the HDD formatted?
Is there Windows in the picture? Pre-installed?

Have you "Try Ubuntu" option? Let us know how it goes/went?
It should give you a working ubuntu desktop... connect to internet, and check how the other hardware behave.

Open Terminal [ctrl+alt+T] run the following commands and post the output here.... you can copy/paste:
```
sudo parted -l
sudo fdisk -l
```

About SWAP: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by gavin8 on 2014-08-30
[COLOR=#000000]sbnwl I am using 14.04.1
sudodus I have tried it, it's working great!
Thanks to all of you, but I can't connect to the internet on that machine, I have not downloaded the drivers, can you tell me how to?[/COLOR]

---

### Post by fantab on 2014-08-30
Hopefully you don't have download any drivers.
How do you usually connect to the internet?

---

### Post by gavin8 on 2014-08-30
Ethernet. I am on the test boot, but please could you tell me how to format a drive

---

### Post by deadflowr on 2014-08-30
> **gavin8 said:**
> Ethernet. I am on the test boot, but please could you tell me how to format a drive

By test boot, do you mean a livecd?
You can reformat and repartition the hard drive with the program gparted, which is included on the livecd's "Try Ubuntu" session.

Anyway, as was already asked, is this going to be a machine with only Ubuntu or will you be trying to run multiple systems such as Windows 7, or 8?
And if only Ubuntu, was the no swap error after trying to install using installation option *Install over whole drive*?
(I'm sorry if that is not exactly what the installation calls it, but it should be something like that.)

---

### Post by gavin8 on 2014-08-30
No, I'm using a USB.
I think I'll only use Ubuntu or Mint for a while, until I can get windows.
And finally, yes it was, when I tried to install over the whole drive.

---

### Post by gavin8 on 2014-08-30
I had a look at GParted, does it require an install?

---

### Post by deadflowr on 2014-08-30
Livecd, liveusb same difference.
What I meant was are you running it from the installation media's Try Ubuntu selection?
(Also known as a live session)

Gparted is on the live session, no need to install.

A quick how to for it
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by ThatBum on 2014-08-30
A swap partition in Linux is like the virtual memory/pagefile in Windows, it's basically overflow if the RAM gets full. However, unlike Windows, Linux can run quite happily without swap space, especially with how much RAM you have. But, I suppose it's still good to have it anyway.

You could tell the installer you want to manually partition the drive with the Something Else option. Try making a single large partition with mount point of /, and leaving 4GB or so of space at the end of this partition and designate it as swap.

---

### Post by fantab on 2014-08-30
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by sbnwl on 2014-08-31
@[**[COLOR=#000000]gavin8[/COLOR]**]("http://ubuntuforums.org/member.php?u=1942868")
You just try playing with the Ubuntu 14.04.1 you have on the USB. Do whatever you wish, go through all the installation options and get familier with them, untill your Windows 8.1 arrives. 
Sometimes it is much better to give yourself a try/jump in the field than to learn the rules of football first.

---

