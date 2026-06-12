---
title: "Wireless Firmware missing, what to do?"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by ask_ on 2011-12-25
Hello,

I have a Laptop on which I have got Windows Vista running. I use wi-fi broadband via a wired router in my house. The windows vista is running Wireless internet properly.
 In ubuntu below network icon, I see 'Wireless (firmware missing)'. What should I do next ?


Is there a way to install the without resorting to an internet connection as I am unable to do so via Ubuntu ?


P.S : I do not know what I should install, so please tell what are the Linux commands whose output I should post, so that you can help me with my problem.

---

### Post by josephmills on 2011-12-25
> **ask_ said:**
> Hello,

I have a Laptop on which I have got Windows Vista running. I use wi-fi broadband via a wired router in my house. The windows vista is running Wireless internet properly.
 In ubuntu below network icon, I see 'Wireless (firmware missing)'. What should I do next ?


Is there a way to install the without resorting to an internet connection as I am unable to do so via Ubuntu ?


P.S : I do not know what I should install, so please tell what are the Linux commands whose output I should post, so that you can help me with my problem.





Hello there could you please open your terminal (ctrl + alt + t )
and enter in 
```
lspci -nn && lsmod && rfkill list all 
``` then paste here please and thanks happy holidays !

---

### Post by lkraemer on 2011-12-26
The easiest thing to do, is to get an Ethernet Patch cable, plug into
Ethernet and do a update.  Then check for New Hardware Drivers.
Most of the time that will get your Wifi working.

You can also post the output of the following so we have the info we need:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modules
iwconfig

```

If you need the Broadcom Firmware there are several good HOWTO's on the forum.
One of which is:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)

But we really need to know:
Ubuntu (*nix) Version
Wifi Hardware Info
Default driver used in (*nix)
What you have attempted to install via Ndiswrapper, if any....
The currently loaded Wifi modules....

All of which the above commands will provide.

lk

---

### Post by ask_ on 2011-12-27
Luckily , I was able to connect via , ethernet wire. And was able to get the firmware driver via the update as u suggested.

Thanks everyone !!!!

---

