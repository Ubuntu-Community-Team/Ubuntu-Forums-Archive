---
title: "Can`t run 2 monitors on ubuntu nvidia quatro 1300FX"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by horne on 2012-03-19
I installed Ubuntu and on the lunch screen before the os starts the 2 monitors run, but when the os start only 1 remain running. I have the latest nvidia drivers. I have pictures at : [http://postimage.org/gallery/hbfpojg/f826319c/](http://postimage.org/gallery/hbfpojg/f826319c/)

---

### Post by gordintoronto on 2012-03-19
Brand and model of your monitors? Their resolution? Version of Ubuntu?

---

### Post by horne on 2012-03-20
Monitors:
Fujitsu Siemens scenic-view p20-2
EIZO S1961

Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10

---

### Post by gordintoronto on 2012-03-20
Have you run Nvidia X server settings? Specifically, the "Display configuration" tab.

---

### Post by souravc83 on 2012-03-20
Try disper.
If you do not have it installed, 
install it with:

[HTML]sudo apt-get install disper[/HTML]

then type 

[HTML]disper -l[/HTML]

to list the monitors connected, and then to clone, type

[HTML]disper -c
[/HTML]
or to extend the display to the other monitor, use 

[HTML]disper -e[/HTML]

---

### Post by horne on 2012-03-22
> **souravc83 said:**
> Try disper.
If you do not have it installed, 
install it with:

[HTML]sudo apt-get install disper[/HTML]

then type 

[HTML]disper -l[/HTML]

to list the monitors connected, and then to clone, type

[HTML]disper -c
[/HTML]
or to extend the display to the other monitor, use 

[HTML]disper -e[/HTML]

on first command i get 
```
root@orlin-OEM:~# sudo apt-get install disper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package disper

```

---

### Post by horne on 2012-03-22
> **gordintoronto said:**
> Have you run Nvidia X server settings? Specifically, the "Display configuration" tab.


Chech this
[IMG]http://s16.postimage.org/fggvdierp/Screenshot_at_2012_03_22_14_09_09.png[/IMG]

---

### Post by gordintoronto on 2012-03-22
You said you have "the latest nvidia drivers," but I'm not sure what that means. Did you run Additional Drivers and install "version current"?

When I Googled the error message, I ran across this: "The problem is solved in 195.36.08-0ubuntu2," but that message was almost two years old.

Another suggestion was to put this in xorg.conf:

Section "Device"
 Identifier	"Default Device"
 Option	"NoLogo"	"True"
        Option "twinview"
EndSection

---

### Post by horne on 2012-04-02
where is xorg.conf: ?

---

### Post by gordintoronto on 2012-04-02
When I Googled: xorg.conf locations,
this appeared:  /etc/X11/xorg.conf

Note that there's a capital 'X' in the location.

To modify the file, use this command:
gksudo gedit /etc/X11/xorg.conf

---

