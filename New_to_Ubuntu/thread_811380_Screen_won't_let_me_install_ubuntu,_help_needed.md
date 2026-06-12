---
title: "Screen won't let me install ubuntu, help needed"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Tichondrus on 2008-05-29
Well, here's my problem:
I have the following:

-edit-

I downloaded the 64 bit version, not sure if that was the right thing to do, so if you could advice me about it as well, I'd be thankful.

-/edit-

Core 2 Duo.
1 GB RAM.
G-Force 7100 GS.

The sad thing seems to be that my screen (17'', brand: olivetti, max resolution = 1024*768, max refresh rate on that resolution = 60  mhz), won't let me install ubuntu.

It happends as follows:
1- I get the in and reboot.
2- Ubuntu shell boots and it asks me of what to do.
3- I choose install and it loads some stuff, and then BANG, the screen goes out of range and turns itself off.

I need help here, 've been trying to get into linux for a while now and to know my screen is the issue...let's say makes me want for it to feed barbeque fire.

---

### Post by overdrank on 2008-05-29
> **Tichondrus said:**
> Well, here's my problem:
I have the following:

-edit-

I downloaded the 64 bit version, not sure if that was the right thing to do, so if you could advice me about it as well, I'd be thankful.

-/edit-

Core 2 Duo.
1 GB RAM.
G-Force 7100 GS.

The sad thing seems to be that my screen (17'', brand: olivetti, max resolution = 1024*768, max refresh rate on that resolution = 60  mhz), won't let me install ubuntu.

It happends as follows:
1- I get the in and reboot.
2- Ubuntu shell boots and it asks me of what to do.
3- I choose install and it loads some stuff, and then BANG, the screen goes out of range and turns itself off.

I need help here, 've been trying to get into linux for a while now and to know my screen is the issue...let's say makes me want for it to feed barbeque fire.

HI  and welcome, Hi when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 or 775 and then hit enter. Hope this helps. Good luck! 
Edit thought the op had it installed

---

### Post by Malta paul on 2008-05-29
Hi, I guess you downloaded the Ubuntu live CD.?
Can you boot up with this disk? This will not install to your HD and should detect your monitor. 
If you can boot as far as the menu, check out your CD.

A little more details will help:)

---

### Post by Tichondrus on 2008-05-29
No, I downloaded the install CD... I think there would be no "Install" option else...

Actually it has both, the live and the install in one, or so it seems, since tehre's an option to run it withow intalling as well as one to install in the menu.
The download link i used was this:
[http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&arch=amd64&mirror=http%3A%2F%2Fubuntu-releases.patan.com.ar%2F&debug=&download-button=](http://www.ubuntu.com/getubuntu/downloading?release=desktop-lts&arch=amd64&mirror=http%3A%2F%2Fubuntu-releases.patan.com.ar%2F&debug=&download-button=)

I don't know what kind of aditional information could be given, but I'll be more than glad to offer it.

Thanks to those who tried so far and in advance for the next posts.

---

### Post by Thanoulis on 2008-05-29
Maybe its something with the Refresh rates of your monitor...i have seen this in older versions...
Try to download the alternate CD, install from there, and log in a terminal (e.g Alt+Ctrl+F2)
Then type:
```
sudo nano /etc/X11/xorg.conf
```
There should be something like this: 
```
Section "Monitor"
      Identifier   "Monitor0"
      VendorName   "Monitor Vendor"
      ModelName    "Monitor Model"
      HorizSync    30-107
      VertRefresh  48-120
EndSection
```
Type the *HorizSync* and the *VertRefresh* lines, then save and reboot.It should work, i believe. 
But keep in mind that these values are rather generic ones.

---

### Post by Malta paul on 2008-05-29
If I were you, I would first try to install the live CD and if your system crashes because of detecting the incorrect video resolution. You can do as 'overdrank' said use F7 to try another resolution.
Good luck:)

---

