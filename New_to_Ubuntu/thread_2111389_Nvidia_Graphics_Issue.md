---
title: "Nvidia Graphics Issue"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by chribuntu on 2013-02-01
Hello! This is my first post. Every few times I boot up I get an error saying it has booted into low-graphics mode. I usually restart the machine 2 times and it fixes the error. But it continues to come up. How do I fix this once and for all?

---

### Post by papibe on 2013-02-01
Hi chribuntu. Welcome to the forums ):P

Did you install the Nvidia proprietary driver? If not, go to 'Drivers' and install the 'nvidia-current (recommended)'.

Then open a terminal, and run:
```
sudo nvidia-xconfig
```
And finally restart your computer.

Let us know how it goes.
Regards.

---

### Post by leptone55 on 2013-02-01
hello,

I have a similar issue as the one described: 

I installed Ubuntu 12.10 on my Macbook 5,2.

To solve it I followed this process [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

When i rebooted the computer was only capable of booting into command line interface. It would boot, black screen, text moving across it then prompted for username and password. then command line.

I have since wiped everything and started over. I have an OSX partition with 10.8.2 and empty LINUX and SWAP partitions ready to go.

Looking at this [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) has me worried as I only see links for MacBook5-2/Lucid and MacBook5-2/Mavrick. Can I put 12.10 or this MacBook and have it work? 12.04? 

If so how do install the proper drivers. Is there a guide somewhere that I can't find for this software with this hardware?

Thank you.

MacBook 5,2 
Intel Core 2 Duo
NVIDIA GeForce 9400M 256MB
OS X 10.8.2

---

### Post by chribuntu on 2013-02-02
> **papibe said:**
> Hi chribuntu. Welcome to the forums ):P

Did you install the Nvidia proprietary driver? If not, go to 'Drivers' and install the 'nvidia-current (recommended)'.

Then open a terminal, and run:
```
sudo nvidia-xconfig
```
And finally restart your computer.

Let us know how it goes.
Regards.


Edit: I reboot several times and got the gui but unity won't load.

---

### Post by papibe on 2013-02-02
Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste the file here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.

---

### Post by chribuntu on 2013-02-02
Here is the link [http://paste.ubuntu.com/1601866/](http://paste.ubuntu.com/1601866/)

---

### Post by drunkenbrawler on 2013-02-02
I had problem with Optimus on my Dell XPS 15-Z. My laptop used to run ubuntu in low graphics mode. I installed Bumblebee. Now everything is working fine.

[http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html)

---

### Post by papibe on 2013-02-02
Thanks.

It looks like the log is for one of those times that all went well as you are getting a resolution of 1280x1024. Is that OK?

Could you post the result of these command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by chribuntu on 2013-02-02
Here is the result of the command
 00:0d.0 VGA compatible controller [0300]: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] [10de:03d6] (rev a2)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:1405]
    Kernel modules: nvidia_current, nvidia_173, nouveau, nvidiafb
By the way it has gotten worse when I boot into Ubuntu the screen is small and it says Input Signal out of Range

---

