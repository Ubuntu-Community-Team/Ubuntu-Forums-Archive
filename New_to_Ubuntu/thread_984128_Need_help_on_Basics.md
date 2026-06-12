---
title: "Need help on Basics"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by zoner on 2008-11-16
Hello:

I just installed Ubuntu for the first time and have the following questions:  

First,I run my desktop on an HF289H (1900 x 1200) monitor.  How do I get Ubuntu to run on this resolution?

Second, How do I get the Adobe flashplayer to install and work in Firefox?  I tried to install under the Ubuntu 8.03 plus option and it didn't work.

Third, I have an Epson printer connected through wireless.  How do I get the printer to work?

Fourth, being brand new to Ubuntu, what are the coolest and best things to try?

Thanks for any help.

---

### Post by chrisod on 2008-11-16
Monitor - I think you will need proprietary drivers to operate at that resolution. Are drivers available for your monitor?

Flash - go to Adobe.com and download flash 10 for Linux. Install instructions are available there too.

Printer - same issue as the monitor. Is there a Linux driver available, and have you installed it? 

Finally, I would suggest getting printing and your monitor working the way you want before you worry about new and cool :)

---

### Post by sportscrazed2 on 2008-11-16
theres any easier way to install flash just go to youtube in firefox start to play a video and install the missing plugins and restart

---

### Post by DoubleMcLovin on 2008-11-16
For your resolution it can be configured through:
"System-->Preferences-->Resolution"
If that doesn't list the resolution you like, you may have to install proprietary drivers for your video card, do this through "System-->Administration-->Hardware Drivers" and selecting the (Recommended) driver. Also if you use NVIDIA graphics card, doing this may install the NVIDIA control panel which will let you set higher resolutions through "System-->Administration-->NVIDIA X Server Settings"

---

### Post by MunkyJunky on 2008-11-16
1. For your monitor, you may need to install some proprietry drivers for your graphics card. Do you know your graphics card model/make? (ATI, nVidia,... ?). 

2. Type **Sudo apt-get install ubuntu-restricted-extras** in terminal. That's the restricted extra's package, and will install Flash, Java, and other packages very useful for running your desktop. Details are here: [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

3. I'm no good with printers, sorry! 

4. Coolest thing to try in my opinion is Compiz. This is installed by default, but I'm pretty sure you have to install the configuration manager seperate (or, atleast I've always had to). Open up terminal and type **Sudo apt-get install compizconfig-settings-manager** and when that's installed, it appears under System > Preferences > CompizConfig settings manager. Some cool things worth turning on are the **Desktop Cube, Expo, Rotate Cube, 3D windows, and shift switcher**.  If you need help getting Compiz going, either post up on the forums or send me a message, I'll give you a walkthrough if needed.

---

### Post by sportscrazed2 on 2008-11-16
when i do that why won't it let me type my password?

---

### Post by MunkyJunky on 2008-11-16
> **sportscrazed2 said:**
> when i do that why won't it let me type my password?

As a security feature, Terminal won't display anything (stars and whatnot) for each character of your password, to stop 'snooping shoulders' as it were. When it asks, just type in your password and hit enter, as terminal DOES pick it up.

---

### Post by sportscrazed2 on 2008-11-16
thanks i had no idea that if nothing was displayed it would still pick up the password

---

### Post by sportscrazed2 on 2008-11-16
do these visual effects slow down your performance or do they just look cool?

---

### Post by MunkyJunky on 2008-11-16
Depends on your hardware. I'm running a nVidia GeForce 6600LE 256mb graphics card, 2.6Ghz Intel Celeron, and 512Mb DDR2 RAM. Compiz runs really well for me though!

---

### Post by sportscrazed2 on 2008-11-16
mine is amd 64x2 1.8ghz with 2gb ddr2 and it seems fine if it does slow it down i can always disable it.  wobbly windows are so fun to play with

---

### Post by zoner on 2008-11-16
> **MunkyJunky said:**
> 1. For your monitor, you may need to install some proprietry drivers for your graphics card. Do you know your graphics card model/make? (ATI, nVidia,... ?). 

2. Type **Sudo apt-get install ubuntu-restricted-extras** in terminal. That's the restricted extra's package, and will install Flash, Java, and other packages very useful for running your desktop. Details are here: [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

3. I'm no good with printers, sorry! 

4. Coolest thing to try in my opinion is Compiz. This is installed by default, but I'm pretty sure you have to install the configuration manager seperate (or, atleast I've always had to). Open up terminal and type **Sudo apt-get install compizconfig-settings-manager** and when that's installed, it appears under System > Preferences > CompizConfig settings manager. Some cool things worth turning on are the **Desktop Cube, Expo, Rotate Cube, 3D windows, and shift switcher**.  If you need help getting Compiz going, either post up on the forums or send me a message, I'll give you a walkthrough if needed.

I tried installing the sudo apt string and it seemed to install, but when I tried to restart an error message came up about kernels, etc., and the system was hung up.  I uninstalled the Ubuntu and will re-install and try again.

What's the easiest and most stable way to through this using the double boot up option with Windows?  Thanks.

---

### Post by MunkyJunky on 2008-11-16
The easiest way would be to use Wubi (Windows Ubuntu Installer) and install it from your Windows desktop. Wubi *can* be a little bit unstable I've found, though. I'd only recommend it for trying out Ubuntu - for a 'proper' install, just use the Live CD (as follows).  The best way (in my personal opinion) is to have Ubuntu automatically resize your partitions for you while installing off the Live CD. Which, is also quite easy.

---

### Post by zoner on 2008-11-16
> **MunkyJunky said:**
> The easiest way would be to use Wubi (Windows Ubuntu Installer) and install it from your Windows desktop. Wubi *can* be a little bit unstable I've found, though. I'd only recommend it for trying out Ubuntu - for a 'proper' install, just use the Live CD (as follows).  The best way (in my personal opinion) is to have Ubuntu automatically resize your partitions for you while installing off the Live CD. Which, is also quite easy.

So if I use the live CD option I can still set up the dual boot option? Thanks.

---

### Post by MunkyJunky on 2008-11-16
Yes, when you get to the partition editor, by default (I think) Ubuntu will suggest resizing your Windows partition to make room for Ubuntu. After you've installed it, you should be dual booting Windows & Ubuntu.

---

