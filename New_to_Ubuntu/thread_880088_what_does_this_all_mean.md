---
title: "what does this all mean?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by mudassar on 2008-08-04
> You need a recent kernel, at least 2.6.18 or 2.4.26, with kernel headers, and gcc-3.4 or newer. Make sure that /lib/modules/VERSION/build is a link to the kernel source, where VERSION is the version of the kernel you are running; this should be setup automatically by distribution package. If this path is not valid, kernel modules can’t be compiled. Also make sure gcc and associated packages (e.g., libc6-dev on Debian based distributions) are installed so C programs can be compiled. For help with these steps, refer to your distribution documents. 

I'm trying ndiswrapper for my wireless card but following the instructions after this bit leads me to a whole bunch of errors.

So i'm assuming it has something to do with this section, because it was the only bit i skipped due to it causing me to look at my screen like this: o_O

I tried [this link here and my card comes up recognised but with no driver, from what sense i can make of it, it doenst tell me what else to do apart from try ndis.]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?action=fullsearch&context=180&value=linkto%3A%22WifiDocs/WirelessTroubleShootingGuide%22")

I have a bunch of screenshots from my efforts from that guide that clearly shows exactly what card i have, except it doesnt show a driver.

Either this or someone tell me how to get rid of the blasted grub loader along with ubuntu. (without doing the entire reset via vista)

---

### Post by mudassar on 2008-08-04
> You need a recent kernel, at least 2.6.18 or 2.4.26, with kernel headers, and gcc-3.4 or newer. Make sure that /lib/modules/VERSION/build is a link to the kernel source, where VERSION is the version of the kernel you are running; this should be setup automatically by distribution package. If this path is not valid, kernel modules can’t be compiled. Also make sure gcc and associated packages (e.g., libc6-dev on Debian based distributions) are installed so C programs can be compiled. For help with these steps, refer to your distribution documents. 

I'm trying ndiswrapper for my wireless card but following the instructions after this bit leads me to a whole bunch of errors.

So i'm assuming it has something to do with this section, because it was the only bit i skipped due to it causing me to look at my screen like this: o_O

I tried [this link here and my card comes up recognised but with no driver, from what sense i can make of it, it doenst tell me what else to do apart from try ndis.]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?action=fullsearch&context=180&value=linkto%3A%22WifiDocs/WirelessTroubleShootingGuide%22")

I have a bunch of screenshots from my efforts from that guide that clearly shows exactly what card i have, except it doesnt show a driver.
Oh and on that guide it says
> TODO: describe what it means when it shows *-network UNCLAIMED, and no configuration line is present.

Which is what it shows for me. How useful.

Either this or can someone tell me how to get rid of the blasted grub loader along with ubuntu. (without doing the entire reset via vista)

---

### Post by northern lights on 2008-08-04
Can you please post the output of ```
sudo lshw -C network
```Thank you.

Further,> **mudassar said:**
> Either this or someone tell me how to get rid of the blasted grub loader along with ubuntu. (without doing the entire reset via vista)while I don't like this idea, you can set the Windows entry in GRUB as default, decrease the time the menu is show and booting into Vista will be much faster...

---

### Post by mudassar on 2008-08-04
[IMG]http://i7.photobucket.com/albums/y300/mudmankhan/Screenshot-3-1.png[/IMG]

Thanks,

---

### Post by mudassar on 2008-08-19
any help?

---

