---
title: "Drivers for Nvidia Geforce FX 5700 Ultra"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by glutetoot on 2013-03-27
I have tried a number of different forums and searched for hours not the internet/youtube and just can get them to is stall. Here is what my computer specs are:

ABIT is7-v2 motherboard with a Pentium 4 3.00 ghz processor, video card is a geforce FX 5700 ulta, 2 gb of ram.  

so that is my computer I just installed a fresh install of ubuntu 12.10 on my computer, I have to boot the livecd with nomodeset to be able to install, and now after the install i have to hold done the shift key and edit the boot menu with nomodeset to boot ubuntu and even get to the desktop. 

Here is a link to the driver that i have downloaded and tried to install ([http://www.geforce.com/drivers/results/35482](http://www.geforce.com/drivers/results/35482)).  When i try to install it is gives me a error saying something about the x session is in use and that i need to reconfig it.


This is what im struggling with.  
1. on the bottom of the link i listed it mentions that nvidia gives me a utilty that will config the x server for me.  [B]BUT I CANT FIGURE OUT HOW TO USE IT????
[/B]2. I also says that i can run "man nvidia-xconfig" to learn how to edit it by hand. [B]BUT WHEN I ENTER "man nvidia-xconfig" IN THE TERMINAL, NOTHING HAPPENS?????
[/B]

**CAN SOMEONE PLEASE HELP ME FIGURE OUT HOW TO CONFIG SO I CAN RUN THE INSTALLER WITHOUT ERRORS???????????????**

---

### Post by glutetoot on 2013-03-27
i just tried to run the installer again and it is asking me to "please exit x before i install"

How do i do that is ubuntu 12.10?

---

### Post by ManamiVixen on 2013-03-27
It is never advised to use the drivers from Nvidia's site. You must use the ones Ubuntu provides as they are tested. 

To install, do "sudo apt-get update && sudo apt-get autoremove && sudo apt-get install linux-headers linux-headers-generic && sudo apt-get install nvidia-current"

---

### Post by glutetoot on 2013-03-27
so i input all the commands everything seams to be working dont know why i did not find this forum earlier.

---

### Post by deadflowr on 2013-03-28
Though it is normally not recommened to install the drivers outside of the Ubuntu repositories, there is nothing wrong with doing so.

If the problem of killing X occurs, simply press ctrl + alt + f1, login as your user and run

```
sudo service lightdm stop
``` 

this will kill X, and you'll be able to do what needs to be done. S'long as you know how to get to the file that you're trying to run/install.

As for installing from the repos, most likely you'll still need to run

```
sudo nvidia-xconfig
```

So that an xorg.conf file will be generated.

Upon a restart, open the nvidia Xserver settings app to futher configure and adjust whatever you can.

---

### Post by alphacrucis2 on 2013-03-28
The GUI way to install the nvidia proprietary drivers is via software & updates - additional drivers tab. At least that's what it called in raring. It might have been called software sources under 12.10

---

### Post by glutetoot on 2013-03-28
ok so i did what you said and it seamed to work. I did and do not have do boot with nomodeset any more!!!!!!! but  when i boot up after login i boot to a blank desktop?????

what is up with that?? did something go goofy?  i tried changing my resolution on the screen but it did not fix it.  any seggestions????

---

### Post by glutetoot on 2013-03-28
ok well i just load gnome and i have a desktop.


I went to watch some hd videos on youtube and they are choppy "really choppy".  Is it because my graphic card is ancient, its a geforce fx 5700 ultra???? or is something else wrong with the software still.  

anyone know anything about this card?  good or bad?  Is it time to upgrade??????

---

### Post by squakie on 2013-03-28
It's old, and you won't get great performance from it.  The motherboard supports an 8x AGP slot, so you would need to find an AGP video card.  Your best bet would be to look on EBay for an AGP video card.  Before you actually purchase one, post back with what you are considering so that perhaps we can help you here by determining what type of driver support and overall performance you could expect.  With the newer versions of Ubuntu use Unity, so I might suggest a slightly different variation of Ubuntu like lubuntu.

---

### Post by bogan on 2013-03-28
Hi!,** glutetoot,**

The 173.14 driver referenced in your Original Post is the correct one for a GeForce FX 5700 ultra, and drivers after that will not support your present card.

In addition the 173.14 driver is unlikely to be compatible with the Xserver-xorg of 12.04.2 or later ubuntu versions.

If you installed the present driver with sudo apt-get install nvidia-current, or from Additional drivers other than the 173 version, you will need to run: ```
sudo apt-get remove --purge nvidia-current # change the package name if different
sudo apt-get install nvidia-173
```That is in addition to downgrading to 12.04.1 or before.

So your best bet is the advise to get a better compatible video card, preferably GT 8xxx series or later, but 8AGP.

Chao!, **bogan.**

---

### Post by kyalami321 on 2013-03-28
To the OP, how much and what kind of RAM do you have on your machine? I have a similar setup on my machine

HP proprietary mobo
P4 2.80 GHz running at 533MHz
GeForce6200 256MB on PCI (newer model than yours, but not by much)
512MB DDR ram, runing at 333MHz. 

the killer on my machine is the RAM, which also causes slow video playback and general lack of snappiness with regards to the interface. When I had the same setup (same graphics + processor) on a mahcine with 2GB of RAM and an Intel mobo, stuff was pretty responsive, including HD video (like Netflix or HD on Hulu). 

consider your RAM. if there's a lot of hard drive activity on your system, particularly when you're trying to watch HD video or similiar tasks, RAM is most likely at fault. Ubuntu is writing to the swap partition in an effort to free up memory.

---

