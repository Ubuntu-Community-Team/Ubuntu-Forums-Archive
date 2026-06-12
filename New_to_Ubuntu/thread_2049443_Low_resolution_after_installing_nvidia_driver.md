---
title: "Low resolution after installing nvidia driver"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Mr_Yaser on 2012-08-28
Im new in ubuntu .. I just installed ubuntu 12.04 x64 today and i folowed this thread to install my graphic card driver.. I was able to install it but unfortunately after restart .. My resolution decreased  to 640 x 480 and i cant change it to any higher.. Anyway, this is the Method i used to install the driver 

[http://www.blogsolute.com/install-latest-nvidia-driver-linux-mint/23836/]("http://www.blogsolute.com/install-latest-nvidia-driver-linux-mint/23836/")


Looking forward for your help i would really appreciate it

---

### Post by ajgreeny on 2012-08-28
I think the problem may be that ubuntu uses lightdm not mdm (mate display manager?) as display manager, therefore the command shown in the "how-to" "sudo service mdm stop" may not do anything.  Did you get any output from running that command from the cli after using Ctrl+Alt+F1?

I also have not used mate, but as it is a fork of gnome 2, I wonder if the problem relates to the driver you downloaded needing some of the gnome 3 libraries.  That may be a bit of a longshot, but is perhaps worth looking into.

---

### Post by Mr_Yaser on 2012-08-28
You are right .. The comand "mdm" didnt work with me, i did a little search in google and i changed it to "lightdm" and contenued the installation.. But the result was not good as you can see from the post

Anyway thank you for the response and i would realy apreciate it if you can fix my problem

---

### Post by pqwoerituytrueiwoq on 2012-08-28
update the driver
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get  install nvidia-current -y
```edit:looks like you installed it the hard way, which means reinstalling after every kernel update
```
sudo nvidia-installer --uninstall
``` to remove the one you installed the hard way
```
sudo nvidia-xconfig
``` may fix your issue
edit2: looks like you were not able o install it the hard way since you cant figure out how to stop the xserver (recovery mode works great for this)
but just use that 1st command and reboot to update the driver

---

### Post by Mr_Yaser on 2012-08-28
still the same,, any idea what might be the problem ?

anyhow, thanks [pqwoerituytrueiwoq]("http://ubuntuforums.org/member.php?u=865458") for trying to help really appreciate it

---

### Post by pqwoerituytrueiwoq on 2012-08-28
please post output of [FONT=Courier New]cat /etc/X11/xorg.conf[/FONT] (or attach that file)
also post what your correct screen resolution is

---

### Post by NikTh on 2012-08-28
Hi , 
can you please open a terminal and post the output of 
```
lspci -nnk | grep -iA2 vga
```this is one command , one line. 

**Put the results between ```
 brackets . **

[noparse][code]the results here
```[/noparse]

Thank you

---

### Post by amirfluid on 2012-10-15
Hi, I have the same problem and the output of lspci -nnk | grep -iA2 vga is
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Lenovo Device [17aa:21d1]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [Quadro NVS 4200M] [10de:1057] (rev a1)
	Subsystem: Lenovo Device [17aa:21d1]
	Kernel driver in use: nvidia

```

I would be thankful if you can help me fix the resolution.

---

### Post by NikTh on 2012-10-15
> **amirfluid said:**
> Hi, I have the same problem and the output of lspci -nnk | grep -iA2 vga is
```

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Lenovo Device [17aa:21d1]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [Quadro NVS 4200M] [10de:1057] (rev a1)
    Subsystem: Lenovo Device [17aa:21d1]
    Kernel driver in use: nvidia

```I would be thankful if you can help me fix the resolution.
Hi, 

You have 2 graphic cards. As we say : Hybrid graphics. The good thing here is that you have Intel and Nvidia, so your problem probably will be solved fairly easy. 

Read the 3rd post from [this thread]( http://ubuntuforums.org/showthread.php?t=1854915) and hopefully you will figure it out easily. 

Thanks

---

