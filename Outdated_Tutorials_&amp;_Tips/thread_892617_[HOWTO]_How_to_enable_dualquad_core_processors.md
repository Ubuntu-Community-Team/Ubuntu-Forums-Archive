---
title: "[HOWTO] How to enable dual/quad core processors"
date: 2008-08-17
forum: Outdated Tutorials &amp; Tips
---

### Post by MofroShow on 2008-08-17
[SIZE="5"][COLOR="Red"]** This howto works for ANY type of processor, as stated by 3rdalbum (Thanks!)**[/COLOR][/SIZE]



Ok this is my first Howto, and my first major post so bare with me :]
On my HP dv6000 i have a 1.7Ghz dual core AMD processor.
Now by default (i guess for power saving purposes) Ubuntu only scales my available cpu power as 800mhz. This simply wont do, will it?

[SIZE="4"]Step 1[/SIZE]. [COLOR="#ff0000"]Install cpufreq[/COLOR]

In the terminal (Applications>Accessories>Terminal) type:

```
sudo apt-get install cpufrequtils
```
Say yes to install the package and wait until it is done.

[SIZE="4"]Step 2[/SIZE]. [COLOR="Red"]Identify Scaling Support[/COLOR]

Now by my understanding most processors have certain frequencies that are available for it to operate on.

Type:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
into the terminal and the output should look something like this:
```
1700000 1600000 800000 
```

Those numbers are the available frequencies for your processor (measured in hertz)

There are also certain governers on your pc. You can see these options by typing:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
The output should look like this:
```
powersave conservative userspace ondemand performance 
```

[SIZE="4"]Step 3[/SIZE]. [COLOR="#ff0000"]Giving yourself full access to your cpu[/COLOR]

In the terminal type:
```
sudo dpkg-reconfigure gnome-applets
```
and answer yes.

This should give you the ability to left-click on the cpu frequeny scaling applet and choose how much cpu power you can use!

(The applet is found by right-clicking the panel and going to Add to Panel. Just search "cpu" and there you go.)



*This is my first Howto so any comments or suggestions are helpful and wanted!*

---

### Post by kanazky on 2008-08-19
Sweet I got tons of options, thanks managed to switch from OnDemand to Power/Performance and to 1.99Ghz :D

Thanks

---

### Post by 3rdalbum on 2008-08-19
Three things:

1. Ubuntu uses all your cores by default, no matter whether it's dual, quad, octo, etc. The title of the HOWTO is incorrect.

2. When the system goes under load, it automatically switches to a higher CPU frequency, so you have speed when you need it, and lower power consumption when you don't.

3. If you want the system running flat-out non-stop, you can turn off power scaling in your computer's BIOS. I don't know if HP machines have this option, but my computer does (and it's necessary to turn it off when you are overclocking, otherwise you stay at the stock speed!).

---

