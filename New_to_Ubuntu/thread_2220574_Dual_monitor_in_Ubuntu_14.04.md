---
title: "Dual monitor in Ubuntu 14.04"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by madmaxou on 2014-04-28
Hey Folks.

After a two year hiatus from Ubuntu (and Linux in general), I finally decided to try Ubuntu out once again.
So I installed Trusty Tahr two days ago and found that only the screen connected through the DVI-port of my graphics card worked. Another monitor connected through the HDMI-port though will tell me it cannot get any signal..
I wouldn't really mind if I were not accustomed to having lots of screen 'real estate'. Once you buy that second monitor it's nigh impossible to go back to working, browsing, etc. on just a single screen without the sensation of confinement.
I've digged through an abundance of forum posts on that matter, but I simply don't have the expertise to judge if the attempted fix suits my issues or even trying to understand what the proposed remedy does to repair the problem at hand (I'm beginning to feel like a monkey with a keyboard). After trying a few things which didn't work and messing up the whole system at it, I made a clean reinstallation of Ubuntu 14.04.
A bit more information about my current system: 

[LIST]
[*]Clean, unchanged installation of Ubuntu 14.04
[*]nVidia GTX 780 Graphics chip
[*]Intel i5 processor
[*]If you need anything more, I will edit my post
[/LIST]

Thanks for any advice, expression of condolence, ....

Max

EDIT: Installing the nVidia proprietary driver completely ****ed my system up. Once I log in I am presented with the standard wallpaper and am able to move the mouse, but nothing else. The sidebar won't show up, right clicking doesn't open a context menu and pressing ctrl alt 1 will only give me a black screen. Does anyone know how to revert the installation of the driver, so I can at least access my ubuntu again?

---

### Post by Vladlenin5000 on 2014-04-28
You need nvidia's proprietary drivers, obviously.

---

### Post by madmaxou on 2014-04-28
> **Vladlenin5000 said:**
> You need nvidia's proprietary drivers, obviously.

Obviously. Thanks for your insight.
So how do I do that exactly?

---

### Post by Vladlenin5000 on 2014-04-28
The easiest way is simply open the additional drivers tab in Software & Updates, select the recommended version, let it install - it can take several minutes - and then reboot.

---

### Post by Don_Tai on 2014-05-01
I have only recently done dual monitors with Lubuntu 14.04, but they should be similar.

You might want to try the default ubuntu Nvidia driver, Nouveau, before you go proprietary. It might work and might be more stable. It worked well for my older Nvidia card. I don't know enough about ubuntu to undo the proprietary driver, other than remove the video card, install a non-Nvidia card, which will reset the driver, log on, then remove the NVidia driver.

Once you solve the driver problem you should have a program called "randr" that you use to turn on the second monitor. As I use lxde my program is in preferences > monitor settings, and is called "lxrandr". After you turn in your second monitor they will mirror each other. From Synaptics download a program called ARandR, which will let you configure your monitors side by side, then save these settings to a disk file, so you can recall it when you reboot.

It is not so hard. Good luck!

---

### Post by sammykur on 2014-05-02
are you pressing 1 or f1?

if you are pressing 1 try pressing  ctrl+alt+F1,but reboot the computer and do it at the log in screen(do not sign in at this screen)

The screen should go black and ask you for your username and password

login and enter the following

```
sudo service lightdm start
```

---

### Post by sammykur on 2014-05-02
If that doesnt work ,try this in a terminal


```
sudo apt-get remove --purge nvidia*
```

(you may have to run the lightdm command again at the login if the desktop doesnt show up at all)

and then install the nvidia driver from additional drivers

this may help you out if neither works, 

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

if you still cant get the HDMI monitor to work and need a newer driver you could try installing the driver with the xorg-edgers repository.

They are experimental but I have had no problems and have a dual monitor set up running the 331.67 driver on 12.04

visit their website first though,   [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


```
sudo add-apt-repository ppa:xorg-edgers/ppa 

sudo apt-get remove --purge nvidia*

sudo apt-get update

sudo apt-get install nvidia-331

sudo apt-get install nvidia-331-uvm

```

---

### Post by rafael14 on 2014-07-29
Hi all! 
After google a lot I found very good solution to instal NVIDIA drivers . 
My video board is Geforce 540m .

[COLOR=#ff0000]1: You need install bumblebee .[/COLOR]
(thx for the [http://askubuntu.com/questions/438601/ubuntu-14-04-nvidia-propriatery-driver-install](http://askubuntu.com/questions/438601/ubuntu-14-04-nvidia-propriatery-driver-install) answered by [Vivek]("http://askubuntu.com/users/260517/vivek") )
First remove current Nvidia installation.
  sudo apt-get purge nvidia*
sudo apt-get purge bumblebee*
sudo apt-get update
sudo apt-get dist-upgrade
  Install Kernel header if didn't already
  sudo apt-get install linux-headers-generic
  Then install bumblebee using below commands:
  sudo add-apt-repository ppa:bumblebee/stable
  For more up-to-date nvidia drivers, you need to add another PPA. As  of 12.04, this is still necessary for Nvidia GT 6xxM cards. It may be  optional for the GT 4xxM and GT 5xxM series on 12.04. When in doubt,  just install it. The command is: 
  sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
  sudo apt-get update
  Install Bumblebee using the proprietary nvidia driver: 
  sudo apt-get install bumblebee bumblebee-nvidia

2: Prime and other stuffs 


sudo apt-get purge libvdpau-va-gl1
sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-prime

3: I dont have sure if you need both (prime and bumblebee) but my geforce 540m could not be selected without install both . 

4: ubuntu init => NVIDIA X server settings   PRIME Profiles , select NVIDIA 

Hope this help .

---

### Post by cesco2 on 2015-07-09
After installing the nvidia drivers you MUST change the X config file.

Just run 
sudo nvidia-xconfig

---

### Post by riverguy99 on 2015-07-13
I had this same issue some time ago and spent a week trying to get dual displays to work.  Got tons of "this might work" help from the Forum, but never got it to work.  So I got desperate and reinstalled 12.04.  Dual displays all but configure themselves in 12.04.  There is one thing you must do, however, to make it wll work:  Log out, then when you get the log-in box, click the tiny "Ubuntu" logo in the upper right corner and change the setting from the default "3D" to "2D."  That's it.  From there, the setup is a piece of cake. 12.04 correctly identified and configured both displays all by itself.

---

### Post by randy26 on 2015-10-09
How to fix the lag when using two monitors in Ubuntu 14.04 Trusty  Using metacity fixed it for me, to install that, one can use the following commands.  sudo apt-get update ; sudo apt-get install gnome-session-flashback  then, when you log into your account pick the option to use metacity. Perhaps, using unity 2d would work as well.

---

