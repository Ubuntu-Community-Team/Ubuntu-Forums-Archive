---
title: "HOW TO: (K)Ubuntu and TabletPC's"
date: 2006-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by rianquinn on 2006-03-29
Before I get started I would like to say that Kubuntu Flight 5 is the first linux distro to actually make me feel at home with my laptop (which is of course a convertable PC). Kubuntu Flight 5 does everything from automatic wireless, and wired lan detection to Plug - n- Play usb devices. Also, I take no responsibility for anything that might happen to your TablePC, or PC.

Ok lets get started here. First things first, how do you get Linux on a TabletPC. Almost "ALL" TabletPC's today DO NOT come with a CD-ROM. If you have a Lenovo x41, this isn't a problem for you because the x41 boots from USB devices. However if you are like me, and own a Toshiba (who probably left out bootable USB devices from the bios to make more money) you have a HUGE problem. Here are a list of options you have:

    - Buy Toshiba's CD-ROM (which somehow is the only CD-ROM you can boot from, currently running at $200)
    - Buy Toshiba's floppy device
    - Boot from an SD-card (Secure Digital)
    - Take out harddrive and install on another machine (preferred method)
    - Network Boot

And here is a list of things that you CANNOT do:

    - Boot an entire OS from the SD-card (no matter how big the SD-card is, you can only put a floppy image on the device)
    - USB Key (no USB devices of any kind)

Why use the harddrive method? Because its cheap and easy. Most new PC's have a plate you can take off to get to the harddrive. From there all you need to do is remove the hardrives from your PC and install your laptop harddrive with  a 2.5" to 3.5" (IDE) converter. This can be found at any computer supply store for a few dollars (mine is realy nice and only cost 6$. NOTE: The converter uses 40 pins, and your PC will most likely only use 39 pins. So you might need to purchase a 40 pin IDE cable, 3$). Hopefully you have a spare computer you can do this with. Otherwise I suggest forking out the money for your TabletPC's version of the CD-ROM. The network boot, and SD-card boot are simply impossible to get working correctly. 

From there you simply install (K)Ubuntu as usual. NOTE: One problem will occur with this method.  (K)Ubuntu will only setup the network devices for your PC, not you TabletPC, so some work might be required later. When the install is finished simply put your harddrive back into your computer. 

After I followed these steps I was greeted by a nice, working Kubuntu install. NOTE: From here everything will be done in Kubuntu. So, what didn't work. 

    - Wacom Support
    - Wireless
    - Jouranl Program (Note Taking)
    - Power and CPU Scaling (Explains why batteries last longer in Windows.)
    - XOrg (screen size was all messed up)

**[COLOR="Green"]XOrg configuration:[/COLOR]**
The xorg.conf file was configured for your PC, not your laptop. If you have a Flat Panel monitor, you will need to change your monitor section. Remove the DPRM support, and replace with

```

HorizSync 31.5 - 63.4
VertRefresh 50 - 100 

```

Other changes might be needed if you have different video cards in your PC and TabletPC. I would use VESA to get things going, and then worry about NVIDIA, and ATI support later.

[COLOR="Green"]
**Wacom Support:**[/COLOR]
Flight 5 uses XOrg ver. 7, and XOrg deprecated its wacom support. So instead you need to get the driver from LinuxWacom Project. To do this, download the source from the LinuxWacom Project's sourceforge webpage. Extract, and look inside the pre-built directory. This is where the driver exists. (NOTE: you don't need to compile linux wacom.) Put the wacom_drv.so into your /usr/lib/xorg/modules/input folder. Next you need to configure your xorg.conf file.

Make the following additions:
```

Section "InputDevice"
     Driver        "wacom"
     Identifier    "cursor"
     Option        "Device"             "/dev/ttyS0"
     Option        "ForceDevice"        "ISDV4"
     Option        "AlwaysCore"         "on"
     Option        "Type"               "cursor"
     Option        "Mode"               "absolute"
     Option        "Speed"              "3.0"
     Option        "Threshold"          "2"
EndSection

Section "InputDevice"
     Driver        "wacom"
     Identifier    "stylus"
     Option        "Device"             "/dev/ttyS0"
     Option        "ForceDevice"        "ISDV4"
     Option        "Type"               "stylus"
     Option        "Mode"               "absolute"
     Option        "Threshold"          "2"
EndSection

Section "InputDevice"
     Driver        "wacom"
     Identifier    "eraser"
     Option        "Device"             "/dev/ttyS0"
     Option        "ForceDevice"        "ISDV4"
     Option        "Type"               "eraser"
     Option        "Mode"               "absolute"
     Option        "Threshold"          "2"
EndSection

# Layouts
Section "ServerLayout"
        Identifier        "Default Layout"
        Screen           "Default Screen"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection


```

