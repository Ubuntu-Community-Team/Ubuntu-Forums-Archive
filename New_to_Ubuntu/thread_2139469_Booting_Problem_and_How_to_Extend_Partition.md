---
title: "Booting Problem and How to Extend Partition ?"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by virus7 on 2013-04-26
Hello,

I am having a very disgusting problem and which is annoying me a lot... My problem is if I want to boot my Ubuntu(I have Windows as well) it gets into it and stay in Black Screen forever, and I have to kill my machine at least twice with same problem on third attempt it gets into Ubuntu... :@ what could be reason/s behind this?

By the way I have installed Ubuntu 12.04 using my Flash drive deleting one partition it was 20GB only, as I thought Ubuntu didnt need that much space. I havent installed that much software or almost nothing to it. Now I have seen that even my 20GB is getting smaller for this partition and I want to extend it. Without Live CD/DVD how is it possible to extend my partition?? 

Thank you!!

---

### Post by carl4926 on 2013-04-26
You really need to supply some detail.
A screen of your partition table would be good, with some comments on what we are seeing....
If I understand you correctly, you have installed entirely in one 20GB partition?

> [COLOR=#000000]Without Live CD/DVD how is it possible to extend my partition??[/COLOR]You need some live media to do this, if not the Ubuntu CD, you can use Parted Magic's (Gparted)

---

### Post by virus7 on 2013-04-27
Hello, I am using Dell Ailenware Laptop, its M17X R4 and am using Core i7 2.3GHz and 12GB DDR3 RAM and a 2GB Nvidia Graphics Card.

Yes I have used my Whole 20GB partition for Ubuntu 12.04

I am still facing this problem and I have to kill my machine again and again... its making me sad/scared for my Alienware... :(

---

### Post by carl4926 on 2013-04-27
> **virus7 said:**
> Hello, I am using Dell Ailenware Laptop, its M17X R4 and am using Core i7 2.3GHz and 12GB DDR3 RAM and a 2GB Nvidia Graphics Card.

Yes I have used my Whole 20GB partition for Ubuntu 12.04

I am still facing this problem and I have to kill my machine again and again... its making me sad/scared for my Alienware... :(

Ideally it would help us to see a screen of Gparted looking at your HDD
or at least the output of
```
sudo parted -l
```

20GB for a basic install is OK, but if you install any quantity of software and if you add personal files to your user account, that space will soon reduce.
If this doesn't apply to you then we might need to consider another possible cause, such as a error log being generated that is producing some very large files.

---

### Post by kamranm1200 on 2013-04-27
Yep. I agree with Carl4926 on this one. ;)

---

### Post by virus7 on 2013-04-28
I have typed the command 
"sudo parted -l" and I got some results like this 

Number  Start      End      Size    Type         File system  Flags
 1          32.3kB   41.1MB 41.1MB  primary   fat16        diag
 2          41.9MB  9945MB 9903MB  primary  ntfs         boot
 3          9945MB 381GB   371GB   primary   ntfs
 4          381GB   750GB   369GB   extended               lba
 5          381GB   666GB   285GB   logical     ntfs
 6          687GB   709GB   21.5GB  logical     ntfs
 7          709GB   750GB   41.4GB  logical     ntfs

I have no idea about this information.. :| Please give me some sort of solution to get rid of Black Screen problem!!
Thanks

---

### Post by virus7 on 2013-04-28
[IMG]http://www.mediafire.com/convkey/2372/tg8mp9cqtzevmqu6g.jpg[/IMG]

---

### Post by carl4926 on 2013-04-28
> **virus7 said:**
> I have typed the command 
"sudo parted -l" and I got some results like this 

Number  Start      End      Size    Type         File system  Flags
 1          32.3kB   41.1MB 41.1MB  primary   fat16        diag
 2          41.9MB  9945MB 9903MB  primary  ntfs         boot
 3          9945MB 381GB   371GB   primary   ntfs
 4          381GB   750GB   369GB   extended               lba
 5          381GB   666GB   285GB   logical     ntfs
 6          687GB   709GB   21.5GB  logical     ntfs
 7          709GB   750GB   41.4GB  logical     ntfs

I have no idea about this information.. :| Please give me some sort of solution to get rid of Black Screen problem!!
Thanks

The only thing there that is possibly related to your 20GB quote is
6 687GB 709GB 21.5GB logical ntfs

But it's ntfs not ext4
And I see no swap partition either, though with 12GB RAM that shouldn't matter.
If you can shrink partition 5 you could grow 6 to take up the freed space. But you need to format 6 to ext4, which basically means a re-install.

How come you want to dedicate so much space to windows and very little to Ubuntu/Linux

---

### Post by carl4926 on 2013-04-28
Darn, you have 20GB of Unallocated space there anyway!!
And what is this a WUBI install???

---

### Post by carl4926 on 2013-04-28
> **carl4926 said:**
> Darn, you have 20GB of Unallocated space there anyway!!
And what is this a WUBI install???

That is all so messed up it isn't even funny
What the * is /host as a mount point?
I suggest you start again
Take a look at this
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

---

### Post by bcbc on 2013-04-28
> **virus7 said:**
> I have typed the command 
"sudo parted -l" and I got some results like this 

Number  Start      End      Size    Type         File system  Flags
 1          32.3kB   41.1MB 41.1MB  primary   fat16        diag
 2          41.9MB  9945MB 9903MB  primary  ntfs         boot
 3          9945MB 381GB   371GB   primary   ntfs
 4          381GB   750GB   369GB   extended               lba
 5          381GB   666GB   285GB   logical     ntfs
 6          687GB   709GB   21.5GB  logical     ntfs
 7          709GB   750GB   41.4GB  logical     ntfs

I have no idea about this information.. :| Please give me some sort of solution to get rid of Black Screen problem!!
Thanks
If you have an nvidia card, you need to either boot with nomodeset ([http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/q/162075/14916")) or install the nvidia closed source drivers: [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers]("http://askubuntu.com/q/47506/14916")

It seems like you don't need a Wubi install as you have already partitioned and have so much free space. If you Wubi is 'mature' you can [migrate]("http://askubuntu.com/q/635/14916") it to a normal install or you can reinstall fresh.

---

### Post by virus7 on 2013-04-29
> **carl4926 said:**
> The only thing there that is possibly related to your 20GB quote is
6 687GB 709GB 21.5GB logical ntfs

But it's ntfs not ext4
And I see no swap partition either, though with 12GB RAM that shouldn't matter.
If you can shrink partition 5 you could grow 6 to take up the freed space. But you need to format 6 to ext4, which basically means a re-install.

How come you want to dedicate so much space to windows and very little to Ubuntu/Linux

hello, the main thing was I was thinking to explore Ubuntu First and interestingly I thought if I started liking it I will allow more space to it. Eventually I liked it so I get another 20GB space for it and wanted to add with current settings, I hoped that it may work just like Windows. :(

So does Reinstalling my system can help me to overcome with this situation? moreover if I say Gparted to convert ntfs to ext4 for my current ubuntu partition is it going to work??

---

### Post by carl4926 on 2013-04-29
well sda6 which is you ubuntu install should be ext4
Use gparted and select sda6 and select resize and pull it left to take up the space you see in grey (20GB unallocated)
Apply
Then format it to ext4

Now install ubuntu and choose this option
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/4.png)
Then here you select sda6 and set the mount point as   /
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png)
You don't have a separate /home so ignore that

If you nned file from your current Ubuntu install you should get those first.

---

### Post by virus7 on 2013-04-30
> **virus7 said:**
> hello, the main thing was I was thinking to explore Ubuntu First and interestingly I thought if I started liking it I will allow more space to it. Eventually I liked it so I get another 20GB space for it and wanted to add with current settings, I hoped that it may work just like Windows. :(

So does Reinstalling my system can help me to overcome with this situation? moreover if I say Gparted to convert ntfs to ext4 for my current ubuntu partition is it going to work??

Hello there, Well after all your suggestion I have reinstalled Ubuntu 12.04 but I am having same problem. This time I have allocated huge space for "/" and "/home" and 6gb for Swap. 

when I faced same problem of Black Screen I have tryed to do with "nomodeset" option but my problem is eventhough I did it it loads something and then it get stuck again to blackish screen.. !! 

By the way I have a "nvidia geforce gtx66m" graphics card, from where can I find a driver for it? my additional driver option doesnt show me anything.. :(

[IMG]http://www.mediafire.com/convkey/b14a/c2o3zof616tb9r46g.jpg[/IMG]

---

### Post by carl4926 on 2013-04-30
Well, you can boot the live cd OK to install?

BTW: / (root) only need be 20GB max,you could reduce it and give more to /home

Are you getting the grub menu? I guess you must be....

---

### Post by virus7 on 2013-05-01
> **carl4926 said:**
>  Well, you can boot the live cd OK to install? 
could you please explain a little bit more

>  BTW: / (root) only need be 20GB max,you could reduce it and give more to /home

Are you getting the grub menu? I guess you must be....

yes i want to do that but with gparted software it shows some kind of small keys to partition and I cant extend or shirnk that volume I dont know how to do that ?? 
am getting grub menu and when I select Ubuntu I face this problem..

---

### Post by carl4926 on 2013-05-01
You can't manage partition from the installed system, you need to use the Ubuntu CD or something like Parted Magic

The whole partition table is somewhat messy mind you.

I would delete partitions and remake them as required, then re-install.

---

### Post by virus7 on 2013-05-06
I do understand all valuable suggestion regarding partition, but am more concern about why am I getting stuck with Black Screen when I choose Ubuntu from my Grub Menu. I have to keep killing my machine atleast 2 times to get into it. In this way I am getting more and more depressed :(

---

### Post by oldfred on 2013-05-07
You mention nvidia geforce gtx66m, which is a laptop chip and many with the m at the end are Optimus? If a standard nVidia you may just need the boot parameter nomodeset, or in BIOS turn off nVidia until you get system working. But some with the Intel default chip have to have the video set to exact monitor size as boot parameter.

If Optimus you will need Bumblebee. nVidia just last week issues the first Linux driver that supports Optimus, but it may need the kernel that will be in 13.10?

       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)

This was Lenovo, but discusses a good way to set video with Optimus.
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

