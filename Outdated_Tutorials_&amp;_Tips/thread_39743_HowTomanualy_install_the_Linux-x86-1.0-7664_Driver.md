---
title: "HowTo:manualy install the Linux-x86-1.0-7664 Driver from Nvidia"
date: 2005-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by codejunkie on 2005-06-06
This is assuming that you have already installed the nvidia drivers via synaptic and it's working correctly on your ubuntu system and you just want to upgrade to the latest drivers from [www.nvidia.com](www.nvidia.com) if there not already in the repositories.

1: Change "nvidia" back to "nv" in /etc/X11/xorg.conf restart x 
2: Now through synaptic remove packages nvidia-glx nvidia-settings and linux-restricted-modules for  your kernel.
3: Now through synaptic install the build-essential and the linux-headers packages for your kernel.
4: Now download the nvidia driver NVIDIA-Linux-x86-1.0-7664-pkg1.run from [www.nvidia.com](www.nvidia.com) and place it In your home directory. 
5: Hit ctrl+alt+F1 and log in as root with sudo su 
6: Now cd to the directory where the nvidia installer is located.
7: Run telinit 3 and killall gdm
8: Run the nvdia installer with sh NVIDIA-Linux-x86-1.0-7664-pkg1.run once the installer has finished.
9: Change "nv" back to "nvidia" in you /etc/X11/xorg.conf with nano /etc/X11/xorg.conf reboot and you should be using the latest nvidia driver. 

note this was installed on ubuntu Hoary i386 running the 2.6.10-5-k7 kernel and i have no idea if it will work with other kernels or platforms because i haven't tried it.
i hope this helps someone and please don't hate me if this doesn't work on your system any feedback is gladly appreicated.

---

### Post by oddabe19 on 2005-06-06
[QUOTE=codejunkie]This is assuming that you have already installed the nvidia drivers via synaptic and it's working correctly on your ubuntu system and you just want to upgrade to the latest drivers from [www.nvidia.com](www.nvidia.com) if there not already in the repositories.

1: Change "nvidia" back to "nv" in /etc/X11/xorg.conf restart x 
2: Now through synaptic remove packages nvidia-glx nvidia-settings and linux-restricted-modules for  your kernel.
3: Now through synaptic install the build-essential and the linux-headers packages for your kernel.
4: Now download the nvidia driver NVIDIA-Linux-x86-1.0-7664-pkg1.run from [www.nvidia.com](www.nvidia.com) and place it In your home directory. 
5: Hit ctrl+alt+F1 and log in as root with sudo su 
6: Now cd to the directory where the nvidia installer is located.
7: Run telinit 3 and killall gdm
8: Run the nvdia installer with sh NVIDIA-Linux-x86-1.0-7664-pkg1.run once the installer has finished.
9: Change "nv" back to "nvidia" in you /etc/X11/xorg.conf with nano /etc/X11/xorg.conf reboot and you should be using the latest nvidia driver. 

note this was installed on ubuntu Hoary i386 running the 2.6.10-5-k7 kernel and i have no idea if it will work with other kernels or platforms because i haven't tried it.
i hope this helps someone and please don't hate me if this doesn't work on your system any feedback is gladly appreicated.[/QUOTE]
 very good, except a few unnesessary things...
1. it's much easier (because the headers have a hard time of showing up in synaptic) of doing 
```
sudo apt-get install linux-headers-`uname -r`
```
2. You do NOT have to change nvidia to nv before installing.
3. You don't have to telinit 3 or kill gdm. All you need to do is
```
sudo /etc/init.d/gdm stop
``` after the installer is done and the driver is installed all you need to do is ```
sudo /etc/init.d/gdm start
```

make sure in your xorg.conf under modules you remove Load GLcore and Load DRI. You should have to add Load glx.

---

### Post by codejunkie on 2005-06-06
[QUOTE=oddabe19]very good, except a few unnesessary things...
1. it's much easier (because the headers have a hard time of showing up in synaptic) of doing 
```
sudo apt-get install linux-headers-`uname -r`
```
2. You do NOT have to change nvidia to nv before installing.
3. You don't have to telinit 3 or kill gdm. All you need to do is
```
sudo /etc/init.d/gdm stop
``` after the installer is done and the driver is installed all you need to do is ```
sudo /etc/init.d/gdm start
```

make sure in your xorg.conf under modules you remove Load GLcore and Load DRI. You should have to add Load glx.[/QUOTE]

