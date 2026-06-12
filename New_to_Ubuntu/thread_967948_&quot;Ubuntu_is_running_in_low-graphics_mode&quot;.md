---
title: "&quot;Ubuntu is running in low-graphics mode&quot;"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by bbi5291 on 2008-11-02
I just started using Ubuntu (so I have the version 8.10) and I am having some trouble with my display. My video card is a NVIDIA Vanta/Vanta LT (quite old, part of the "Legacy" series). Originally everything was working fine, except that my screen resolution didn't go higher than 1024x768.

First I did a search on "higher resolution in Ubuntu" and I tried "sudo dpkg-reconfigure -phigh xserver-xorg". After this, when I restarted the X-server, I got some error message that I can't quite remember, something about the framebuffer device, I guess...

Then I went to the NVIDIA website to download a driver. When I tried to install it, I got the message "No precompiled kernel interface...". It tried to build a kernel interface and encountered an error (from what I see this problem is actually quite common). After doing some searching, I tried the advice of creating a blank <linux/config.h> file, but that didn't solve the problem either.

After doing some more searching, I found that the driver doesn't support Ubuntu 8.10 yet (at least that's what I think it said). But I decided to try using the nvidia-xconfig utility anyways. Now when the X-server loads, I get the error message "error parsing the configuration file" and then "Ubuntu is running in low-graphics mode".

Strangely enough, I still have a 1024x768 resolution, so all I really did was mess up the xorg.conf file. What drivers do I need to download and how do I fix the xorg.conf file? I have attached it (but I had to upload it as a text file...)

Edit: OK, so I restored the xorg.conf file from the earliest backup copy and now everything is back to how it was at the beginning. But I still can't get a resolution greater than 1024x768.

---

### Post by mikewhatever on 2008-11-02
You could try running <sudo displayconfig-gtk> and setting the desired resolution. Hope it works.

---

### Post by tabarraei on 2008-11-02
Hi

I have the same problem,
I have ATI radeon 9600, but ubuntu 8.10 does not know it and all I got is 800*600

please somebody help

---

### Post by oldsoundguy on 2008-11-02
This worked for me:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

There are provisions for NVida and ATI cards .. both new and legacy programs are also available.

worth a shot .. you can always REMOVE the program as it does have it's own removal utility.

---

### Post by Axis on 2008-11-02
I had a similar problem and put all of these into a script and it solved my problem.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

Of course you could alternatively just type them all into terminal.

---

### Post by Axis on 2008-11-02
Double posted? Sorry

---

### Post by Acksys on 2008-11-02
Axis,

I upgraded from Gutsy to Intrepid and kept getting this "error parsing config file" followed by "Ubuntu is running in low graphics mode". Your fix worked perfectly for me. Thanks!

---

### Post by Slap2tickle on 2009-02-08
Hi everybody, I've been looking high and low for a solution but this is the closest I have come to getting one so I'll post here, I recently upgraded from hardy heron to intrepid and had success on my laptop but something went wrong on my desktop, when I restart I get an error message saying (after the start up progress bar finishes turning orange)
"Ubuntu is running in low-graphics mode, the following was encountered, you may need to update your configuration to solve this.
Failed to initialize the kernel module
screen found but none have a usable configuration"
 (There are some lines missed out from that)

I tried the solution on here which was successful for starting up but when I try to enable the desktop features it won't work, I find that the NVIDIA drivers have been disabled, when I enable them and restart I get the start up problem with the warning message (after the start up progress bar finishes)again.
I found one suggestion to upgrade the drivers manually but when I do this I get 
"The CC version check failed
The compiler used to compile the Kernel (gcc 4.2) does not exactly match the current compiler (gcc4.3)."

Please help as I'm banging my head on the wall and I'm completely new to this

---

### Post by sgc818 on 2009-10-09
> **Axis said:**
> I had a similar problem and put all of these into a script and it solved my problem.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

Of course you could alternatively just type them all into terminal.

Just to say this worked perfectly thanks

---

### Post by windguy on 2010-01-10
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot


Thank you very much to "AXIS"...This helped me with my 42" Sony. This helped
with my VGA connection. Now I'm having problems with my DVI to HDMI. Just
installed a NVidia GeForce 8400GS, TD512EH. No output, won't recognize my card. 
But thank you very much for getting me to this point. Ubuntu on a 42" Sony
looks great!

---

