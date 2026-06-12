---
title: "Unable to install Geforce 8800 GT drivers"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-07-02
Hey,

Just purchased an Nvidia Geforce 8800 GT 512 Mb video card. 

After installing the video card on the motherboard, I turned the pc on, but the X server and gnome didn't load. After a few restarts, they did, but the graphics were terrible.

So, I went to nvidia's site and downloaded the linux driver for Geforce 8800:

[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)

> Linux Display Driver - x86

Version: 173.14.09
Operating System: Linux x86
Release Date: June 11, 2008

Release Highlights

    * Fixed aliased font rendering corruption on X.Org server 1.5.
    * Fixed a display corruption problem driving two dual-link DFPs with Quadro FX 1700 GPUs.
    * Fixed a regression that prevented the X driver from starting on some GeForce FX, 6 and 7 mobile GPUs.
    * Fixed a locale-interaction issue in the nvidia-settings X server configuration file parser.
    * Added preliminary support for Linux 2.6.26.

during the installation, i was asked to shut off the x server, which i did. Then the installation went on, and it was successful, supposedly.

So, I rebooted, but got the same terrible graphics. It wouldn't start normally of course, I had to reboot a few times before loading the x server. 

I then uninstalled that driver and tried a few others through synaptic, i tried the following:

- nvidia-glx
- nvidia-glx-envy
- nvidia-glx-legacy
- nvidia-glx-legacy-envy
- nvidia-glx-new

They all didn't work, and by that i mean: after installing them, the x server wouldn't loand normally and when it does, the graphics are just terrible.

However, the only one in synaptic that worked was:
nvidia-glx-new-envy (which i am currently using)

after installing and rebooting, the login screen loaded properly and without any problems. However, the resolution was huge, which i adjusted once i was on the desktop. BUT, I have two problems:

1. whenever I logout or reboot the computer and get to the login screen, the resolution becomes huge, once i login, it goes back to normal. How can I make the login screen resolution normal?

2. Though this is the same resolution that I used before installing the geforce 8800 card, there is something strange about it. The text seems a bit fuzzy/blurry? I played around with OS font options, but to no avail. Any ideas?


If you have any answers or suggestions, feel free to post please. If you want to walk me through installing the nvidia driver, I can do that. If you want any system output, i can produce that as well.

Note: I ran glxgears and got this:

```
ali@ali-desktop:~$ glxgears
Error: API mismatch: the NVIDIA kernel module has version 173.14.05,
but this NVIDIA driver component has version 173.14.09.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
45774 frames in 5.0 seconds = 9152.294 FPS
45980 frames in 5.0 seconds = 9193.606 FPS
46647 frames in 5.0 seconds = 9327.204 FPS
46513 frames in 5.0 seconds = 9301.807 FPS
46966 frames in 5.0 seconds = 9384.769 FPS
46973 frames in 5.0 seconds = 9392.679 FPS
47125 frames in 5.0 seconds = 9423.569 FPS
46448 frames in 5.0 seconds = 9284.985 FPS
47213 frames in 5.0 seconds = 9442.070 FPS
46607 frames in 5.0 seconds = 9317.146 FPS
47013 frames in 5.0 seconds = 9401.481 FPS
47066 frames in 5.0 seconds = 9410.462 FPS
46353 frames in 5.0 seconds = 9269.297 FPS
^X
ali@ali-desktop:~$ 
```

---

### Post by Hobo Joe on 2008-07-03
Use Envy to install your drivers. It'll make things a lot easier.

```

sudo aptitude install envyng

```

Once it's installed, just run it from Applications > System Tools > Envy, or the command 'envyng'. Uninstall the nVidia driver first, to clean things up, then install the latest one and reboot.

Everything should work after that, good luck!

---

### Post by Victormd on 2008-07-03
+1
Envy-NG will make your life much easier!

---

### Post by stchman on 2008-07-03
> **newbuntuxx said:**
> Hey,

