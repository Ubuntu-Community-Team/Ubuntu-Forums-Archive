---
title: "Installing nvidia graphics driver"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by inception8 on 2008-08-08
Hi. I'm pretty new to this whole Ubuntu/Linux OS. I decided to install Ubuntu through Sun's xVM VirtualBox. Everything is peachy. Looks nice. Wonderful. It's intriguing to learn something new and try to enjoy it at the same time.

But. It's running at 800x600. My nVidia graphics card is a GeForce 8500GT. There's no listing in Hardware Drivers. I went to nVidia's website and downloaded a run package. It wouldn't run without root privileges. So I tried the sudo command line in the terminal window and followed the nVidia instruction from their website ---> sudo sh "then the package line dot run". I assumed that's what I need to do to have root access from a little reading I did try to do.

It tells me can't open.

So I tried to do some more reading and used the Synaptic Package Manager but I have no idea what the hell is going on with that or what I need to be doing in the proper steps (as in a complete guide). Can someone please help me find a solution to installing the driver for the graphics card( and what I might need to do next) so I can please move on and start enjoying Ubuntu a little better than this resolution. It's just a little difficult running in this little window that's 1/4 of a widescreen 1680x1050 desktop. 

Thankyou very much in advance. I'm trying.
D.

---

### Post by Crafty Kisses on 2008-08-08
You can try this:
```
sudo apt-get install nvidia-glx
```
See if that solves it.

---

### Post by vandorjw on 2008-08-08
Hi, 

Virtual box provide emulated graphics.
Installing the Nvidia Drivers will not help you. (i think)

if you want you can try this. Open Terminal, (applications --> accesories --> terminal)

then type
sudo apt-get install envyng-gtk

--> this installs a program to automatically install the correct video drivers if you have an ATI or Nvidia Card.

once it is installed, open it Applications-->System Tools --> envy

and select automatically install Nvidia drivers.


PS: it won't work :)
PPS: Reply Number 2 will not work either. but feel free to try it, so you learn what it does.

but have fun trying. 

(This will work if you do not install in virtual box)

---

### Post by cdtech on 2008-08-08
Try the link in my signature (installing nvidia drivers).

Hope this helps ya........

**P.S.**
Just seen cc7gir's **P.S.** sorry....

---

### Post by Crafty Kisses on 2008-08-08
Yeah, Envy is a good approach too.

---

### Post by bumanie on 2008-08-08
There is no point installing nvidia drivers into virtualbox. Virtualbox uses the vesa video driver and does not support 3D acceleration. If you want 3D acceleration, you will have to install ubuntu onto a dedicated partition. Running windows in virtualbox has the same issue, ie one cannot play games as 3D acceleration is not supported.

---

### Post by mikewhatever on 2008-08-08
> **inception8 said:**
> Hi. I'm pretty new to this whole Ubuntu/Linux OS. I decided to install Ubuntu through Sun's xVM VirtualBox. Everything is peachy. Looks nice. Wonderful. It's intriguing to learn something new and try to enjoy it at the same time.

Are you trying  to install nvidia driver on Ubuntu running in VBOX? Can you post the output of the following command from Ubuntu:

> sudo lshw -C display

---

### Post by inception8 on 2008-08-09
Envy didn't work. But I appreciate mentioning it. I had to do a manual. That didn't work.

Damn it. :)

---

### Post by Crafty Kisses on 2008-08-09
> **inception8 said:**
> Envy didn't work. But I appreciate mentioning it. I had to do a manual. That didn't work.

Damn it. :)

Post the following output:
```
glxinfo
```

---

### Post by dross_kuh on 2008-08-09
do the following >>   right-CTRL + G  ,  then Right - CTRL + F
that will turn on auto screensizemode and put u into full screen mode.

