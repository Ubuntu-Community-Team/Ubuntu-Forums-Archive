---
title: "New to Ubuntu many issues need help"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by darksyde2 on 2015-09-29
Hi, Im need to ubuntu. I installed ubuntu mate on my old compaq pressario v6000 now im having the following issues;

1- wifi does not work (i tried 'additional driviers'- the 1st time it showed the wifi drivers and i selected it but it doesnt work and every time since then whenever i click additional drivers again the wifi drivers is not shown.

2- clicking shutdown or restart does not turn off the pc- it seems to start shutting down but just stays on the ubuntu mate logo indefinitely( left it shutting down over 8 hrs). u have to press and hold the power button to turn it off.

3- startdisc creator does not work. whenever i tried to make a bootable sd card it copies the files but evetually gives an error "installing bootloader failed"

any help will be appreciated. 

thanks.

---

### Post by yancek on 2015-09-29
Posting some details on your hardware would be a first step, CPU and graphics card, etc.  Did you compare your actual hardware to the minimum requirements to run Ubuntu?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by v3.xx on 2015-09-29
Please post your equipment specs by entering the following command in terminal (press Ctrl + Alt + T) and posting the final output using code tags.

```
sudo apt-get install inxi && inxi -Fxz
```

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

[COLOR="#B22222"]An afterthought:[/COLOR]
If you haven't updated your new install, you need to do so.

---

### Post by DuckHook on 2015-09-29
Hi darksyde2 and welcome to Ubuntu and the forums.

Awaiting your reply to the hardware inquiries requested by *yancek* and *v3.xx*. In the meantime, my guesses as to your issues:

1. I suspect that you have the old broadcom WIFI chipset, which continues to be problematic in Ubuntu. To see if this is so, please post back to this thread the output of the following:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```2. To see what process shutdown hangs on, hit the <ESC> button when the shutdown overlay screen comes on. This will allow you to see the down-and-dirty individual processes being shut down as they occur. If you are lucky, the process that hangs may be declared before waiting interminably to finish. I suspect that your hang has something to do with the (wrong) WIFI driver as well since you tried to install one through "additional drivers". Unfortunately, those drivers will not work for certain broadcom chipsets that may be the usual suspects in your case.

Let's get 1 & 2 dealt with before tackling 3.

---

