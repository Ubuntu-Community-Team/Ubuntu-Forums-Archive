---
title: "NVidia dirver for Ubuntu-x86_64 doesn't work"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-08-14
Hello there. I just installed the latest NVIDIA driver [NVIDIA-Linux-x86_64-173.14.12-pkg2.run] but got some problems. After I restarted my computer, I can only get 800x600 resolution. 

Could anyone here let me know how to diagnose and fix this problem?

Thanks,

---

### Post by tuxxy on 2008-08-14
You should of jsut enabled the driver at** system > admin > hardware drivers**, if you tried then you could also download envy and try and isntall through this.

---

### Post by Unewbeginner on 2008-08-14
> **tuxxy said:**
> You should of jsut enabled the driver at** system > admin > hardware drivers**, if you tried then you could also download envy and try and isntall through this.

hi tuxxy, I tried this but it still doesn't work. do you mean I need to uninstall the driver I downloaded from the web? 

Thanks,

---

### Post by tuxxy on 2008-08-14
Is there anything displayed at **system > admin > hardware drivers**

---

### Post by drs305 on 2008-08-14
I use EnvyNG but you can try this for stuck resolutions:
Backup xorg and run configuration app:
```
sudo cp /etc/X11//xorg.conf /etc/X11/xorg.conf-bak
sudo displayconfig-gtk

```

If that doesn't give you what you want you can try configuring it via the Nvidia X configuration app (you may have to install it):
```
gksu nvidia-settings
```

If these don't work and you don't get an answer, EnvyNG has worked well for me for installing nvidia drivers.

---

### Post by cprofitt on 2008-08-14
Sounds like the issue may be the video drivers not detecting the refresh rate or model properly... and defaulting to 800x600.

---

### Post by Unewbeginner on 2008-08-14
> **tuxxy said:**
> Is there anything displayed at **system > admin > hardware drivers**

Yes, it is
```
NVIDIA accelerated graphics driver (latest cards)
```

I also tried Envy, but still can't make it work. Any ideas?

Thanks,

---

### Post by erickghint on 2008-08-14
Did you edit your disabled modules?

gksudo nano /etc/default/linux-restricted-modules-common

There will be a bit at the bottom that looks like this:


DISABLED MODULES - ""

Just put nv in the quotes and you're good to go. You may have to reinstall the driver, but this time it will stick.

Hope this works for you.

---

### Post by Unewbeginner on 2008-08-14
> **drs305 said:**
> I use EnvyNG but you can try this for stuck resolutions:
Backup xorg and run configuration app:
```
sudo cp /etc/X11//xorg.conf /etc/X11/xorg.conf-bak
sudo displayconfig-gtk

```

If that doesn't give you what you want you can try configuring it via the Nvidia X configuration app (you may have to install it):
```
gksu nvidia-settings
```

If these don't work and you don't get an answer, EnvyNG has worked well for me for installing nvidia drivers.

Hi I tried both of your suggested solution, but neither of them work to me. I already tried EnvyNG but it didn't work.

---

### Post by tuxxy on 2008-08-14
Did you download the driver from the web first? is it possible you have installed more than 1 driver by mistake? 

yes uninstall the driver you downloaded from the web, Search in synaptic for nvidia-glx and nvidia-glx-new see which driver you have installed here and also remove any you do.

Now try a fresh driver install from system > admin > hardware drivers and if it that fails try envy again.

---

### Post by Unewbeginner on 2008-08-15
> **tuxxy said:**
> Did you download the driver from the web first? is it possible you have installed more than 1 driver by mistake? 

yes uninstall the driver you downloaded from the web, Search in synaptic for nvidia-glx and nvidia-glx-new see which driver you have installed here and also remove any you do.

Now try a fresh driver install from system > admin > hardware drivers and if it that fails try envy again.

I unistalled all the drivers and tried all you suggested, but it still doesn't work for me... 

Anyone could help me out?

Thanks

---

### Post by keyboardslave on 2008-09-17
Use this Driver.
(beta driver)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_17768&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17768&num=1)

"wget ftp://download.nvidia.com/XFree86/Linux-x86_64/177.68/NVIDIA-Linux-x86_64-177.68-pkg2.run"
(x86_64 version)

"wget ftp://download.nvidia.com/XFree86/Linux-x86/177.68/NVIDIA-Linux-x86-177.68-pkg1.run"
(x86)


With this Tutorial,
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=](http://ubuntuforums.org/showpost.php?p=5086971&postcount=)


I bet it will work :P

Regards,

---

### Post by road_rage on 2009-01-29
OK, so I was also in NVIDIA gtx260 driver hell and the instruction at the link worked perfectly. 

Now if we could just make this easier for others to find. I was not really sure what to do as everywhere I went it said to goto to the Sys-->Admin-->Hardware Drivers and that never showed anything for me either. 

Sorry for rambling, just appreciative and hoping a bump may give this solution the love and exposure it deserves.

TY again.

---

### Post by birdiewd on 2009-02-14
> **road_rage said:**
> OK, so I was also in NVIDIA gtx260 driver hell and the instruction at the link worked perfectly. 

Now if we could just make this easier for others to find. I was not really sure what to do as everywhere I went it said to goto to the Sys-->Admin-->Hardware Drivers and that never showed anything for me either. 

Sorry for rambling, just appreciative and hoping a bump may give this solution the love and exposure it deserves.

TY again.

I had the same troubles, followed the guide above and now I'm back in 1680x1050 bliss with all my eye candy back on. WOOT for the Ubuntu forums and the people who post to them!!!!

---