if it does`nt then u need to install the guest addititions :/

---

### Post by Shanoes on 2008-08-09
> **bumanie said:**
> There is no point installing nvidia drivers into virtualbox. Virtualbox uses the vesa video driver and does not support 3D acceleration. If you want 3D acceleration, you will have to install ubuntu onto a dedicated partition. Running windows in virtualbox has the same issue, ie one cannot play games as 3D acceleration is not supported.

This correct. To reiterate on Bumanie's post:

** Nvidia drivers will not work if you have installed Ubuntu in Virtualbox **

From:
[http://www.virtualbox.org/wiki/User_FAQ:](http://www.virtualbox.org/wiki/User_FAQ:)

[LIST]
[*]"How come it doesn't detect my nVidia/ATI/whatever graphics card?"
[/LIST]
[INDENT]  Because the guest sees a virtual graphics card, not the host graphics card. The virtual graphics card provides the necessary VESA and VGA features to make the guest operative systems work OK. Additional features, like higher resolutions, is provided by the graphics driver included with the guest additions. More details on how to install guest additions and features of the virtual graphics card can be found in the manual. 



 [/INDENT]

---

### Post by inception8 on 2008-08-09
> **Codename said:**
> Post the following output:
```
glxinfo
```

name of display: :0.0
xlib: extension "GLX" missing on display ":0.0"
xlib: extension "GLX" missing on display ":0.0"
xlib: extension "GLX" missing on display ":0.0"
Error: couldn't find RGB GLX visual

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
--------------------------------------------------------------
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
0x21 24 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 00 None
xlib: extension "GLX" missing on display ":0.0".
xlib: extension "GLX" missing on display ":0.0".
0x32 tc 1 0 0 c . . 0 0 0 0 0 0 0 0 0 0 0 00 None

---

### Post by inception8 on 2008-08-09
> **Shanoes said:**
> This correct. To reiterate on Bumanie's post:

** Nvidia drivers will not work if you have installed Ubuntu in Virtualbox **

From:
[http://www.virtualbox.org/wiki/User_FAQ:](http://www.virtualbox.org/wiki/User_FAQ:)

[LIST]
[*]"How come it doesn't detect my nVidia/ATI/whatever graphics card?"
[/LIST]
[INDENT]  Because the guest sees a virtual graphics card, not the host graphics card. The virtual graphics card provides the necessary VESA and VGA features to make the guest operative systems work OK. Additional features, like higher resolutions, is provided by the graphics driver included with the guest additions. More details on how to install guest additions and features of the virtual graphics card can be found in the manual. 



 [/INDENT]

Heh. I appreciate that. Yeah I think I've figured that out actually. You're supposed to be able to resize the virtual box and the guest will resize along with it (but I should still be able to change the resolution within Ubuntu to something higher than at this point 640x480). Can't I still install the nvidia drivers for Ubuntu within Ubuntu? 

I think I did install the guest additions finally. Or at least it appeared to install correctly.

---

### Post by inception8 on 2008-08-09
> **mikewhatever said:**
> Are you trying  to install nvidia driver on Ubuntu running in VBOX? Can you post the output of the following command from Ubuntu:

Yes I am trying to install nvidia driver on Ubuntu in VBox.

It doesn't appear to display this now but did when I first typed it out in the terminal window:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: VirtualBox Graphics Adapter
       vendor: InnoTek Systemberatung GmbH
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=0

I had to install the updates for Ubuntu. And then I finally got the VBoxLinuxAdditions to finally install. So that has in fact now changed.

Now when I type that command:
Hardware lister (lshw) - B.02.12.01 (this is it; the rest listed below that are switch command usage)

This is making my head spin.

---

### Post by Shanoes on 2008-08-09
> **inception8 said:**
> Heh. I appreciate that. Yeah I think I've figured that out actually. You're supposed to be able to resize the virtual box and the guest will resize along with it (but I should still be able to change the resolution within Ubuntu to something higher than at this point 640x480). Can't I still install the nvidia drivers for Ubuntu within Ubuntu? 

I think I did install the guest additions finally. Or at least it appeared to install correctly.

You could install the drivers if you want to... however I wouldn't recommend it as they don't do anything useful in VirtualBox. VirtualBox provides hides the real graphics hardware (i.e. your nvidia card) from the guest OS and provides a 'virtual' graphics card in its place. 

By the sounds of it, you will need the VirtualBox guest additions in order to get your virtual screen to resize. A quick google found this page:

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

---

### Post by inception8 on 2008-08-09
> **dross_kuh said:**
> do the following >>   right-CTRL + G  ,  then Right - CTRL + F
that will turn on auto screensizemode and put u into full screen mode.

if it does`nt then u need to install the guest addititions :/

