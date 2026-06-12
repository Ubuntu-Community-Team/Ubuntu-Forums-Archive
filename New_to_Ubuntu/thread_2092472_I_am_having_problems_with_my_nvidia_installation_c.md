---
title: "I am having problems with my nvidia installation can you help?"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by computernewb22 on 2012-12-07
So my ubuntu 12.04 was not recognizing my nvidia driver and had it set on unknown and was booting me in 2D enviroment and would not boot any of the games. So I followed this video on youtube [http://www.youtube.com/watch?v=qYYnTdX6EwI](http://www.youtube.com/watch?v=qYYnTdX6EwI) (All of the instrutctions are in th description so you guys don't have to watch the whole video) and I did everything he said to do. But then I get stuck in this part where he tells me to >  chmod +x devdriver*.run (your driver filename) and I type this in after I download the driver and restart my laptop and hit alt+ctrl+F1 >  chmod +x NVIDIA-Linux-x86_64-310.19.run  and nothing happens so I type this in > chmod +xNVIDIA-Linux-x86_64-310.19.run
  and I get this response > chmod: missing operand after `+xNVIDIA-Linux-x86_64-310.19.run'
Try `chmod --help' for more information.
  What am I doing wrong? can you help?

---

### Post by pierceTN on 2012-12-07
try entering these in the terminal:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current


Pierce

---

### Post by computernewb22 on 2012-12-07
I did that and my screen is still in 640X480 resolution.

---

### Post by grahammechanical on 2012-12-08
If the Nvidia driver is installed you will have in the Dash the Nvidia Xserver Settings Manager. That will give you information about the driver and its configuration. It should let you change settings.

In System Settings there is a utility called Details. It always says Graphics unknown and Driver unknown. It says this when I use 12.04 and 12.10 and also now when I am using 13.04 development version. I do not worry about it. 

These utilities are still under development. In fact Linux and Ubuntu should be considered as under continual development and not finished products.

You will also find in the Dash a Utility called Additional Drivers. I find that a better way to change video drivers than using commands.

Regards.

---

### Post by Bartender on 2012-12-08
> **grahammechanical said:**
> You will also find in the Dash a Utility called Additional Drivers. I find that a better way to change video drivers than using commands.

+1, unless for some crazy reason the Additional Drivers app can't recognize your nVidia card?  I've installed Ubuntu several times in the last few years to PC's running nVidia cards and always used the "Hardware Drivers" or "Additional Drivers" utility. 

Run the utility.  It should look at your card, then come up with a short list of nVidia drivers.  One will be recommended.  "Activate" that driver.  I don't know why it's called "Activate", that's a little confusing, so just think of Activate as "download & install".

When it's finished installing, you might want to restart (unnecessary?) then tap Alt+F2 key.  Type or paste 

```
gksudo nvidia-settings
```

into the box, and hit Enter.  That'll get you into the nVidia configuration utility.  

If you just type 

```
nvidia-settings
```

that'll get you into the nVidia configuration utility.  It'll look the same as if you'd typed "gksudo" but it won't store any changes you make!

EDIT:  I can't guarantee that you'll be able to run your games, but the above *should* install the best nVidia drivers for your setup.

---

