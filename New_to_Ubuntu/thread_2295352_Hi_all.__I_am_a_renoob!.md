---
title: "Hi all.  I am a renoob!"
date: 2015-09-17
forum: New to Ubuntu
---

### Post by fishman2 on 2015-09-17
I used Ubuntu in its early stages when all versions of Linux were somewhat stable.  :p  After reading Microsoft's new privacy policy for Windows 10 and also being rolled into Windows 7 and 8, I am back!  The only Windows PC I have is one for gaming only and some development/testing.  My full use Lenovo Y510P laptop is now on Ubuntu 14.x.  

One of the most important lessons that I have learned today is NEVER install Nvidia drivers from the Nvidia site for Ubuntu.  ALWAYS use the Search for applications feature, and type in "drivers", then select "Additional Drivers" and then select the appropriate Nvidia drivers.  If you do it any other way, you will break all of the OpenGL symbolic links, and it is very difficult to fix if you are new to Linux.

Anyway, I hope to contribute to this community as I learn.  I am a software engineer, but so far all of my development has been Java, C# (not mono but Windows), and mainframe application development, along with a bit of web and database development.

---

### Post by Bashing-om on 2015-09-17
fishman2; Hi ! Welcome to the forum;

And a warm welcome back .. 
Hang in here, you will find that this OS is a programmer's dream come true.

[INDENT][INDENT]we can do
[/INDENT][/INDENT]

---

### Post by tristan16 on 2015-09-18
Funny, I actually *have* to install Nvidia drivers from their website, otherwise BOINC can't find my GPU. It doesn't seem to break anything, but it's a little annoying having to reinstall after every kernel upgrade.

---

### Post by DuckHook on 2015-09-18
> **tristan16 said:**
> Funny, I actually *have* to install Nvidia drivers from their website...it's a little annoying having to reinstall after every kernel upgrade.Does installing DKMS help? I haven't messed around with nVidia for a while now, but DKMS sure helped with my proprietary AMD drivers back in my 12.04 install.

---

### Post by tristan16 on 2015-09-18
> **DuckHook said:**
> Does installing DKMS help? I haven't messed around with nVidia for a while now, but DKMS sure helped with my proprietary AMD drivers back in my 12.04 install.

All I know about DKMS is that it's used in VirtualBox. I installed it, but I won't know if it does anything until I need to update the kernel again.

---

### Post by Curtis310 on 2015-09-18
Thanks I'll keep that in mind when installing drivers for my Nvidia card.

---

### Post by DuckHook on 2015-09-18
> **tristan16 said:**
> All I know about DKMS is that it's used in VirtualBox. I installed it, but I won't know if it does anything until I need to update the kernel again.It is used inside VirtualBox to automatically update the guest's VM drivers whenever a new kernel is added. When installed to your primary OS, it should perform the same function in your main box: that is, to auto update video drivers for every new kernel. Important to note that it requires an initial video driver installation to register the driver to its internal database before it will subsequently auto-update. Therefore, if you install DKMS *after* your proprietary video driver is already in place, you will need to reinstall that driver one more time after your next kernel upgrade. But thereafter, it should auto-update with each new kernel.

---

