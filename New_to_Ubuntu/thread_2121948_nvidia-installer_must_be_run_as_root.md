---
title: "nvidia-installer must be run as root"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by secera on 2013-03-03
i have an nvidia geforce 8600 gt and when i run it as a sudo it says that "sh: 0: Can't open ./NVIDIA-Linux-x86-310.32". 
and i try to run it as a program in terminal it says "ERROR: nvidia-installer must be run as root". what should i do?

---

### Post by Cheesemill on 2013-03-03
Is there any reason you are downloading the driver from the Nvidia website? This should only be done as a last resort.

You should try using the driver from the Ubuntu repositories instead, if you can tell us what version of Ubuntu you are using we can give you specific instructions.

---

### Post by The Cog on 2013-03-03
Are you trying to run a driver downloaded from the nVidia site? If so then unless you have good reason, can I suggest you install the driver provided by the Ubuntu repositories. That way you won't end up with a black screen every time there is a security update to the kernel. 
Open the Ubuntu software centre, choose Edit->Software Sources, and look in the Additional Drivers tab.

If you really want to install the nvidia one, put the word sudo in front of the command, to request admin rights. like this (but you will have to shut down the GUI and do it from a tty console):
```
sudo ./NVIDIA-Linux-x86-310.32
```

---

### Post by darkcrimson on 2013-03-03
First, you'll want to exit X Server if you haven't already. 

```
sudo telinit 3
```

Then, run the installer.
```
sudo ./NVIDIA-Linux-x86-310.32
```

---

### Post by von Corax on 2013-03-03
> **Cheesemill said:**
> Is there any reason you are downloading the driver from the Nvidia website? This should only be done as a last resort.

You should try using the driver from the Ubuntu repositories instead, if you can tell us what version of Ubuntu you are using we can give you specific instructions.

I'm having this same problem. I'm running Lucid LTS (10.04), and the device is a GT540M.

Any guidance you can offer will be greatly appreciated.

---

### Post by darkcrimson on 2013-03-03
Check the Ubuntu Software Center for a current version of the Nvidia drivers. If you're unable to locate one, try using the steps outlined above. You'll need to stop X and install as root by using the commands outlined.

---

### Post by darkcrimson on 2013-03-03
Search for "NVidia binary X.Org driver ('current' driver)" in the Ubuntu Software Center.

---

### Post by 3rdalbum on 2013-03-03
> **von Corax said:**
> I'm having this same problem. I'm running Lucid LTS (10.04), and the device is a GT540M.

Any guidance you can offer will be greatly appreciated.

You should be using a newer version of Ubuntu with newer hardware such as yours, especially if you are new to Linux. If you install 12.04 or 12.10 your graphics card will work using the repository driver like we advised the original poster. Ubuntu 10.04 only has a couple of months of desktop support left anyway.

If there's a specific reason you need 10.04 on that hardware, you can try installing the driver from the Nvidia website, but you need to switch off the X server temporarily.

```
sudo service gdm stop
```

Then use the terminal to run the Nvidia driver installer. You'll need to do this after every kernel update.

Don't know how to use the terminal? Save yourself a lot of hassle, just upgrade your Ubuntu to 12.04 or 12.10 and use the instructions given to the person who originally posted in the thread.

---

### Post by von Corax on 2013-03-04
For the time being I have good reasons for sticking with Lucid. I have tried the Nvidia driver (both the one in the CUDA toolkit and the stand-alone one) but the driver doesn't seem to be finding the card.

---

### Post by mastablasta on 2013-03-04
new ubuntu has newer kernel. drivers in linux are part of kernel. so in order to run linux well on a newer mashcine/hardware it is much better to use newer kernel provided in the newer version of the OS. if you know how, you could maybe also install new kernel on old Ubuntu. though i am not sure if it would work well on desktop.

so your issues could be resolved by simply using 12.04 or 12.10. what is keeping you on 10.04?

---

### Post by sda123 on 2013-03-04
Hey, to solve it do sudo sh NVIDIA-Linux-x86-310.32

I hope it solves your problem :)

Can't help if it doesn't

---

### Post by bogan on 2013-03-04
Hi!, **secera,**

You Posted:> i have an nvidia geforce 8600 gt and when i run it as a sudo it says that "sh: 0: Can't open ./NVIDIA-Linux-x86-310.32". 
and i try to run it as a program in terminal it says "ERROR: nvidia-installer must be run as root". what should i do?I f you really need to install the nvidia.com downloaded driver, there is something wrong  with the command you quote.

Unless you have renamed, or extracted it,  the file should be called "NVIDIA-Linux-x86-310.32[COLOR=#ff0000].run[/COLOR]" and the command you need would be: ```
sudo sh NVIDIA-Linux-x86-310.32[COLOR=#ff0000].run[/COLOR]
``` that assumes you had CD-ed to the folder where the .run file was downloaded, and previously either booted to a text terminal or shut down the Xserver with: ```
sudo service lightdm stop
```.

If you have extracted the .run file then "NVIDIA-Linux-x86-310.32" is a folder containing the decompressed files, including a comprehensive ReadMe file. In that case you should CD to that folder, and the command you need is: ```
sudo nvidia-installer
```

Full instructions are available in :[http://ubuntuforums.org/showthread.php?t=1743535&page=5](http://ubuntuforums.org/showthread.php?t=1743535&page=5) Post #1126

Chao!, **bogan.**

---

### Post by von Corax on 2013-03-06
> **3rdalbum said:**
> You should be using a newer version of Ubuntu with newer hardware such as yours, especially if you are new to Linux. If you install 12.04 or 12.10 your graphics card will work using the repository driver like we advised the original poster. Ubuntu 10.04 only has a couple of months of desktop support left anyway.

If there's a specific reason you need 10.04 on that hardware, you can try installing the driver from the Nvidia website, but you need to switch off the X server temporarily.

```
sudo service gdm stop
```

Then use the terminal to run the Nvidia driver installer. You'll need to do this after every kernel update.

Don't know how to use the terminal? Save yourself a lot of hassle, just upgrade your Ubuntu to 12.04 or 12.10 and use the instructions given to the person who originally posted in the thread.

It turned out that my problem wasn't with the drivers, but that no /dev nodes had been created. I eventually found in another thread a script for creating the appropriate /dev/nvidia* nodes, ran the mknod commands from the script, and have had no trouble getting my CUDA code to run. I haven't tried enabling the X driver yet, though.

Y'know, just in case anyone was interested.

---

