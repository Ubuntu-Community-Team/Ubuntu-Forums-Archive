---
title: "Ubuntu will not start up"
date: 2018-08-10
forum: New to Ubuntu
---

### Post by florp on 2018-08-10
Hi. I have been using Ubuntu for about a month. I was playing a game and then it just stopped working. I restarted my PC and when I chose to start Ubuntu it flashes something, to fast to see, and then the screen just go black. I can go into repair mode and go into Ubuntu like that, but I can not use it like that. The display drivers is not installed. I have tried to reinstall Ubuntu, but the same happens when I try to. Black screen. Plz help:(

---

### Post by kc1di on 2018-08-10
Do you by any chance have a Nvidia video card? 
if you do chances are that the latest update which updated the kernel messed up the driver. 

if that is the case you can boot to the older kernel by hitting the shift key as your machine is boot to reveal the grub menu then going to advanced and selecting the one with kernel 4.15.0.29
this is assuming you are running ubuntu 18.04.

---

### Post by florp on 2018-08-10
Thank you for the response.
When I start up my pc it gives me a window that give me 4 options. Ubuntu, Advanced options for Ubuntu, Windows boot Manager and System setup. I have chosen Ubuntu and hit Shift, but it just went dead. Advanced options gives me 4 options Linux 4.15.0-30- Generic, then recovery mode, then Linux 4.15.0-29- Generic and then the recovery mode for that.

Where mustI go?

---

### Post by florp on 2018-08-10
Ok. I did downgrade to 4.15.0-29 but it did not help.

---

### Post by kc1di on 2018-08-10
We need a little more info on your machine, make, model, ram video card etc.

---

### Post by florp on 2018-08-10
ok. It is a I5 Intel. Radeon RX 470 Armor 8G. 8G ram. 2T HHD

---

### Post by NM5TF on 2018-08-10
@florp...

you might find some help here  [https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux")

good luck...

tommy

---

### Post by NM5TF on 2018-08-10
> **florp said:**
> Thank you for the response.
[COLOR="#00FF00"]When I start up my pc it gives me a window that give me 4 options[/COLOR]. Ubuntu, Advanced options for Ubuntu, Windows boot Manager and System setup. [COLOR="#FF0000"]I have chosen Ubuntu and hit Shift, but it just went dead[/COLOR]. Advanced options gives me 4 options Linux 4.15.0-30- Generic, then recovery mode, then Linux 4.15.0-29- Generic and then the recovery mode for that.

Where mustI go?

the little "window" with the 4 options is the GRUB MENU......you say that you selected Ubuntu & then keyed shift.....[COLOR="#FF0000"]you should have just keyed ENTER/RETURN to start Ubuntu[/COLOR]....

the confusion arose when the  previous helper told you to key SHIFT during boot.....that was only to get to the GRUB MENU....he didn't know that you have a dual-boot with Windoze....

did you go to the web page I referenced earlier & look at the driver for your card ???

tommy

---

### Post by florp on 2018-08-11
Hi Tommy.
I did go to the site and did every thing. At the end it gave me this 'Module build for 4.15.0-330-generic was skipped since the kernel header for this does not seem to be installed.' 'dgpu required KMS'

I did not word when I started up
PS.I would like it if I did not have that Grub menu.... when this is working. I do not have Windows on this machine.

---

### Post by NM5TF on 2018-08-11
> **florp said:**
> Hi Tommy.
I did go to the site and did every thing. At the end it gave me this 'Module build for 4.15.0-330-generic was skipped since the kernel header for this does not seem to be installed.' 'dgpu required KMS'

I did not word when I started up
PS.I would like it if I did not have that Grub menu.... when this is working. [COLOR="#FF0000"]I do not have Windows on this machine[/COLOR].

if you "[COLOR="#FF0000"]don't have Windows on this machine[/COLOR]" then why do you have Windows Boot Manager & System Setup in your GRUB menu ???

something wrong here.....

when you installed Ubuntu did you first wipe the disk of Windoze ???

it almost seems like it was installed dual-boot alongside Windoze 

if you still have a good Ubuntu live install media, and you REALLY don't want Windoze on that machine, you could always wipe the disk and do a "fresh install" of Ubuntu...your choice of course

that's what I did when Win Vista drove me from Windoze to the freedom of Linux...

tommy

---

