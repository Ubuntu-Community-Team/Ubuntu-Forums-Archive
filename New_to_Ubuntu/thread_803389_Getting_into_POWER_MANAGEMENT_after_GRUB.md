---
title: "Getting into POWER MANAGEMENT after GRUB"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by rraj.be on 2008-05-22
After selecting My os choice from GRUB my monitor goes into power management mode displaying like

HORIZONTAL FREQUEVCY
VERTICAL FREQUENCY

ETC

and time goes on counting down from 20 seconds.

at 5th or 6th second my login screen appears and everything is fine after that.

Whats the cause for this and whats the solution

---

### Post by neurostu on 2008-05-22
it looks like for some reason your video card isn't outputing anything to your monitor and your monitor is going into power management mode.  I'm not sure how to fix it though...

---

### Post by philinux on 2008-05-22
Install and run startupmanager from synaptic.

Tick the box to show text at start up. You can also set the timeout countdown and screen resolution. See screenshot.

---

### Post by rraj.be on 2008-05-22
Is there arny other way to do this.

My net speed is very slow that it will take 1 hour to download 10 MB.

please tell me some other go if possible.

---

### Post by philinux on 2008-05-22
Which ubuntu you got running.

If Hardy have a look in System>Admin>Hardware drivers. See if you graphics card driver is active.

---

### Post by philinux on 2008-05-22
Post the output of 

cat /etc/usplash.conf

---

### Post by rraj.be on 2008-05-22
this is the output

```
# Usplash configuration file
xres=1280
yres=1024


```

---

### Post by philinux on 2008-05-22
Does your monitor support that resolution?

---

### Post by rraj.be on 2008-05-22
I dont know.

I am using LG 15" CRT monitor.

in windows i use to have 1024 X 728.

how to see whether my monitor suports this or not.

---

### Post by philinux on 2008-05-22
In the terminal use


gksudo gedit /etc/usplash.conf

Change the values to those

1024
728
Then click Save
Then reboot

---

### Post by rraj.be on 2008-05-22
Are you sure that there wont be any problem like unable to display monitor beacuse in windows there will be such problem if i reset screen resolution more that a limit.

---

### Post by philinux on 2008-05-22
You're reducing it not increasing it.

what setting you got in System>Prefs>Screen resolution?

---

### Post by philinux on 2008-05-22
Once you've changed usplash.conf you need to issue this command

sudo update-initramfs -u

I forgot that step

---

### Post by rraj.be on 2008-05-22
k.

i cahnged.

then what is ```
initramfs.
```

I created one custom live cd using remastersys reconstructor etc.

every thing just took me to initramfs shell when i booted from the live cd.

is there any solution for this.

---

