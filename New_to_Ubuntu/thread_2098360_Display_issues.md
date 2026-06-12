---
title: "Display issues"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Oweirdone on 2012-12-26
(12.04.1 LTS)

[FONT=Arial][SIZE=1]Need some help:
[/SIZE][/FONT][B][FONT=Arial][SIZE=1] Running Ubuntu, but my laptop screen is broken, so I have a second monitor hooked up.
 
 Problem 1) It displays on this monitor, but not in the right  resolution, and when I try to select resolutions, the one I need isn't  there.
 Problem 2) It doesn't  recognise there is a second monitor, it believes it's displaying on the  laptop screen, which could be why the resolution choices are wrong.
 
 How do I get it to recognise that it's displaying on a separate monitor?[/SIZE][/FONT][/B]

Many thanks,

Owe.

---

### Post by Crossbow on 2012-12-26
I had that first problem last week. I fixed it by installing Nvidia-173 and removing the older Nvidia driver. I downloaded it from the Nvidia website and did the install/remove with Synaptic.

---

### Post by NikTh on 2012-12-26
> **Oweirdone said:**
> (12.04.1 LTS)

[FONT=Arial][SIZE=1]Need some help:
[/SIZE][/FONT][B][FONT=Arial][SIZE=1] Running Ubuntu, but my laptop screen is broken, so I have a second monitor hooked up.
 
 Problem 1) It displays on this monitor, but not in the right  resolution, and when I try to select resolutions, the one I need isn't  there.
 Problem 2) It doesn't  recognise there is a second monitor, it believes it's displaying on the  laptop screen, which could be why the resolution choices are wrong.
 
 How do I get it to recognise that it's displaying on a separate monitor?[/SIZE][/FONT][/B]

Hi ,
please give more info.

What is the graphics card you use ? and what driver you use ? and the connection , is via HDMI or VGA ? 

As for the reference to "Laptop Screen" this is probably a mistake of "System Settings > Displays" do not bother about that. 

Thanks

---

### Post by Oweirdone on 2012-12-26
The laptop is an E-System Sorrento 1. The connection is standard VGA (I believe). It doesn't say what graphics card it uses, rather, unhelpfully, it says, "Integrated" and having searched online I seem unable to find the specifications for the laptop. Possibly becuase it was sold by Curries, who have since gone out of business.

I've ensured that the software is up to date, but without knowing which make of graphics card is i nit, I can't download the relevant divers. 

Having said that, the card is,a s I said, integrated, and the processor is an 'Intel Celeron C900'.

Thanks

Owe.

---

### Post by NikTh on 2012-12-26
Hi ,
can you open a terminal (even in this resolution) and provide the results of below commands ? 

```
lspci -nnk | grep -iA2 vga
sudo lshw -C display
xrandr
```Copy-paste the results back here. 
_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")
 


Thanks

---

### Post by Oweirdone on 2012-12-27
```
jkmcc@jkmcc-Sorrento:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter [1039:6351] (rev 10)
    Subsystem: Elitegroup Computer Systems Device [1019:5057]
jkmcc@jkmcc-Sorrento:~$ sudo lshw -C display
[sudo] password for jkmcc: 
Sorry, try again.
[sudo] password for jkmcc: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:d4000000-d401ffff ioport:9000(size=128)
```

---

### Post by NikTh on 2012-12-27
Oh man !! 

You have this SIS graphics card.. 
Sorry ... I cannot help you with that. 

The only thing I can suggest is to try to upgrade the driver through a PPA.. (maybe) 

You can see the current installed driver with this command 
```
apt-cache policy xserver-xorg-video-sis
```or
```
apt-cache policy xserver-xorg-video-siliconmotion
```The Xorg-edgers PPA have a newer version .. (almost always) in their repository. 

If you want to update and test run 
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update 
sudo apt-get dist-upgrade
```**Be aware that this repository is NOT considered as stable** , [read the description]("https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise"). 

Also you can try to add the sis module to /etc/modules and see if this can help .. 
```
echo "sis" | sudo tee -a /etc/modules
```[COLOR=Red]In case of a problem[/COLOR] with the upgrade of driver you can revert back with
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers/ppa
sudo apt-get update ; sudo apt-get dist-upgrade
```Thats all my suggestions about this chip. 

Good Luck.

---

### Post by Oweirdone on 2012-12-27
```
apt-cache policy xserver-xorg-video-sis
```

gave me

```

  Installed: 1:0.10.3-3build2
  Candidate: 1:0.10.3-3build2
  Version table:
 *** 1:0.10.3-3build2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
```

Whilst 

```
apt-cache policy xserver-xorg-video-siliconmotion
```

gave me

```

  Installed: 1:1.7.5-1build2
  Candidate: 1:1.7.5-1build2
  Version table:
 *** 1:1.7.5-1build2 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
```

If this helps, I'll let you know what happens when I try the update thing :)

---

### Post by Oweirdone on 2012-12-27
Hate to break the double post rule...

But the drivers installed nicely, when I look at my system details it now says, "vesa.6630" with experience as "standard". The computer will still not recognise the second screen. The current resolution is 1024x786 when the optimum is 1280x1024. Is there any way of manually setting the resolution for the screen using the terminal or a program?

Thanks

Owe.

---

### Post by audiomick on 2012-12-27
I don't think you will get an update. The candidate is the same as the installed version.

I assume you have looked at the monitor utility for setting screen resolutions and such. Does it show two monitors connected, or only one?

---

### Post by Oweirdone on 2012-12-27
Yeah that was the first thing I looked at :\ Only seeing one screen and it thinks it's the laptop.

---

### Post by Oweirdone on 2013-01-18
Heya, had to come back to this thread, more problems of the same type.

The second screen still has the problem with the left side of the screen, but I live with that.

The flickering that happened on the laptop screen, now happens every so often on the secondary monitor. Any ideas? I've unplugged and replugged cables, rebooted, not worked :\ It isn't all the time, but sometimes.

---

### Post by helpee on 2013-01-18
Man, I feel like I'm reading a greek tragedy here... sorry, bro, but it sounds like you may have a damaged video card... you might just have to go get your laptop repaired... or set up remote desktop to it and run the old laptop from another computer?

---

### Post by Oweirdone on 2013-01-18
Haha, it's an old laptop :) If there's nothing I can do then I'll keep using whilst it's half decent, and get rid of it when it isn't :) Thanks :)

---

