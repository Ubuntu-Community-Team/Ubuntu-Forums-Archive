---
title: "LG 24MK400H-B Hdmi-no signal/Vga-bad image"
date: 2019-09-05
forum: New to Ubuntu
---

### Post by migteixas on 2019-09-05
Hey,

Changed my monitor recently to LG 24MK400H-B and the image is really bad whenever anything moves(scroll, mouse, videos). 
I am currently pluged with the Vga since the Hdmi doesn't work at all.
I have a gtx960 and already updated my nvidia drivers. Currently am using nvidia-driver-435.

Thanks

---

### Post by Autodave on 2019-09-05
Where did you get that driver from?

What is the max size of the monitor's resolution?  Some cheaper VGA cables are do not do well on larger resolutions.

---

### Post by Skaperen on 2019-09-05
which HDMI doesn't work?  video out on PC/card?  video in on monitor?  cable?

---

### Post by migteixas on 2019-09-05
> **Autodave said:**
> Where did you get that driver from?

What is the max size of the monitor's resolution?  Some cheaper VGA cables are do not do well on larger resolutions.

I believe i got it on terminal using some code i don't remember

1920x1080

Thanks

---

### Post by migteixas on 2019-09-05
> **Skaperen said:**
> which HDMI doesn't work?  video out on PC/card?  video in on monitor?  cable?

I meant that when i plugged it with the HDMI cable it didn't work as the monitor said "No Signal". Haven't tested yet

---

### Post by migteixas on 2019-09-05
Ok,
I was beeing dumb, the hdmi cable was not connected properly.
Now i have a grey screen on the HDMI but only after i start my session. While the system is iniciating it still says "No Signal"

---

### Post by Frogs Hair on 2019-09-05
CP from your previous thread. You have a graphics driver PPA in your repository sources list.

> Get:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease [21,3 kB] 

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/dev](https://launchpad.net/~graphics-drivers/+archive/ubuntu/dev)

---

### Post by Frogs Hair on 2019-09-05
Post the output of the following command.

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

---

### Post by migteixas on 2019-09-06
> **Frogs Hair said:**
> Post the output of the following command.

```
lspci -k | grep -EA3 'VGA|3D|Display'
```

```
01:00.0 VGA compatible controller: NVIDIA Corporation GM206 [GeForce GTX 960] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. [MSI] GM206 [GeForce GTX 960]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
```

---

### Post by Frogs Hair on 2019-09-06
Open software and updates/sources-additional drivers and see if proprietary drivers are available or installed. It appears as if you are using the open source driver.

---

### Post by migteixas on 2019-09-06
Using NVIDIA metapackage from nvidia-driver-435 (open source)

This is the one that is selected

---

### Post by Frogs Hair on 2019-09-06
If there are no other options listed that's what's available. What can tell us about the driver ppa you installed ?

---

### Post by migteixas on 2019-09-06
I have 4 other options all of them Open Source. Should i get proprietary drivers?

Btw, i don't know what ppa means so i can't really tell you nothing about that

---

### Post by Frogs Hair on 2019-09-06
At some point a driver ppa was  added to the system. If there are no proprietary divers listed they may not be available for your card.
> Get:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease [21,3 kB]                      

---

### Post by migteixas on 2019-09-06
What should i do with that?

I've seen that there are drivers for my card at the geforce site, how can i install that?

---

### Post by Frogs Hair on 2019-09-06
Can you please take screenshot of the driver options, you can upload it using the paperclip symbol on the reply toolbar. I'm guessing the 390 tested proprietary driver should work with that card, but don't know why it's not listed.

---

### Post by Autodave on 2019-09-07
Do NOT install any driver from Nvidia's website!  You *never* want to use them.

---

### Post by migteixas on 2019-09-07
> **Frogs Hair said:**
> Can you please take screenshot of the driver options, you can upload it using the paperclip symbol on the reply toolbar. I'm guessing the 390 tested proprietary driver should work with that card, but don't know why it's not listed.


[ATTACH=CONFIG]283960[/ATTACH]

---

### Post by Frogs Hair on 2019-09-07
I think those drivers are from the PPA. Switch to the nouveau driver on the bottom and then go into other software and disable the driver PPA and then check if there are any proprietary options. If not you can always enable the PPA again if needed.  


> [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu)

---

### Post by migteixas on 2019-09-07
No proprietary options still

---

### Post by migteixas on 2019-09-07
```
sudo apt-get purge nvidia*
```

I used this and suddenly:
[ATTACH=CONFIG]283964[/ATTACH]

Everything still the same though

---

### Post by CatKiller on 2019-09-07
> **migteixas said:**
> Hey,

Changed my monitor recently to LG 24MK400H-B  
... meaning you were using something else before. What resolution was that, and how was it connected? 

>  and the image is really bad whenever anything moves(scroll, mouse, videos).  

What exactly do you mean by this? 

>  I am currently pluged with the Vga since the Hdmi doesn't work at all.

You'll be better off if you can get the HDMI working rather than using VGA. VGA is analogue, and many monitors' EDID implementations over VGA are pretty horrible. With that monitor, HDMI will give you a higher refresh rate as well as a less noisy signal and potentially better EDID signalling. 

The display that's initialised first, which is used for the BIOS screen, the Grub stuff and Plymouth, is set in the BIOS. You'll ideally have that set to your HDMI output. Then the X server will be started, either autoconfigured or using xorg.conf, to display the login screen. When you log in the display will be set using ~/.config/monitors.xml. Additionally, nvidia-settings stores its own configuration somewhere else.

So there are several places where your old configuration may be interfering with your new one, in addition to all the usual fun & games with inappropriate signalling, cables, and autodetection.

---

### Post by Frogs Hair on 2019-09-07
> **migteixas said:**
> ```
sudo apt-get purge nvidia*
```

I used this and suddenly:
[ATTACH=CONFIG]283964[/ATTACH]

Everything still the same though

You now have 2 proprietary driver options you didn't have before. Try with a different cable if possible just to make sure that the cable isn't the problem. Do you have DVI/HDMI or VGA/HDMI ?

---

