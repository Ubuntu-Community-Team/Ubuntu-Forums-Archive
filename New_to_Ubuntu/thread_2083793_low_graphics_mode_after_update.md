---
title: "low graphics mode after update"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by f99777 on 2012-11-13
I am a total beginner so please take that into account...

I wiped an old dell optiplex sx280 and put 12.10 (I think) on it and it was working fine.

It wanted to update and I said yes, it installed and required a reboot but ever since I get the message I am running in low graphics mode and I can't get past it or get it to boot.

I have video files on the desktop I want, if I can get to them and save them to an external hard drive I'll just reinstall from a boot CD but I'd rather not lose the files.

Any step by step help would be greatly appreciated.

---

### Post by mardybear on 2012-11-13
You should be able to retrieve your files using the bootCD or even low graphic mode.

It seems your X Window system is not working properly, hence the low graphic mode. The following steps will reset your xorg.conf file.

Boot your computer to the login prompt but don't login.

Press CTRL + ALT + F1 to access the terminal, login using your username and password.

Enter the following to backup your existing xorg.conf file (must be exact):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Enter the following to reconfigure your xorg.conf file (must be exact):
sudo dpkg-reconfigure xserver-xorg

Enter 'sudo reboot' to reboot your system.

If it worked, you should be able to login normally and get on with your life. If not, post back and maybe someone else can help.

mardybear

---

### Post by NikTh on 2012-11-14
> **f99777 said:**
> 
It wanted to update and I said yes, it installed and required a reboot but ever since I get the message I am running in low graphics mode and I can't get past it or get it to boot. 
Hi,

this is probably due to a fault of graphics card driver. 
Try what @mardybear suggested , but is not sure that you have an xorg.conf file (xorg.conf is not a requirement anymore). 
You can tell us what graphics card you have and if you remember to install any additional driver. 

> **f99777 said:**
> I have video files on the desktop I want, if I can get to them and save them to an external hard drive I'll just reinstall from a boot CD but I'd rather not lose the files.
That's easy. 
Just boot from the LiveCD-USB of Ubuntu and open nautilus (the default file manager) . 
Then search - find - copy your important files to the external HDD. 

Thanks

---

### Post by f99777 on 2012-11-16
> **mardybear said:**
> You should be able to retrieve your files using the bootCD or even low graphic mode.

It seems your X Window system is not working properly, hence the low graphic mode. The following steps will reset your xorg.conf file.

Boot your computer to the login prompt but don't login.

Press CTRL + ALT + F1 to access the terminal, login using your username and password.

Enter the following to backup your existing xorg.conf file (must be exact):
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Enter the following to reconfigure your xorg.conf file (must be exact):
sudo dpkg-reconfigure xserver-xorg

Enter 'sudo reboot' to reboot your system.

If it worked, you should be able to login normally and get on with your life. If not, post back and maybe someone else can help.

mardybear

Thanks for your input I'll give it a go

---

### Post by f99777 on 2012-11-16
> **NikTh said:**
> Hi,

this is probably due to a fault of graphics card driver. 
Try what @mardybear suggested , but is not sure that you have an xorg.conf file (xorg.conf is not a requirement anymore). 
You can tell us what graphics card you have and if you remember to install any additional driver. 


That's easy. 
Just boot from the LiveCD-USB of Ubuntu and open nautilus (the default file manager) . 
Then search - find - copy your important files to the external HDD. 

Thanks

If mardybears doesn't work I'll try what you suggested, thanks!

---

