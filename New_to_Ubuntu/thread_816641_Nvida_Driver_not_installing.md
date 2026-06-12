---
title: "Nvida Driver not installing"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by krav maga on 2008-06-02
Hello,
  
 I am trying to install the driver NVIDIA-Linux-x86_64-173.14.05-pkg2.run for the Nvidia 9800 gtx on version Ubuntu 8.04

I have used su and sudo both tell me:

-desktop:~$ sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run
[sudo] password for : 
sh: Can't open NVIDIA-Linux-x86_64-173.14.05-pkg2.run


Then if i try to run the driver with "Run through terminal" it gives me the error code:ERROR: nvidia-installer must be run as root


Thank you so much in advance for you help as I am very new to Linux. 

Krav [http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)

---

### Post by krav maga on 2008-06-02
/ bump

---

### Post by alienexplorers on 2008-06-02
have you tried loading the nvidia drivers using Envy-ng which is located in the synaptic repositories.

---

### Post by krav maga on 2008-06-03
No i have not. I will try to figure out how to do that thanks!

---

### Post by Xiong Chiamiov on 2008-06-03
The original problem lies in that bash is trying to launch "NVIDIA-Linux-x86_64-173.14.05-pkg2.run" from one of the standard bin locations, eg /usr/bin or /usr/local/bin, just as in how you can simply call the command "ls".  Try typing
```

sudo ./NVI

```
and then pressing tab to complete the filename.  "./" indicates that it is in the current directory.

---

### Post by krav maga on 2008-06-03
When i type that i tells me the command is invalid? Is there something silly i am not doing?

Can i use "wine" to run the windows version? I dont think that would work but im 99% newb

---

### Post by Ilias83 on 2008-06-03
Just type in terminal:
sudo apt-get install envyng-gtk
this will install EnvyNG.
Then Application->System Tools->EnyNG and the rest is easy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by krav maga on 2008-06-03
Does envy support 9800 yet. I looked at the drivers and they were the incorrect versions. I am still not able to install the driver.

---

### Post by PmDematagoda on 2008-06-03
> **krav maga said:**
> Does envy support 9800 yet. I looked at the drivers and they were the incorrect versions. I am still not able to install the driver.

First of all, where did you download the Nvidia driver to?

---

### Post by hotweiss on 2008-06-03
This should fix it:

Download the new driver:

[http://www.nvnews.net/vbulletin/showthread.php?t=113919](http://www.nvnews.net/vbulletin/showthread.php?t=113919)

0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

---

### Post by Colonel Goeth on 2008-06-03
> **hotweiss said:**
> This should fix it:
0. sudo apt-get remove nvidia*
1. Ctrl-Alt-F1
2. sudo /etc/init.d/gdm stop
3. sudo su
4. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
5. go through all the prompts
6. restart

Does this work? Did you try restarting a couple times?  
What happens if the kernel gets updated when you do an apt-get upgrade?  Do you just repeat the process?

I tried this but I used sudo instead of sudo su to run sh ./NVIDIA-L... It worked for a while but doesn't work after I reboot.  I have 9600GT with Kubuntu Hardy.

---

### Post by krav maga on 2008-06-03
> **PmDematagoda said:**
> First of all, where did you download the Nvidia driver to? The desktop.

Hotwiess I took those steps and it still tells me that it " can not open file" there must be something really simple i am not doing. It sounds like it does not have the permission to open the file?

Are there anyfiles i need or kernels?

Thanks for you help guys i hope i can figure this out!

---

### Post by hotweiss on 2008-06-03
> **krav maga said:**
> The desktop.

Hotwiess I took those steps and it still tells me that it " can not open file" there must be something really simple i am not doing. It sounds like it does not have the permission to open the file?

Are there anyfiles i need or kernels?

Thanks for you help guys i hope i can figure this out!

See if this post doesn't help you:

[http://ubuntuforums.org/showpost.php?p=5082510&postcount=2](http://ubuntuforums.org/showpost.php?p=5082510&postcount=2)

---

### Post by avtolle on 2008-06-03
> **krav maga said:**
> The desktop.

Hotwiess I took those steps and it still tells me that it " can not open file" there must be something really simple i am not doing. It sounds like it does not have the permission to open the file?

Are there anyfiles i need or kernels?

Thanks for you help guys i hope i can figure this out!
OK, since you downloaded the file to your desktop, have you, in the terminal ```
cd Desktop
```, then tried the commands which are not working? Note the uppercase "D" in the above.

---

### Post by krav maga on 2008-06-03
Hotweiss, thank you for that link it worked perfectly!:) How can we get that sticky?

---

