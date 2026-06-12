---
title: "need help in install ubuntu"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by speedman2202 on 2012-08-13
hiii


i have use ubuntu windows desktop download and have downloaded and install linux and left it install and going to sleep after  that when i try ubuntu .... seemed too slow and some icons not running with me ... so i will burn the IMG to a CD and reinstall ubuntu again .... so anybody can help me in uninstall to install ubuntu again from cd ..... or just format the ubuntu partition and install again in same partition???


thx at advanced :)

---

### Post by mr-woof on 2012-08-13
Hi,

so if ive got this right, you've installed ubuntu and its not worked?

Try and burn the iso image to a different cd, how does the system run ok when you use the live cd?

---

### Post by NikTh on 2012-08-13
Hi , 
take a look at this video tutorial --> [http://www.youtube.com/watch?v=LokDqte3sA4](http://www.youtube.com/watch?v=LokDqte3sA4)

This is a regular dual-boot installation tutorial with windows , and NOT a wubi install. 
Any problems - queries post back here. 
Thanks

---

### Post by deadflowr on 2012-08-13
If you want to uninstall an Ubuntu install which is inside your windows install, simply go into the windows add/remove program section look for ubuntu and remove.
For help installing ubuntu look here:

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

And please read over the subsections in the Other Installation Guides at the bottom. Especially about Partitioning and MultiOSBoot.

---

### Post by speedman2202 on 2012-08-13
ty all ....i have got what i need .... i wish there's thx button to thank u all


best regards :)

---

### Post by mr-woof on 2012-08-13
good luck :D

---

### Post by speedman2202 on 2012-08-13
i have stuck with something ..... i have 5 partitions (C , D , E , F , I) .....C partition contain WinXP and i D,E, F have my own data ....i want install Ubuntu on I partition ..... and the video u provide me not show to me how to choose a specific partition ..... can anybody help me with a clear  steps cuz i afraid to do something that will erase all my entire data ......:|

---

### Post by UbuntuNerd on 2012-08-13
> **speedman2202 said:**
> i have stuck with something ..... i have 5 partitions (C , D , E , F , I) .....C partition contain WinXP and i D,E, F have my own data ....i want install Ubuntu on I partition ..... and the video u provide me not show to me how to choose a specific partition ..... can anybody help me with a clear  steps cuz i afraid to do something that will erase all my entire data ......:|

hey bro look at this guide is simple to follow:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

---

### Post by speedman2202 on 2012-08-13
> **UbuntuNerd said:**
> hey bro look at this guide is simple to follow:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