Yeah. Thanks. That's fine. I appreciate that. But it makes no difference. Ubuntu is still displaying at 640x480 or 800x600 in that full screen mode in the center of the screen (with black all around the small central view that you have of Ubuntu).

---

### Post by PmDematagoda on 2008-08-09
> **inception8 said:**
> Yeah. Thanks. That's fine. I appreciate that. But it makes no difference. Ubuntu is still displaying at 640x480 or 800x600 in that full screen mode in the center of the screen (with black all around the small central view that you have of Ubuntu).

Try booting Ubuntu in Recovery Mode and selecting xfix, then see if it makes an improvement.

---

### Post by inception8 on 2008-08-09
> **Shanoes said:**
> You could install the drivers if you want to... however I wouldn't recommend it as they don't do anything useful in VirtualBox. VirtualBox provides hides the real graphics hardware (i.e. your nvidia card) from the guest OS and provides a 'virtual' graphics card in its place. 

By the sounds of it, you will need the VirtualBox guest additions in order to get your virtual screen to resize. A quick google found this page:

[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/](http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/)

Yeah. That's what I've been gathering. Supposedly after numerous failed attempts of trying to figure out how to install the Additions I finally managed to follow what this guys suggests - [http://allisterx.blogspot.com/2008/05/additions-and-ssh-access-to-virtualbox.html](http://allisterx.blogspot.com/2008/05/additions-and-ssh-access-to-virtualbox.html) (without the SSH) and it actually installed properly as far as I know. But apparently I have no indication as to how to change the virtual box resolution so I don't get such a tiny 640x480/800x600 window box. It's aggravating.

Ya know at this point this was all a lost cause from the start. The main interest that I initially had was to run Ubuntu within a Virtual Box to learn a little about (Linux) it and surf the web, as has been suggested, on top of WinXP.

I don't want to have to reboot just to surf and play around in Ubuntu. That's the point. If there's another way fine I'll do that.

Thanks to you and everyone else for your kind help.

---

### Post by inception8 on 2008-08-09
> **PmDematagoda said:**
> Try booting Ubuntu in Recovery Mode and selecting xfix, then see if it makes an improvement.

Cool. I'll try that. First I have to figure out how to boot Ubuntu in Recovery mode and select xfix.:popcorn:

---

### Post by inception8 on 2008-08-09
I got the additions working. All is fine for now. Thanks everyone for helping out.

---

### Post by starcannon on 2008-08-09
To any future readers of this thread.

A "Virtual Box" regardless of brand name is nothing more than a virtual computer, that is, its a computer thats built from software, not from hardware. It has drivers, devices, and all the things you'd expect, but they are all "virtual". Its like controlling another computer(guest) with your computer(host). 

The guest computer has "some virtual video card" your (the host) computer may have a nice Nvidia video card. Your (the host) computer is a separate entity from the guest computer. Consider this, if I gave you my I.P. address and let you log into my cloudbook laptop, which has a crappy VIA video card in it, and you having a nice Nvidia card in yours were unhappy with the way my cloudbook was performing, nothing in the world you did as far as trying to install Nvidia graphics drivers would help my crappy VIA graphics chipset. This is exactly the same thing thats happening with the Virtual Box. The Virtual Box is running some generic proprietary graphics chipset, it only exists virtually, all the same, your Nvidia based graphics chipset is NOT going to have any power or rule over the generic chipset in the virtual device.

Anyway, thats the best I could do to explain what is going on. If you want the cool desktop effects you can either do a Wubi install, or you can partition your hard drive and do a clean Ubuntu install, or you can buy a separate hard drive and do a clean Ubuntu install, all of which will allow you to have your cake and eat it to. You can dual boot, meaning you can still run windows with full features, and still run Ubuntu with full features, AND you can have all those nifty desktop effects in Ubuntu.

GL and most of all have fun.

---

