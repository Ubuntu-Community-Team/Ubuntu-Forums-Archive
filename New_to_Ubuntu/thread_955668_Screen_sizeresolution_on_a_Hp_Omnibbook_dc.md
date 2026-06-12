---
title: "Screen size/resolution on a Hp Omnibbook dc"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by parakoudos on 2008-10-22
I have installed the ubuntu for the very first time , and very first time trying something else than win...
Even though I had a few(hard) troubles during the installation, this forum was a major help, and I am actually Very impressed by the ubuntu 8.04.
I am now running dual boot on a HP Omnibook XE2 DC 
Cpu 600Mhz
Video: LynxEM(Not sure)4Mb
256 Mb Ram
The Problem I cannot solve is that I Have a screen 14.1" but the Ubuntu is using only the 12" OR LESS OF IT. And I cannot increase the resolution more than 800X600.(If I decrease it 640x.. I see nothing but vertical lines.)
Any Help Very Welcome...

---

### Post by o.besner on 2008-10-22
Open a console, and type :

*gedit /etc/X11/xorg.conf*

and paste the output here. When there is a problem with the display, it's most of the time found there. If you type : *man xorg.conf*, you can get more information to understand your configuration file.

---

### Post by roger_1960 on 2008-10-22
Hi

It may be easier to open a teminal 'applications-accesories-terminal' (console) and type (or copy/paste from here):

sudo displayconfig-gtk

Enter your password (wont show) and then play with the settings in the GUI for model and display.  Its best to know the max resolution of your screen before you do this.

---

### Post by parakoudos on 2008-10-22
Thank you Both Guys for so fast help...

1st. gedit /etc/X11/xorg.conf showed just a blank page...(so no error?)


2nd. sudo displayconfig-gtk    ....Very helpfull but none of the choises I tried almost all of them...Is it possible that I download the driver for Ubuntu ?
How can I find what driver is the most suitable for mehow o find what adapter do I have?

---