Just purchased an Nvidia Geforce 8800 GT 512 Mb video card. 

After installing the video card on the motherboard, I turned the pc on, but the X server and gnome didn't load. After a few restarts, they did, but the graphics were terrible.

So, I went to nvidia's site and downloaded the linux driver for Geforce 8800:

[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)



during the installation, i was asked to shut off the x server, which i did. Then the installation went on, and it was successful, supposedly.

So, I rebooted, but got the same terrible graphics. It wouldn't start normally of course, I had to reboot a few times before loading the x server. 

I then uninstalled that driver and tried a few others through synaptic, i tried the following:

- nvidia-glx
- nvidia-glx-envy
- nvidia-glx-legacy
- nvidia-glx-legacy-envy
- nvidia-glx-new

They all didn't work, and by that i mean: after installing them, the x server wouldn't loand normally and when it does, the graphics are just terrible.

However, the only one in synaptic that worked was:
nvidia-glx-new-envy (which i am currently using)

after installing and rebooting, the login screen loaded properly and without any problems. However, the resolution was huge, which i adjusted once i was on the desktop. BUT, I have two problems:

1. whenever I logout or reboot the computer and get to the login screen, the resolution becomes huge, once i login, it goes back to normal. How can I make the login screen resolution normal?

2. Though this is the same resolution that I used before installing the geforce 8800 card, there is something strange about it. The text seems a bit fuzzy/blurry? I played around with OS font options, but to no avail. Any ideas?


If you have any answers or suggestions, feel free to post please. If you want to walk me through installing the nvidia driver, I can do that. If you want any system output, i can produce that as well.

Note: I ran glxgears and got this:

```
ali@ali-desktop:~$ glxgears
Error: API mismatch: the NVIDIA kernel module has version 173.14.05,
but this NVIDIA driver component has version 173.14.09.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
45774 frames in 5.0 seconds = 9152.294 FPS
45980 frames in 5.0 seconds = 9193.606 FPS
46647 frames in 5.0 seconds = 9327.204 FPS
46513 frames in 5.0 seconds = 9301.807 FPS
46966 frames in 5.0 seconds = 9384.769 FPS
46973 frames in 5.0 seconds = 9392.679 FPS
47125 frames in 5.0 seconds = 9423.569 FPS
46448 frames in 5.0 seconds = 9284.985 FPS
47213 frames in 5.0 seconds = 9442.070 FPS
46607 frames in 5.0 seconds = 9317.146 FPS
47013 frames in 5.0 seconds = 9401.481 FPS
47066 frames in 5.0 seconds = 9410.462 FPS
46353 frames in 5.0 seconds = 9269.297 FPS
^X
ali@ali-desktop:~$ 
```

If you are running Hardy then nvidia-glx-new is the proper driver.

Gutsy and earlier you need Envy 0.9.10.

---

### Post by Cresho on 2008-07-03
well!  I want to put in my 2 cents in.  YOu probably basterdized your drivers.  In hardy heron, after a fresh install, all you need to do is go into Administration->Hardware Drivers, and run that.  It installs and automatically cofigures x for you.  Reboot and then your good to go.

i get 13105.fps with glxgears with compiz-fusion on and 27000 fps without compiz.

I am using a bfg 8800gt with a modified thermaltake fan for 40 degree celsius temp performance.

I just want to point out that the default hardware drivers from hardy heron is more than enough to make your card work.  If you want extra, in terminal type

sudo apt-get install nvidia-settings and you get the extra stuff for config.  if you run compiz fusion, you may need to follow my directions in correct configuration for smooth 200fps look!

[http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing)

---

### Post by aktiwers on 2008-07-03
Manual install is really not that hard either. I made a small guide here:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Its a bit outdated, so I will update it below to fit your needs:

Install needed tools and libs:
```
sudo aptitude install libc6 libc6-dev
``````
sudo aptitude install build-essential linux-headers-$(uname -r);
```Go here and download the latest driver:[URL="http://www.nvidia.com/object/linux_display_ia32_169.07.html"]
[/URL][http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)
(here is the main link [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html))

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1
Log in
 
Full terminal mode. Start by going to Desktop:
```
cd Desktop
```Then stop gdm (the installer requires this):```
sudo /etc/init.d/gdm stop
```Give the installer rights to be executed:```
sudo chmod +x NVIDIA-Linux-x86-96.43.05-pkg1.run
```And then execute/run the installer:
```
sudo ./NVIDIA-Linux-x86-96.43.05-pkg1.run
```After that reboot
```
sudo reboot
```Done!

---

### Post by newbuntuxx on 2008-07-03
> **Hobo Joe said:**
> Use Envy to install your drivers. It'll make things a lot easier.

```

sudo aptitude install envyng

```

Once it's installed, just run it from Applications > System Tools > Envy, or the command 'envyng'. Uninstall the nVidia driver first, to clean things up, then install the latest one and reboot.

Everything should work after that, good luck!

> **Victormd said:**
> +1
Envy-NG will make your life much easier!


Hey guys,

I downloaded envy and installed it. I then ran it and selected the automatic hardware detection which installs this driver: 173.14.05 (ie. nvidia-glx-new-envy), which I already had. So, that didn't make a difference.

Then I uninstalled (nvidia-glx-new-envy) and ran envy but this time, i choose the manual option. I selected: 96.43.05. That didn't work. So, i removed it and tried: 71.86.04. And that didn't work. 

Then, i went back and selected the automatic hardware detection option. nvidia-glx-new-envy was installed again. But i still get the same problem: the resolution at the login screen is huge, once i login, it changes to normal.

So, any additional suggestions or tips?

---

### Post by newbuntuxx on 2008-07-03
> **Cresho said:**
> well!  I want to put in my 2 cents in.  YOu probably basterdized your drivers.  In hardy heron, after a fresh install, all you need to do is go into Administration->Hardware Drivers, and run that.  It installs and automatically cofigures x for you.  Reboot and then your good to go.

i get 13105.fps with glxgears with compiz-fusion on and 27000 fps without compiz.

I am using a bfg 8800gt with a modified thermaltake fan for 40 degree celsius temp performance.

I just want to point out that the default hardware drivers from hardy heron is more than enough to make your card work.  If you want extra, in terminal type

sudo apt-get install nvidia-settings and you get the extra stuff for config.  if you run compiz fusion, you may need to follow my directions in correct configuration for smooth 200fps look!