thanks for the nice feedback and great tips on the howto i might add these tips to the howto later if you don't mind.

---

### Post by mentalinc on 2005-06-14
so many problems with AMD64 hoary

gives errors during install about library installs

then when you try at glxgears it gives an error message

also during install it gives change_page_attr error
tells me to update to 2.6.11 or newer
but hoary only 2.6.10-5

also suggests i look at the readme Appendix N known issues

except i cant download the readme from the nvidia page - gives me an error message

---

### Post by codejunkie on 2005-06-15
[QUOTE=mentalinc]so many problems with AMD64 hoary

gives errors during install about library installs

then when you try at glxgears it gives an error message

also during install it gives change_page_attr error
tells me to update to 2.6.11 or newer
but hoary only 2.6.10-5

also suggests i look at the readme Appendix N known issues

except i cant download the readme from the nvidia page - gives me an error message[/QUOTE]

this is the 32bit nvidia driver for i386 pc's if your trying to install this driver  on AMD64 it might give you errors if you have the AMD64 you need to download and install the 64bit driver from nvidia [http://www.nvidia.com/object/linux_display_amd64_1.0-7664.html](http://www.nvidia.com/object/linux_display_amd64_1.0-7664.html) hope this helps.

---

### Post by mentalinc on 2005-06-15
yeah i have the 64bit version i thought that the steps to install would be the same.
if they are then the drivers do not work with a clean install hoary

---

### Post by cutOff on 2005-06-15
I think the steps are the same but you should choose appropriate drivers for your architecture.

I advise you to look codejunkie's post.

---

### Post by codejunkie on 2005-06-15
[QUOTE=cutOff]I think the steps are the same but you should choose appropriate drivers for your architecture.

I advise you to look codejunkie's post.[/QUOTE]

yep the steps should be the same you just need the correct driver for your architecture and the appropriate linux-headers packages for your kernel version.

it should work on AMD64 but i haven't tested it because i don't have a 64bit processor.

---

### Post by kleeman on 2005-06-16
Just a word of warning based on an unpleasant experience  :roll: I followed this howto and everything seemed to be working fine (3d games etc etc) until I rebooted and then everything involving 3d acceleration segfaulted. Reinstalled the drivers according to the howto and it started working again  :roll: HOWEVER I noticed that the kernel module was generating a bunch of error messages concerning cache aliasing (I am using the 686-smp kernel btw). Upon reboot X failed altogether and further reboots revealed what looked like file corruption. I tried uninstalling and reinstalling the old hoary drivers but no dice. Net result a painful reinstall. Beware YMMV!

---

### Post by rosslaird on 2005-06-16
Another caution:

Some people have experienced a serious issue with this driver: a black screen and no X session. (There's a long post over at the the nvidia forums about it).

I myself had this problem after upgrade, and as a result I have resturned to the previous version.

Your mileage may vary.

Ross

---

### Post by Lunde on 2005-06-16
WARNING! Serious issues with these drivers and 2.6.10-5 kernel

First boot: everything worls fine the first 2min, then the glxgear frames pr seconds drop to 70 fps. 

Second boot: second boot, no OpenGL, no nvidia-settings but at least I get X started.

third reboot: No more X, reinstallation of driver needed to start x

I was very entusiastic and I really liked these drivers for 2min.

---

### Post by Omnios on 2005-06-16
???? Could that be a problem in xorg config (havent installed driver yet just researching) but had a similar problem with nv and nvidia where nvidia didnt show or wasnt chosen. If the official driver showes as nvidia shouldnt be a prob but if its different it just might be a glitch. This was solved by adding show "nvidia" to the config.

---

### Post by rosslaird on 2005-06-16
Nobody seems to be really sure what's causing these problems.
Various solutions have worked for various people, but not universally.
Here's the "black screen" post from the Nvidia forums:

[Black screen](http://www.nvnews.net/vbulletin/showthread.php?t=50254&page=1&pp=15)

---

### Post by irusun on 2005-06-18
This thread helped me get my GF6200 up and running - thanks!  The new 7664 driver works great for the card I have.

To make it easy for myself for future driver upgrades, I wrote a really simple script using the steps outlined in the first couple of posts.  I figured someone else might find it useful as well, so I've included it in this post.

It's extremely simple - no error handling or anything like that.  It will remove and install the appropriate packages, ask for the driver version to download (e.g. 7664), download the driver and install it.

You should look the script over before using it - I'm not a developer and can't be held responsible for whether it works or renders your computer completely useless.  Any feedback is welcome - or feel free to modify it and post an improved version.

---

### Post by moment on 2005-06-18
The latest driver crashes my X while switching to text (Ctrl+F1) and I have problem with DPMS. I have a Geforce FX Go5200. I switched back to 7174

---

### Post by Boggles3 on 2005-07-18
yes there is some crazy problem i know with the 64 gforce drivers hen you try to get the latest ones..
xserver failures everywhere...lol i reinstalled ubuntu exept this time i did 32 bit.. i have a dual xeon machine but i dont feel like dealing with the 64 bit crap .. 
i may switch back in the future when more kinks are worked out of 64 bit technology in general ..

   never could get the 7667 drivers to work with 64 and now i leary to try it here in 32 just cuz it was a bad experience.. but im sure il muster the guts to try again soon lol :) 

ill have to remember this post cuz it was a good clean how to \\:D/

---

### Post by tseliot on 2005-07-19
Hi guys, I compiled my kernel by myself as I needed kernel 2.6.12. The question is: how can I compile either the headers  or the modules required to install Nvidia drivers? (I'm using Ubuntu 64)

Thanks in advance

---

### Post by codejunkie on 2005-07-19
[QUOTE=tseliot]Hi guys, I compiled my kernel by myself as I needed kernel 2.6.12. The question is: how can I compile either the headers  or the modules required to install Nvidia drivers? (I'm using Ubuntu 64)

Thanks in advance[/QUOTE]
if you used kpkg example:
```

sudo make-kpkg --append-to-version=-custom kernel_image modules_image

``` to build your kernel you can just cd /usr/src/linux and run this command to build the headers like so
```

sudo make-kpkg --append-to-version=-custom kernel_headers

```
the .deb for the headers package will be made in the same place your new kernel was.
if you manually built the kernel and just linked to the kernel you can just point the nvidia installer to the /usr/src/linux dir i can't remember the exact command but it's in the readme.txt file on nvidia's website hope this helps.
Edit: i believe the command is --add-this-kernel so it would be something like this 
```
sh NVIDIA-Linux-x86_64-1.0-7667-pkg1.run --add-this-kernel
```
this will build a custom nvidia installer with support your kernel compiled in then just install it, very useful if you have to reinstall again and don't want to go through the steps again.
or 
```
sh NVIDIA-Linux-x86_64-1.0-7667-pkg1.run --kernel-source-path=/usr/src/linux
``` will install the driver only.

---

### Post by rwabel on 2005-07-19
how can it get uninstalled, in th case of getting back to the ubuntu binary nvidia drivers?

edited: is it sufficiant to ```
sudo nvidia-installer --uninstall
```  and reinstall the ubuntu nvidia stuff?

---

### Post by codejunkie on 2005-07-19
[QUOTE=rwabel]how can it get uninstalled, in th case of getting back to the ubuntu binary nvidia drivers?

edited: is it sufficiant to ```
sudo nvidia-installer --uninstall
```  and reinstall the ubuntu nvidia stuff?[/QUOTE]
yep that should work then reinstall the ubuntu nvidia drivers.

---

### Post by tseliot on 2005-07-29
There's an error when I accept to install ia32 OpenGL compatibility libraries (I have an AMD64)

ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
       (expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
       '/usr/lib32/libGL.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and third-party graphics driver packages.

How could this be solved?

UPDATE: I've solved my problem, all the instructions are available in my HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=52924](http://www.ubuntuforums.org/showthread.php?t=52924)

---

### Post by tseliot on 2005-08-01
[QUOTE=tseliot]There's an error when I accept to install ia32 OpenGL compatibility libraries (I have an AMD64)

ERROR: The runtime configuration check failed for library 'libGL.so.1.0.7667'
       (expected: '/emul/ia32-linux/usr/lib/libGL.so.1', found:
       '/usr/lib32/libGL.so.1').  The most likely reason for this is that
       conflicting OpenGL libraries are installed in a location not inspected
       by `nvidia-installer`.  Please be sure you have uninstalled any
       third-party OpenGL and third-party graphics driver packages.

How could this be solved?
[/QUOTE]

(I have an AMD64 and I'm using the 64bit nvidia installer)
Well, the problem hasn't been totally solved. The  computer freezes (completely) randomly. Is there a way to install OpenGL 32bit compatibility libraries?

for my xorg you can look here:
[http://ubuntuforums.org/showthread.php?t=53506&page=1](http://ubuntuforums.org/showthread.php?t=53506&page=1)

---