ummm .... ok ..... he request 3 partitions .... i have only one partition for ubuntu about 8 Gb .... and he want divide me it .... can u tell me another easier way :(

---

### Post by marlow59 on 2012-08-13
ubuntu needs to divide your partition, I don't advise you to prevent it, you can manually allow minimal sizes to the 2 "secondary" partitions. Another advice : put your data on an external drive, an HDD with 11 partitions is verry confusing and easilly messed up.

---

### Post by NikTh on 2012-08-13
> **speedman2202 said:**
> i have stuck with something ..... i have 5 partitions (C , D , E , F , I) .....C partition contain WinXP and i D,E, F have my own data ....i want install Ubuntu on I partition ..... and the video u provide me not show to me how to choose a specific partition ..... can anybody help me with a clear  steps cuz i afraid to do something that will erase all my entire data ......:|

Hi , 
yes this video is for a simple dual-boot option . You need to entangle with the advanced installation from "Something Else" option. 

Choose "Something Else" . Partition editor will open. You will see there a list with all of your partitions. You will not see letters like windows (C,E,I etc). Ubuntu recognizes partitions with a different way , like dev/sda1 , dev/sda2 etc... 

You must _**choose carefully the partition **_you want to install Ubuntu and you must delete this partition. When you delete it , you will see "Free Space" . Click on that and create a new partition , filesystem: Ext4 with journal. You must mount / root there. 
Then you can install Ubuntu . 
Another problem might be the swap-area. Ubuntu needs a swap-area for operations like Suspend to ram . So ...
**a better option **might be to create 2 partitions. One for / root and one for swap area. Swap not need a filesystem , it is just swap. 

See this tutorial here.. [http://www.youtube.com/watch?feature=player_detailpage&v=3HANcetKsqc#t=162s](http://www.youtube.com/watch?feature=player_detailpage&v=3HANcetKsqc#t=162s) , it is from specific time and forward . You will get an Idea on how advanced installer works. 

**The most important thing is to backup somewhere your data.** Advanced installer is not easy for novice users. 
**Tip:** Can recognize the partition you want to delete from size. e.g: If partition is 10GB , you will see a size like 10000MB (maybe less)  (Ubuntu will display all sizes in MBs)
Thanks.

---

### Post by UbuntuNerd on 2012-08-13
sorry about the late reply i was in school, to add to all other replies if you dont make those partitions you will more then likely get an error along the lines of "No root file system define" and i will not let you install or "no boot partition define" so you have to do it unless you install ubuntu on your full drive and in that case you wont have to do none of the partion steps.

if you look at the guide i posted it says it uses 4gb you said you had 8gb  which should be plenty hope that helps !!!!

---

### Post by speedman2202 on 2012-08-14
> **UbuntuNerd said:**
> sorry about the late reply i was in school, to add to all other replies if you dont make those partitions you will more then likely get an error along the lines of "No root file system define" and i will not let you install or "no boot partition define" so you have to do it unless you install ubuntu on your full drive and in that case you wont have to do none of the partion steps.

if you look at the guide i posted it says it uses 4gb you said you had 8gb  which should be plenty hope that helps !!!!


i have install it successfully but when i install it's take more time (about 3 hours) also i have checked on download music package while install and already connected to internet .... when retrieve 11 to 45 ...... it's take much more time and i guess he download files but it was too slow in download (instead my internet connection 512kbps) and when i open firefox while install .... too slow and even hard to open any website .... so i do skip for this downloaded package tell he become fast in download other component (like hardware ) then he finished and when restart the OS too slow also cant try connect  to my router ....... so i dont know whats wrong ....  i feel guilty that i think in move from windows to Linux ..... so i want post my installation logs to show my problem but i dont know how to get from ubuntu OS , also why it's take much more time in download package (is it too big) .....also system too slow on my pc , and here my hardware info

cpu: intel celeron 2.66/256kb
ram: 256*2
HDD: 80 GB
VGA: ATI Radion 64MB


thx

---

### Post by speedman2202 on 2012-08-14
up :|

---

### Post by speedman2202 on 2012-08-14
Up

---

### Post by HermanAB on 2012-08-16
With a machine like that, you should install Lubuntu.  The regular Ubuntu will be unusable, exactly as you found.

---

### Post by mastablasta on 2012-08-16
...or Xubuntu, maybe even Kubuntu with low-fat settings package. Both should use less than 200MB Ram.
 
Ubuntu uses 3D acceleration which might not be suported well on your GPU. And that could be the reason for a slow down. before installing other desktop environments, you could try Unity 2D or Gnome classic mode.

---

### Post by smartboyhw on 2012-08-16
More info by the previous post: Unity 3D will be shipping as default in recent 12.10 builds.

---

### Post by speedman2202 on 2012-08-17
ok guys , the sum up is

i want move from WinXP to Linux world , and i do small search and many pple suggest me try first ubuntu .... also i need to learn Linux shell commands .... so i decide try Ubuntu

so what u all suggest me ....?????

thx

---

### Post by Morderwurst on 2012-08-17
> **speedman2202 said:**
> ok guys , the sum up is

i want move from WinXP to Linux world , and i do small search and many pple suggest me try first ubuntu .... also i need to learn Linux shell commands .... so i decide try Ubuntu

so what u all suggest me ....?????

thx

[Lubuntu]("http://lubuntu.net/")

---

### Post by speedman2202 on 2012-08-17
> **Morderwurst said:**
> [Lubuntu]("http://lubuntu.net/")
thx for replay

but can u tell me what deffrance between K,L,Xubuntu and the Ubuntu it self???

thx anyway :)

---

### Post by mastablasta on 2012-08-17
they use different desktop environment (DE): [http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment). 
in linux you can add the desktop of your choice or a windows manager on top of kernel (core).
 
since they use a different desktop it means they "draw" windows in different ways. so if Unity doens't work Lubuntu might. 
 
 
K, L, X refer to KDE, XFCE and LXDE which are desktop environemnts. However under them Ubuntu core system is running.
 
in windows XP desktop environemnt is Luna, while in Vista and Win7 its Aero.

---

