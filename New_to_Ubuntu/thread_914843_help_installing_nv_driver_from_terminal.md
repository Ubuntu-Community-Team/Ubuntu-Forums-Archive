---
title: "help installing nv driver from terminal"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by klein de usa on 2008-09-09
hi
how do i find out the newest nvidia driver and download it and install it?
i tryed wget [http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg.1run](http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg.1run)
but i'm getting a 404 error 
=> NVIDIA-Linux-x86-169.09-pkg.1run
how would you find out what ver. driver is on that server?

im using a terminal, from the alternat install cd!

---

### Post by mahy on 2008-09-09
I'm not sure  if I understand you correctly, but why can't you do the normal installation, and install newer nv driver afterwards, when the system is up and running? That'd seem much more logical to me...

---

### Post by kpkeerthi on 2008-09-09
Enable Universe and mulitverse repositories from System -> Admin -> Software Sources.

Go to System -> Admin -> Hardware Drivers and enable the nvidia driver.

---

### Post by handydan918 on 2008-09-09
> **kpkeerthi said:**
> Enable Universe and mulitverse repositories from System -> Admin -> Software Sources.

Go to System -> Admin -> Hardware Drivers and enable the nvidia driver.


OP says he's using a terminal.

I agree with the other post above, why not install the nv driver later?

If you have to install the nv driver now, you may need to use another machine to find the URL of the driver you need. You don't state what exactly is your video card, so I can't be sure what driver you need, but if you will give us that info, I bet someone can help you out.

```
lspci | grep -i vga
```

---

### Post by graben3 on 2008-09-09
First of all the v 169 dot someting of the nVidia driver is installable through Envy and this method is by far the simplest when you can go into a graphical mode !

Second. What prevents you to just login in a console but not on the alternate CD ?

Third. Here is the link I followed to install my driver (it was not supported by Envy since Im using a beta driver for a too new card : nvidia gtx260)

This links works :
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=)

But you still have to find the right driver for your hardware and download it yourself from the nvidia website !

---

### Post by klein de usa on 2008-09-09
hi
geforce 6200 
nv44a rev.a1 

install goes to black screen right after orange bar fills up, does this after  alternat install and also if you boot from live cd  ubuntu 8.04.01

i found the ver for 8.04 Hardy Heron ==  169.12 
and adjusted my http but it gave me the same error 404 not found

---

### Post by bodhi.zazen on 2008-09-09
The nvidia drivers are a little confusing ....

First there are the open source options ~ nvidia-glx (and for newer cards nvidia-glx-new). You install these with apt-get :

```
sudo apt-get install nvidia-glx nvidia-settings
```

Then reboot.

Then there are the nvidia drivers. You can install them with envy :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can use envy from X if you like.

Last you can compile the nvidia drivers yourself, which means download the driver, drop out of X and run the script:

```
sudo chmod u+x Nvidia*.run
sudo sh ./NVIDIA*.run
```

before you can compile you need to install build-essential and the kernel headers.

```
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```

Which of these otions do you want help with ?

---

### Post by klein de usa on 2008-09-09
hi
handydan918
graben3
thank you  the link graben3 posted gave me what i needed:

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/NVIDIA-Linux-x86-173.14.12-pkg1.run)

im going to try it out now

---

### Post by andy_blah on 2008-09-09
Maybe you should try Envy?

```
sudo apt-get install envyng-gtk
```

---

### Post by klein de usa on 2008-09-09
hi
thanks all for the help 

this problem is fixed in a rather crazy way, i ended up booting from the alternate cd and starting a terminal, typed in 
code:
```
sudo apt-get install nvidia-glx nvidia-settings
```

rebooted and copied my xorg.conf file from 7.10 into 8.04.01 
had to stop the failsafe from rewriting my xorg file 
rebooted computer and ubuntu 8.04.01 booted right up.

running sudo dpkg-reconfigure xserver-xorg didn't work it reconfigured my keyboard and that was it, it no longer ask's about the video card or pci address or monitor. as far as i can tell

---

### Post by bodhi.zazen on 2008-09-09
Use nvidia-settings to set your monitor :

```
gksu nvidia-settings
```

If you like the changes, click the "save" button, otherwise re-start X (ctrl-alt-backspace) and they will revert.

---

### Post by handydan918 on 2008-09-10
> **klein de usa said:**
> hi
thanks all for the help 

this problem is fixed in a rather crazy way, i ended up booting from the alternate cd and starting a terminal, typed in 
code:
```
sudo apt-get install nvidia-glx nvidia-settings
```

rebooted and copied my xorg.conf file from 7.10 into 8.04.01 
had to stop the failsafe from rewriting my xorg file 
rebooted computer and ubuntu 8.04.01 booted right up.

running sudo dpkg-reconfigure xserver-xorg didn't work it reconfigured my keyboard and that was it, it no longer ask's about the video card or pci address or monitor. as far as i can tell

Nicely done. Good problem solving.

---

### Post by Bucky Ball on 2008-09-10
```
sudo apt-get install nvidia-glx nvidia-settings
```Nice one. You can go one better and try:

[B]sudo nvidia-glx-new

[/B]ps: handydan, lol, love that profile pic! Accurate here! I want a real sticker for my desktop ...:-?

---

### Post by magump on 2008-09-10
I used ENVY to install my NVidia driver.  It can be found at:[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Just follow the directions from the website.  It sets up the card and monitor.  Lots of Luck!

---