The only thing that you might need to change is the /dev/ttyS0 line. This is the serial deivce your Wacom is connected to. Its important that you get this right. To find out which one you have you can apt-get wacom_tools, and run wacdump. Keep testing all of your serial devices until you find the right one. Then change this line for cursor, styles, and eraser. 

To enable your serial device you need to install setserial, and create the following file: /etc/serial.conf

And this to the file:

```

/dev/ttyS0 port 0x338 irq 4 autoconfig

```

And once again make sure you have the correct serial port.

And thats it fokes. Your should now have wacom support. If you have a USB Tablet, you might need to change your xorg.conf a little more. I know the USB Tablets need a few extra lines than I supplied. 

[COLOR="green"]**Networking**[/COLOR]
Before you get going, pray you don't have a wireless device with a Broadcom chipset. If you do, you are in for a wild ride. There are more threads on this site than I can count. I personnaly couldn't get mine working in Ubuntu but was a breeze to setup in Gentoo. However, my TabletPC has an Intel IEEE wireless card built in, and Kubuntu can configure it for you. Heres what you have to do. Record the output form ifconfig. All you need is the number of eth's you have. I have:

eth0, eth1, eth2, and eth3.

Then open your /etc/netwroking/interfaces file, and duplicate the following:

```

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

for each eth you have. Then reboot and your done. Any other wireless devices you have that doesn't have built in kernel support, you will need to do extra research on. However, NDiswrapper, is where you should start.

[COLOR="green"]**Journal Program**[/COLOR]
Xournal is the best I have seen. I like it a lot. Download the source, and compile. You will need, a compiler, automake, make, and several libraries. All of which are on Xournals site. Once you have everything Xournal needs (look at the installation notes on the Xournal site), run the auto-gen script and you are on your way. Maybe someone can create a debian package for Xouranl. 

[COLOR="green"]**Power and CPU Scaling**[/COLOR]
Simply apt-get kpowersave. Its amazing. It will even enable you to suspend to disk. Something I miss about Windows. (Of course not anymore since I have kpowersave). 

Well, thats it, you should have a working TabletPC. If you think I left anything out let me know. I can always amend this HOW TO. Also, might be nice if everyone added there thoughts.

One Last thing. If you are looking for a handwritting recognition and on-screen keyboard like Windows has. I will spare you some time. There is none. I heard that KDE4 will have an on-screen keyboard, but still no word about the handwritting recognition. Maybe one of us can make it ourselves :).

---

### Post by anasofiapaixao on 2006-07-28
Just two things to add: first (and stupid) you can always run setserial ttyS'n' and check which one gives a '0x338' output - in my case it was ttyS4 - and then replace ttyS0 with it in every wacom section of xorg.conf.

Second (even more stupid), GOK (Gnome on-screen keybord), even though uncomparable to the windows one, may do the trick sometimes. BUT do NOT try to type like  more than 1.33/2 keys per second or something really bad will happen to your text. I even prefer to go to the keyboard than to GOK... *cries*. GOK is pre-installed with (no K)Ubuntu, but anyway apt-get and a launcher with the simple command "gok" will do the trick.


An extra thing: nowadays toshiba PCs do have booting from anything you plug to them (haven't tested removable drives tho) if hitting F12 on startup. You get a nifty menu with pics and just select. But it's not like they stopped being bitchy: you get a "recovery" DVD that a) only works with THAT toshiba model, b) hasn't even a windows setup; it's a plain stupid ghost image file with TONS of pre-installed bullshit I don't need clutteling my system tray which if I want to unpack I need to c) run a stupid toshiba app that will ERASE YOUR ENTIRE HDD with one pass of zeros (so do not dream of partition recovery).

I love and hate toshiba at the same time. You know when you are with a guy that is perfect in almost anything but likes to play with your feelings? It's about that.

---

### Post by Henrik on 2006-08-02
Try SOK instead of GOK: [https://wiki.ubuntu.com/Accessibility/Projects/SOK](https://wiki.ubuntu.com/Accessibility/Projects/SOK) 

It should work with tablets.

---

### Post by anasofiapaixao on 2006-08-12
**EDIT 2:** Found SOK [here]("https://wiki.ubuntu.com/Accessibility/Projects/SOK/definitions").


**EDIT:** I still can't find it. The [link on this page]("https://wiki.ubuntu.com/Accessibility/Projects/SOK/dev") is broken... Since I first heard of SOK I've been searching like crazy and still haven't found the download.


I have been acompaining all the talk about SOK and I've been dying to try, but there's only one thing that has kept me from doing it until now: I couldn't find the download!! So I thought it hadn't been publicly released yet. Now how stupid is that. Thankfully I just bumped into the link. It must sound surreal.

I'll try it right away!

---

