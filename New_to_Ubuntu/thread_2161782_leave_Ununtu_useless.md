---
title: "leave Ununtu useless"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by MarsMantra on 2013-07-11
Hi. Yesterday I install Ubuntu 13.04 along with Windows 7, but i still having the same problems that with older versions. The major problem is that the battery discharge in about 25 min and the pc seems to fly. I have a Sony Vaio with intel i5 @ 2.40Ghz 4Gb ram and a hybrid video card Intel/ATI (Tarjeta interna: Intel® HD Graphics 3000 Tarjeta externa: AMD Radeon 6470M (512MB). Somebody tell me that the problem was on the drivers of the video card, so i download them from ADM´s webpage and install them, but after the reboot unity dissapear. I try to install Gnome desktop, and send me an error, then i try to uninstall unity and the same error. Now there is nothing when i log in, and Ubuntu don´t allow me to install anything, is there a restore option like in Windows? or  what can i do to recover Ubuntu without erase or affect windows´s partition?:confused:

---

### Post by VMC on 2013-07-12
I want to make sure your not left high and dry. So I will post a note here and check back tomorrow. 

I don't have have a current laptop so I don't know what may be the causing the battery drain. You could open up the "monitor" program and see what's using resources.
 
But before that lets see what or how you partitioned you hard disk. You will need to boot up the LiveCD and from a terminal type the following:

```
sudo fdisk -l
```

Also, we need to know how you installed the video drivers. It may be that it needs tweaking a bit to get things back in order.
 You mentioned you downloaded the drivers from AMD's webpage. Were they Windows drivers? Someone may have wanted you to install Linux drivers for  Ubuntu.

Here's one such link that may help you understand your issue. You may have followed the instructions already. First check it out then come back here and tell us if that's what you did to get your video drivers installed. Here's the [BinaryDriverHowto for ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

I'll check back here tomorrow to see if you have received more help.

Edit: there is a Recovery option, but it may not help you with your issue. It should have been an option on the grub boot page.

---

### Post by mastablasta on 2013-07-12
this is how you install additional drivers in ubuntu [http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)
or: [http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/](http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/)

you probably complicated too much and messed it all up by doing it manually. you need to remove the installed deriver and then install them again.

you might also want to do some reading here: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

### Post by newb85 on 2013-07-12
> **mastablasta said:**
> this is how you install additional drivers in ubuntu [http://www.psychocats.net/ubuntu/drivers](http://www.psychocats.net/ubuntu/drivers)
or: [http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/](http://linuxg.net/how-to-install-additional-drivers-in-ubuntu-13-04-from-the-gui/)

you probably complicated too much and messed it all up by doing it manually. you need to remove the installed deriver and then install them again.

[s]Proprietary drivers for AMD cards aren't in the repositories, so they have to be installed manually.  The methods you pointed out don't apply.[/s]

---

### Post by mastablasta on 2013-07-12
> **newb85 said:**
> Proprietary drivers for AMD cards aren't in the repositories, so they have to be installed manually. The methods you pointed out don't apply.

they aren't? then how did i install them then just last weekend using additional drivers?

they are, but you need to enable partners repository in software center sources. it even offered me two version i just went with first one. seems to be working fine.

edit: unless Kubuntu does things so much differently... cause we actually installed them in Kubuntu 13.04.

edit2: no, they are there in Ubuntu as well: 

[http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/](http://www.makeuseof.com/tag/should-you-use-amd-proprietary-graphics-drivers-how-do-you-install-them-ubuntu/)

[http://askubuntu.com/questions/302105/ubuntu-13-04-and-amd-proprietary-graphics-drivers-with-ppa](http://askubuntu.com/questions/302105/ubuntu-13-04-and-amd-proprietary-graphics-drivers-with-ppa)

---

### Post by javierrivera on 2013-07-12
Unluckily hybrid card support is quite poor in Ubuntu (althoug NVIDIA is better), you battery is beign drain so fast because it's quite possible that your computer is using both video cards at the same time.

You need to uninstall the official drivers, as they (likely) don't support your card, look here:

askubuntu.com/questions/74171/is-my-ati-graphics-card-supported-in-ubuntu

In the first answer there is an explanation on how to revert to the original drivers.

Afterwards, you can check here for some possible solutions to make your video card work:

[http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel](http://askubuntu.com/questions/21455/how-to-manage-two-video-cards-on-a-laptop-ati-and-intel)

---

### Post by Mark Phelps on 2013-07-12
> Somebody tell me that the problem was on the drivers of the video card, 

While that part could be true, going to AMD and downloading drivers was a mistake.

You have Switchable Intel/AMD drivers -- which pose a serious problem in Linux.  You can read through this thread to get an idea of what you're up against: [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics")

---

### Post by MarsMantra on 2013-07-12
Allright, thanks everybody for the help, I tink i got the solution, at least for the video card problembs.
After try with all the solutions you post on, I just reinstall ubuntu, but i do with the 12.10 version instead of the 13.04 that i got. after that, vmc's solution ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) was the one that make the drivers work properly.
Now the temperature is about 50 °C and my pc doesn't seems to fly :D.
Again thank's everybody for your help.):P:p

---

### Post by VMC on 2013-07-12
@MarsMantra,

Great job. If your satisfied with the results, then can you mark this topic [solved]("http://ubuntuforums.org/showthread.php?t=2121377"). 

Also, I almost forgot - **Welcome to the forums!**

---

