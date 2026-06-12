---
title: "Installing Ubunto for the first time. Help Please!"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by ezcomputersolutions on 2008-08-08
Hi,
I am new at this.
I have download Ubunto and put it on a CD. I want to Dual Boot.
I have a Everex Stepnote PC. It came preloaded with vista, but I had XP put on instead. I know want to Dual Boot with Ubunto. 
The last time I installed Ubunto, the screen was to large, and I could not figure out how to adjust the resolution to make the screen smaller. 
I am also wandering about Driver issues. If I install Ubunto know with XP as my main OS, after I install Ubunto on my other Partion, will a boot menu come up? So that I can choose which OS I want? Also, where can I find the correct drivers to download and install?
I appreciate the help,
Thank you,

---

### Post by Diabolis on 2008-08-08
Yes, you'll have a menu from where you can choose which operating system you want to use.

If you can't see all the contents of a window, due to low resolution, you can press <Alt> and click on the window to move it around.

Before searching for the correct drivers, you need to know which is your graphics card:
```
lspci | grep VGA
```

You can reconfigure your graphics with this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by trigsenior on 2008-08-08
hello , 

Here is a tutorial for setting up the dual partion 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

Driver problems , you should cross that bridge when you get there as it is very difficult to fix from windows. However the screen resolution have a look at this post [http://ubuntuforums.org/showthread.php?t=500340](http://ubuntuforums.org/showthread.php?t=500340). But like i said do the install first before you worry about drivers. 


Hope this atleast pointed you in right direction =) 

Btw its ubuntu not ubunto but easy mistake weird name for os :)

---

### Post by vikramaditya on 2008-08-08
If you can get into your bios (usually hit F2 or escape key during bootup) then set your pc to boot from cdrom drive.  Then, you can take the ubuntu live cd for a test drive without installing.  If it behaves ok, chances are good that it'll install ok.

---

### Post by dje on 2008-08-08
have a good read on [psychocats]("http://www.psychocats.net/ubuntu/index.php") and also [ubuntutip]("http://ubuntutip.googlepages.com"), they've both got some great resources

dje

---

### Post by ezcomputersolutions on 2008-08-08
Ok, Thanks,
My graphics card is:
 VIA Chrome9 HC IGP Family

---

### Post by tanman on 2008-08-08
Hi,
If you want to you can check out some of my videos that are directed to newer users. I do a podcast called MSC Giz Cast.

The home page is located here:
[-MSC Comp Casts]("http://www.msccompcasts.com")

---

### Post by Diabolis on 2008-08-08
If your graphics don't work out of the box after installing Ubuntu, this thread might be of your interest:

[http://ubuntuforums.org/showthread.php?t=655143](http://ubuntuforums.org/showthread.php?t=655143)

---

