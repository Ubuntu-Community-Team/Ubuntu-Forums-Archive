---
title: "Copy the Cd, Boot on Flash Drive and Install Ubuntu, is that posible?"
date: 2008-05-01
forum: Philippine Team
---

### Post by robinx1578 on 2008-05-01
My Dvd Drive is malfunctioning, theres no way i can load the distro. Is it possible to load the install cd on the Flash drive n make it bootable so that i can install ubuntu. Im downloading the ubuntu 8, 64bit edition, if you have any idea pls let me know. Thnxz in advance... 

-=Hp Pav DV2315nr, turion 64x2, 1 gig ram, 160 hd=-

---

### Post by loserboy on 2008-05-01
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by Samhain13 on 2008-05-01
I have an idea, since you ask. It doesn't concern a flash drive but a partition.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

It's the guide I used for installing 7.10. I have a faulty CD drive also.

---

### Post by dodimar on 2008-05-01
I think this one could be of help (since I believe you don't have any existing Linux installation and you don't have to use your optical drive for this one).

[Install Ubuntu 8.04 From USB drive]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/")

---

### Post by robinx1578 on 2008-05-01
Thnxz for all the support guyz. Its seems very confusing for me he3 , Maybe i spent a day for this one. U know i have some gigz of data on my notebook i dunno where to put it since my dvd drive is not working. 

Guyz have u experience setting ubuntu 8 on a notebook (specifically HP PAV Laptop) have u encounter any hardware incompatibility issue  especially in wifi device, graphics n etc?

---

### Post by dodimar on 2008-05-01
Sorry man, I have a desktop.

But if you want to back up your data from your HD, you can get a spare HD and use an HD enclosure (USB), if your data isn't that big (around 1GB), get a USB drive enough for your files and copy it there (but I think you'll be using your drive for installation, if you can borrow from someone, it'll be better), in short, look for external storage device (aside from optical of course)...

---

### Post by killer_d76 on 2008-05-02
installing Ubuntu on laptop was the easiest OS to install! (in my own opinion and i'm a newbie in terms of OS's installation ) why?.. because most of the driver for your hardware is already included, and if not, you could easily download it on the net with Ubuntu's guidance, i have a Neo Empriva Laptop with XP on it, all i did was run the installation disk (well in your case a flashdrive and do the SOP **"Backup your files things first!!!"**) just follow the instruction (_use the default settings except time settings_) normally you would end up with a 50/50 hard disk drive partition and a boot grub (it's where you pick or choose wich OS to use during boot up)and your set! :guitar:

---

### Post by robinx1578 on 2008-05-02
@ dodimar
          Hi, at last my ubuntu is up and running, your link seems to be useful man although it took me to endless link but still in the end it works. My ubuntu is running on a 20g usb hard drive, i just have one more problem, my wifi isn't working  all i can do for now is to connect via wire.. 

@ Killer_d76
          Hello, thanxz for the reply its seems very easy on you setting up the OS. And i agree with you however if you read my post i got a little situation here which kinda different. Installing OS via optical drive is flawless all you have to do is click, read and decide. Installing Ubuntu without optical drive is more challenging, you have to make your usb drive boot and install it from there and believe me its more easy reading the procedure than doing it :).

---

### Post by dodimar on 2008-05-02
> **robinx1578 said:**
> @ dodimar
          Hi, at last my ubuntu is up and running, your link seems to be useful man although it took me to endless link but still in the end it works. My ubuntu is running on a 20g usb hard drive, i just have one more problem, my wifi isn't working  all i can do for now is to connect via wire.. 


yeah, lots of links.. but it's helpful. glad your system is working now (mine's not, I wont be home this weekend to setup it up).

regarding wifi, it's a problem Linux hasn't yet resolved, but there is always a workaround for that. you can check this one [<<link>>]("http://ubuntuforums.org/showthread.php?t=202834")(I know you're new to Linux, but don't be intimidated by too much codes). This post regarding wifi was updated just a few days ago..

---

### Post by robinx1578 on 2008-05-05
My unit is running smoothly for now.. still im having problem with the ndiswrapper... I need this to access my wifi.

---

### Post by killer_d76 on 2008-05-06
hey, i just got an idea, isn't it possible for you to remove you hard disk drive, plug it on an USB to SATA, borrow an old computer from your friend that has a working DVD drive and remove your friends HDD (to avoid data loss on his or her HDD)plug in your HDD on the USB port, then try to boot on CD, and click install,perhaps doing this procedure Ubuntu will recognise your drive as the only HDD on the system and will install ubuntu there, once installed plug it back in your laptop, restart your laptop!:popcorn:

---

### Post by dodimar on 2008-05-07
Ei robin, are you running your Ubuntu from an external drive or you were able to install Ubuntu to your laptop's HD?

---

### Post by robinx1578 on 2008-05-07
@ killer
        Yeah its possible but i dont want to be that way.. Aside from that ubuntu wont need a large space to put in.. Im have 160gig on my laptop, Im still running dual os, in my side i cant simply remove MS, i have a lot of stuff there that wont run on ubuntu. 
        Besides running ubuntu on an external drive is quite fun. All i have to do is plug n play. 

@ dodimar
       Im running ubuntu on external HD, I dont want to put it on my HD, neither i dont want a dual boot in the same HD. its bad for Ubuntu.. coz when windows fail it will also wipe out the Grub boot loader and its menu.lst configuration file. and if windows wipe out the boot loader it will only boot to windows even though Ubuntu is still there it wont be reachable. its repairable but.... For me its better to be this way.

---

### Post by dodimar on 2008-05-08
Hmmmn... I see and I agree. That's the problem I have now. I can't run Ubuntu Cause Grub has Error 18 because of partitioning problems (cause I dual boot XP and Linux).

---

### Post by robinx1578 on 2008-05-08
it happens to me before but not in ubuntu. im using mandrake when i encountered that kind of problem. Maybe this will help [http://ubuntuforums.org/showthread.php?t=7051](http://ubuntuforums.org/showthread.php?t=7051)

---

