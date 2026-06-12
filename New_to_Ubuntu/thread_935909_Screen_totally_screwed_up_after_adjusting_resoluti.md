---
title: "Screen totally screwed up after adjusting resolution"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by sumithaswar on 2008-10-02
I have a HP Pavilion dv2945se Notebook PC with AMD Turion Machine(64-bit) and have an NVIDIA GeForce Go 7150M (UMA) graphics card with 1071MB

After goin through a forum suggestion, I tried to increase the screen resolution  
for my machine by fiddling wid the display but after makin it 1024x768 wen I rebooted the system the screen got royally messed up and I cant see anything but 4 mouse pointers and a smugged display, my system still loads properly on Windows Vista, so the problem does not seem to be of hardware...
Can anybody direct me to a proper solution of the problem even if it involves re-installing Ubuntu

---

### Post by Bölvaður on 2008-10-02
If you are unable to use ubuntu atm you can go 2 ways.

1. boot the rescue option in grub to log into command line mode
2. boot from the live cd

with both ways you can fix the files you need.
either it is changing the resolution in xorg.conf or the grub menu.
I am not too good about changing the xserver so you can hope someone comes here and help out with that. but you can add vga= (number like 792 (cant remember) which you can config after your needs, please look it up either on this forum or wikipedia). you'll find this file under /boot/grub/menu.lst

---

### Post by Zaff on 2008-10-02
what you want to do is boot under ubuntu and when you see the messed up display press Ctrl + Alt + F1. this will take you to a command line only display. Actually you can get 6 of them by choosing any F key from F1 to F6. F7 is for the graphical display.
Once you're in command line mode, login (it will ask for logging name and then password, password doesn't appear at all, that's normal) and at the prompt type this :
```
sudo /etc/init.d/gdm stop
```
It will ask for your password and, like before, this one won't appear on screen. This stops the gnome display manager. Then you want to reconfigure your x server.
If you have the nvidia driver installed then you can type the following :
```
sudo nvidia-xconfig
```
This will generate a new xorg.conf file in /etc/X11/
If you don't have the nvidia drivers installed then try this : 
```
sudo dpkg-reconfigure xserver-xorg
```
This should also generate an xorg.conf.

Try the nvidia command first if you're unsure. If it's not installed it'll tell you that the command doesn't exists, in which case try the dpkg-reconfigure one above.
Then restart gdm :
```
sudo /etc/init.d/gdm start
```
and you should have a working display. 

Changing the resolution should be possible without tweaking the xorg manually by using the screen resolution dialog in System-> Preferences or by typing the following command in a terminal :
```
sudo nvidia-settings
```
and setting it in the Nvidia dialog that'll appear.

Hope this helps.

---

### Post by gillespiea on 2008-10-02
i was just about to say press ctrl+Alt+F1 then login and use the command 

**sudo dpkg-reconfigure xserver-xorg**

i managed to do this before myself, after you've ran through all that you should be able to enable your resticted drivers and set the correct display setting.

seems i've been beaten to it, just thought i'd add that anyway :P

---

### Post by sumithaswar on 2008-10-04
Thnks a ton ZAFF ur suggestions worked wonders...
my old display 800x600 is back and is  working fine and everything seems to be normal...
I was bout to do a reinstall.
anyways
any suggestions for increasing the resolutions to 1024?
cos I tried it the last time and screwed up the display badly..

the nvidia command does not work...

---

### Post by sdowney717 on 2008-10-04
I think, IF you are using the free NV driver, you can simply delete everything in xorg.conf file, from the # comments on down, and 
xorg and the driver will autoconfigure all available resolutions on every boot.
I know this work if you have an ATI radeon. With no xorg entries, I got every resolution available and could simply select from the list.

IF you are using the NV driver from Nvidia, then you must run the nvsettings to generate the xorg,conf file. With nothing in xorg, ubuntu will choose to use the free NV or free radeon ATI driver.

This caused me so much anguish when I tried to fill up xorg with all sorts of settings to get the resolutions working. From there I learned more about xorg settings and tweaked it to give me things such as compiz running on the free driver, etc...

---

### Post by parkini on 2008-10-04
> **sdowney717 said:**
> I think, IF you are using the free NV driver, you can simply delete everything in xorg.conf file, from the # comments on down, and 
xorg and the driver will autoconfigure all available resolutions on every boot.
I know this work if you have an ATI radeon. With no xorg entries, I got every resolution available and could simply select from the list.

I too was having problems getting my resolution to set correctly until I tried this nifty little trick.  It was the only thing that fixed my problem.

Thank you!

---

### Post by Zaff on 2008-10-06
I don't know about that xorg.conf trick so you might wanna try that.
Have you looked into System -> Preferences -> Screen Resolution ?
If this doesn't work then paste your xorg.conf so that I can take a look at it.

---

