---
title: "Ubuntu 13.10 Blank Screen after logout"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by abhishes on 2013-12-29
Hello,

I have installed the Ubuntu 13.10 distribution of Ubuntu.

After I logoff, many times, I get a blank black screen. when this happens even if I wait for a very long time, it does not eventually turn into a login screen.

the only thing I can do now is to restart the machine by pressing the power button.

I searched the web and many people resolved the issue by editing a file called kdmrc. but on my system where is nothing called kdmrc

many other people also resolved it by editing [COLOR=#000000][I]/etc/X11/gdm/gdm.conf but on my system where is no file called gdm.conf

I am using the standard 13.10 Ubuntu

Because of this problem I have faced data corruption because many processes have to be terminated abnormally when the hard boot occurs.

Pardon me if this is a very basic question or something which has been answered many times... but none of the solutions listed on the internet are working for me because the files mentioned in solutions are not present on my system[/I][/COLOR]

---

### Post by 3grciii on 2013-12-29
Ubuntu comes in many flavors, and it&#8217;s designed for very different kinds  of users. Edubuntu, Ubuntu Studio, Ubuntu Gnome, Saucy Salamander.... If we knew which release you are running we would be able to assist you. The System Monitor system tab tells me that I am currently using gnome 3.4.2 under ubuntu 12.04 (precise) 32-bit. Can you provide a bit more information? I recall having similar problems with a system utilizing Intel HD graphics (on-chip core i3). You can get a list of hardware from a terminal with the command sudo lshw. This may also be helpful.

---

### Post by abhishes on 2013-12-29
wow. when I do system information. I don't even have a tab called system.

I did 

head /proc/version It says

Linux version 3.11.0-14-generic (buildd@allspice) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013

the way I installed this is I searched the web for Ubuntu ISO and then downloaded the ISO file from ubuntu site. The version is 13.10 64 bit saucy. I am pretty sure that I am not using kde.. I am using what comes by default with Ubuntu 13.10 saucy iso

If I do

gnome-session --version

it says 

gnome-session 3.9.90

---

### Post by pedro14 on 2014-03-19
I had the same problem and I solve with **THIS** [http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10/](http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10/). **YES**, after a month searching a solution 6 ****ing pixels were the problem.

;)

---

