---
title: "Disable bluetooth and wifi (on server)"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by killwarez on 2013-12-05
hello, I am running ubuntu 13.10 server on mac mini. Everything is great, I want to save some power however and want to make sure my Wifi and Bluetooth are turned off since I dont use them.

How would I make sure they are off permanently (i.e. dont turn back on after reboot).

I tried using rfkill but it says its a "soft" block.... can I do a hard block? does soft block still use power?

Side note - ive looked into powertop app, and it has good/bad section. When I switch everything to "good" how do I make those settings stick through reboots?

Thanks!

---

### Post by codenine75a on 2013-12-06
> **killwarez said:**
> hello, I am running ubuntu 13.10 server on mac mini. Everything is great, I want to save some power however and want to make sure my Wifi and Bluetooth are turned off since I dont use them.

How would I make sure they are off permanently (i.e. dont turn back on after reboot).

I tried using rfkill but it says its a "soft" block.... can I do a hard block? does soft block still use power?

Side note - ive looked into powertop app, and it has good/bad section. When I switch everything to "good" how do I make those settings stick through reboots?

Thanks!

blacklist your drivers from /etc/modprobe.d/blacklist.conf

---

### Post by killwarez on 2013-12-06
Could someone elaborate on how to determine which drivers and how? I am not a linux guru. Thanks!

---

### Post by ian-weisser on 2013-12-07
> **killwarez said:**
> How would I make sure they are off permanently (i.e. dont turn back on after reboot).

You learn how to identify and blacklist kernel modules: See [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

Or you open up the case and remove those hardware components. Store them carefully - you might want to reinstall them someday.

---

### Post by varunendra on 2013-12-07
> **killwarez said:**
> I tried using rfkill but it says its a "soft" block.... can I do a hard block? does soft block still use power?
I couldn't find any authentic source to back this up, so I may be wrong, but as far as my knowledge and understanding of these devices goes, the power state of both hard and soft block are **'Exactly' same**.

Both hard block and soft block send these devices into a low power state where they consume only enough power to be able to 'keep listening for a resume signal' and resume back when it is sensed. This power is in micro-amps, which means even a tiny button cell can keep them alive in this state for weeks, maybe months.

As such, you really don't need to worry about their power consumption whether they are hard or soft blocked.

> **killwarez said:**
> Side note - ive looked into powertop app, and it has good/bad section. When I switch everything to "good" how do I make those settings stick through reboots?
You can't. Powertop makes temporary changes to system configuration files, and the only way to make these changes permanent is to write/edit these configuration files manually.

Older versions of powertop used to tell the user which files to edit to achieve the optimal power state. The current versions do this automatically and don't tell which files they change/create to do that.

While you can do some research to find that info and tune things to make it permanent, it is not recommended, as aggressive power saving also compromises the performance and sometimes the stability of the OS too (things not working as expected, system crashing etc.).

> **killwarez said:**
> Could someone elaborate on how to determine which drivers and how?
For wireless driver, you can run -
```
lspci -nnk | grep -A2 0280
```
The output will show the driver in use in the last line of the output. You can then add a line "blacklist *<whatever is your driver in the above output>*" in your **/etc/modprobe.d/blacklist** file (existing lines in it will give you an idea of how to add your custom lines in it).

The bluetooth device driver is usually "btusb", but you can confirm that using "usb-devices" command (look for device whose Vendor/Product IDs are same as your bluetooth in "lsusb" output). You can then blacklist it in the same way as above

But again, blacklisting the drivers or removing these cards permanently just to save power is absolutely insane and unnecessary. Once they are disabled using radio kill switch (hard or soft block), they consume 'almost' no power.

---