[http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing](http://ubuntuforums.org/showthread.php?t=646356&highlight=antiliasing)

Are you suggesting that I reinstall hardy? Isn't that a bit extreme? like trying to clip your nails by chopping off your arm How can I undo the damage that I have done to the drivers? 

any tips?

---

### Post by newbuntuxx on 2008-07-03
aktiwers, I tried your way. But the following didn't work: 


```
sudo aptitude install libc6 libc6-dev

sudo aptitude install build-essential linux-headers-$(uname -r);
```

When I put the above in terminal i get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done   
```

Nonetheless, i followed the rest of your instructions to the dot, and the driver still didn't work. 

Any other suggestions?

---

### Post by Cresho on 2008-07-04
did you fix your sources on your system?

here is a portion of my notes for new nvidia drivers from the site.

setting up your ubuntu first of all:fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
1. sudo aptitude remove automake1.4
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. grub into recovery mode and hit root. cd into the directory where you downloaded the NVIDIA-Linux-x86-169.09-pkg1.run and sh NVIDIA-Linux-x86-169.09-pkg1.run in terminal. (this one is 32bit version)
4. ignore the question or say no to kernel download during instal and have nvidia xconfig update the x
5. if screen is not proper, continue and once booted, open synaptic package manager and remove nvidia kernel common. then repeat top process if to ensure all is installed again.
6. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
7. reboot and your good to go.

I been using these notes and it never fails.  If you get an error like kernel source or somethuing in that nature that it's not installed, come back and ill tell you which other source to install.

---

### Post by Victormd on 2008-07-04
> **Cresho said:**
> i get 13105.fps with glxgears with compiz-fusion on and 27000 fps without compiz.

How do you get such high fps?
My graphics card is working fine, no problems with it, the driver is properly installed, have the settings set to startup under sessions and compiz is working without a glitch and this is what I get with glxgears:
> 302 frames in 5.0 seconds = 60.270 FPS
300 frames in 5.0 seconds = 59.885 FPS
300 frames in 5.0 seconds = 59.884 FPS
300 frames in 5.0 seconds = 59.887 FPS

WHY???

---

### Post by Cresho on 2008-07-04
I am using the 8800gt oc from bfg (big fu@%$n guns) company!  The best graphics card on the market for the 8800gt series.

---

### Post by Victormd on 2008-07-04
> **Cresho said:**
> I am using the 8800gt oc from bfg (big fu@%$n guns) company!  The best graphics card on the market for the 8800gt series.

I don't really think that has much to do with it. A difference of a few fps I would understand, but 2 orders of magnitude difference... That tells me that there's something wrong with my drivers, the only problem is, there isn't!

I wouldn't say that there's anything wrong with my card because in Windows I get high fps in any game I play with graphics options on full and full res.

---

### Post by newbuntuxx on 2008-07-05
> **Cresho said:**
> did you fix your sources on your system?

here is a portion of my notes for new nvidia drivers from the site.

setting up your ubuntu first of all:fix software sources "Download from" usa to main server. update the resources. It is in Administration->Software Sources. refresh with button on top. Also add third party software and source software sources. in add and remove programs, under show, select "all available applications"
1. sudo aptitude remove automake1.4
2. sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev xserver-xorg-dev
3. grub into recovery mode and hit root. cd into the directory where you downloaded the NVIDIA-Linux-x86-169.09-pkg1.run and sh NVIDIA-Linux-x86-169.09-pkg1.run in terminal. (this one is 32bit version)
4. ignore the question or say no to kernel download during instal and have nvidia xconfig update the x
5. if screen is not proper, continue and once booted, open synaptic package manager and remove nvidia kernel common. then repeat top process if to ensure all is installed again.
6. add startup file to system->preference->sessions "nvidia-settings --load-config-only"
7. reboot and your good to go.

I been using these notes and it never fails.  If you get an error like kernel source or somethuing in that nature that it's not installed, come back and ill tell you which other source to install.

Thanks alot Cresho! Your solution made a huge difference. 

Here is what I was getting after Envy installed the nvidia driver:

without compiz:
```

ali@ali-desktop:~$ glxgears
62901 frames in 5.0 seconds = 12580.120 FPS
62662 frames in 5.0 seconds = 12523.709 FPS
63168 frames in 5.0 seconds = 12633.587 FPS
63082 frames in 5.0 seconds = 12616.392 FPS
61141 frames in 5.0 seconds = 12228.198 FPS
62421 frames in 5.0 seconds = 12484.062 FPS
62027 frames in 5.0 seconds = 12405.256 FPS
62003 frames in 5.0 seconds = 12398.212 FPS
```


with  compiz:

```
ali@ali-desktop:~$ glxgears
41806 frames in 5.0 seconds = 8361.113 FPS
42196 frames in 5.0 seconds = 8437.314 FPS
42235 frames in 5.0 seconds = 8446.992 FPS
42160 frames in 5.0 seconds = 8431.899 FPS
42183 frames in 5.0 seconds = 8436.468 FPS
42249 frames in 5.0 seconds = 8449.792 FPS
42225 frames in 5.0 seconds = 8444.934 FPS
42209 frames in 5.0 seconds = 8441.756 FPS
42174 frames in 5.0 seconds = 8434.658 FPS
42287 frames in 5.0 seconds = 8453.924 FPS

```

And here is what I got after following your instructions:

Without Compiz:

```
ali@ali-desktop:~$ glxgears
87729 frames in 5.0 seconds = 17545.758 FPS
87938 frames in 5.0 seconds = 17587.526 FPS
87986 frames in 5.0 seconds = 17597.186 FPS
87654 frames in 5.0 seconds = 17530.765 FPS
85981 frames in 5.0 seconds = 17196.176 FPS
87661 frames in 5.0 seconds = 17532.074 FPS
87646 frames in 5.0 seconds = 17529.067 FPS
87670 frames in 5.0 seconds = 17533.821 FPS
```

With Compiz:

```
ali@ali-desktop:~$ glxgears
74123 frames in 5.0 seconds = 14823.761 FPS
74920 frames in 5.0 seconds = 14983.859 FPS
74848 frames in 5.0 seconds = 14969.582 FPS
74912 frames in 5.0 seconds = 14982.391 FPS
74851 frames in 5.0 seconds = 14970.125 FPS
74841 frames in 5.0 seconds = 14968.059 FPS
74877 frames in 5.0 seconds = 14975.244 FPS
74915 frames in 5.0 seconds = 14982.943 FPS
74951 frames in 5.0 seconds = 14990.041 FPS
```

The default resolution is much better now, and its not too fuzzy, though I think it can be better. One thing that didn't change though was the resolution at the login screen. I still have the same problem where the resolution is so small that I can only see a quarter of the login box. 

Any solutions to that?

Thanks again Cresho.

---

### Post by Cresho on 2008-07-06
hmmm..just remember, the instructions I gaved you are for advanced users.

IMPORTANT!  if you do an update, and ubuntu has a new kernel installed, then you are out of luck.  you will need to install using the instructions and sometimes it is difficult making heads or tails of which kernel source to use.  In any case, if you have difficulty booting up, when the system boots up, in the grub list, you can use the previous kernel version instead of booting into the new one and you can also edit the "sudo gedit /etc/fstab" list and add # infront of the new kernel so you can use the old one incase you get tired of scrolling down the grub list to boot up to the working kernel with nvidia.

Anyway, im rambling.  your ddc/ci support or the lack of, Nvidia detects your monitor refresh rate and automatically sets correct paramaters.  You can create your own refresh rate to fix this problem but that is another story. I think it's called modline [http://bohne-lang.de/spec/linux/modeline/](http://bohne-lang.de/spec/linux/modeline/) and use those to do a custom entrance in the nvidia-settings.  Of course I have not gone this far but you can totally hose your system and not be able to log back in if your hz is off by a hair.  you would then need to boot at log in gnome safe mode.  just informing and warning you.

what funky monitor are you running if you don't mind me asking? :lolflag:

---

### Post by Cresho on 2008-07-06
sorry, ohh ya, read my previous post ontop of this one.

I just had to post my results

 Re: Showoff Your "glxgears" FPS Under Gutsy Gibbon
73929 frames in 5.0 seconds = 14785.652 FPS
74591 frames in 5.0 seconds = 14918.185 FPS
67298 frames in 5.0 seconds = 13459.454 FPS
66217 frames in 5.0 seconds = 13243.355 FPS
109133 frames in 5.0 seconds = 21826.574 FPS
108724 frames in 5.0 seconds = 21744.669 FPS
105900 frames in 5.0 seconds = 21179.915 FPS
107968 frames in 5.0 seconds = 21593.492 FPS
100842 frames in 5.0 seconds = 20168.339 FPS
107681 frames in 5.0 seconds = 21536.041 FPS
107155 frames in 5.0 seconds = 21430.910 FPS
102861 frames in 5.0 seconds = 20572.183 FPS
106947 frames in 5.0 seconds = 21389.306 FPS
108198 frames in 5.0 seconds = 21639.513 FPS
108671 frames in 5.0 seconds = 21734.113 FPS
104066 frames in 5.0 seconds = 20813.080 FPS
102356 frames in 5.0 seconds = 20471.044 FPS
109265 frames in 5.0 seconds = 21852.886 FPS
109381 frames in 5.0 seconds = 21876.112 FPS
109237 frames in 5.0 seconds = 21847.312 FPS
109586 frames in 5.0 seconds = 21917.042 FPS
108736 frames in 5.0 seconds = 21747.126 FPS
101523 frames in 5.0 seconds = 20304.494 FPS
108558 frames in 5.0 seconds = 21711.474 FPS
109546 frames in 5.0 seconds = 21909.056 FPS
108517 frames in 5.0 seconds = 21703.230 FPS
123550 frames in 5.0 seconds = 24706.902 FPS
123604 frames in 5.0 seconds = 24720.631 FPS
123377 frames in 5.0 seconds = 24675.247 FPS
123683 frames in 5.0 seconds = 24736.516 FPS
123531 frames in 5.0 seconds = 24706.130 FPS
124117 frames in 5.0 seconds = 24823.237 FPS
123758 frames in 5.0 seconds = 24751.575 FPS
123519 frames in 5.0 seconds = 24703.656 FPS
124080 frames in 5.0 seconds = 24815.981 FPS
123819 frames in 5.0 seconds = 24763.735 FPS
123832 frames in 5.0 seconds = 24766.350 FPS
124302 frames in 5.0 seconds = 24860.366 FPS
123927 frames in 5.0 seconds = 24785.400 FPS
124055 frames in 5.0 seconds = 24810.811 FPS
113658 frames in 5.0 seconds = 22731.596 FPS



8800gt

---

### Post by Cresho on 2008-07-06
> **Victormd said:**
> I don't really think that has much to do with it. A difference of a few fps I would understand, but 2 orders of magnitude difference... That tells me that there's something wrong with my drivers, the only problem is, there isn't!

I wouldn't say that there's anything wrong with my card because in Windows I get high fps in any game I play with graphics options on full and full res.

HMMM, I just read your machine spec!  There is something Very wrong.  In anycase, I get around 27000fps in glxgears.

---

### Post by aktiwers on 2008-07-06
remember this is no benchmark test.. so if it runs good and all I would not worry about it

---

### Post by newbuntuxx on 2008-07-09
> **Cresho said:**
> hmmm..just remember, the instructions I gaved you are for advanced users.

IMPORTANT!  if you do an update, and ubuntu has a new kernel installed, then you are out of luck.  you will need to install using the instructions and sometimes it is difficult making heads or tails of which kernel source to use.  In any case, if you have difficulty booting up, when the system boots up, in the grub list, you can use the previous kernel version instead of booting into the new one and you can also edit the "sudo gedit /etc/fstab" list and add # infront of the new kernel so you can use the old one incase you get tired of scrolling down the grub list to boot up to the working kernel with nvidia.

Anyway, im rambling.  your ddc/ci support or the lack of, Nvidia detects your monitor refresh rate and automatically sets correct paramaters.  You can create your own refresh rate to fix this problem but that is another story. I think it's called modline [http://bohne-lang.de/spec/linux/modeline/](http://bohne-lang.de/spec/linux/modeline/) and use those to do a custom entrance in the nvidia-settings.  Of course I have not gone this far but you can totally hose your system and not be able to log back in if your hz is off by a hair.  you would then need to boot at log in gnome safe mode.  just informing and warning you.

what funky monitor are you running if you don't mind me asking? :lolflag:




hey,

I am using SyncMaster 203B, the flat screen one. I bought it last year. Its pretty new.

I just dont understand why it doesn't remember my correct resolution at login screen, and then once i login, it goes back to normal? that just beats me....

---

