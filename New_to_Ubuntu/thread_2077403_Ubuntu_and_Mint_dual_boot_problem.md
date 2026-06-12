---
title: "Ubuntu and Mint dual boot problem"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Polomint01 on 2012-10-28
I have been running Ubuntu now for a few years, I am using 10.10 now.
I did not update to Unity, I prefer the gnome environment.
I was getting worried about the loss of support for 10.10, so decided to install Mint as a dual boot, and see what I thought of it.

I decided to import my apps from Ubuntu to Mint, using the Mint apps transfer program.I did not know that it would also transfer all the Ubuntu config files etc, so now my Mint is a mess. I want to get back to vanilla Mint before the transfer, or if that is not possible.
To un install Mint and re-install it.
My problem is I think that Mint now now contains the boot up (grub?)
So how do I uninstall Mint and still allow Ubuntu to boot up, or how do i get Mint back to vanilla state.
Any help welcome, I am ok with using the terminal, and have some knowledge of dealing with boot up issues (back in my window days)

Thanks

---

### Post by NikTh on 2012-10-28
Hi , 
to get the Mint back to vanilla state , I don't know any other method except re-install. 

If you want to install Ubuntu's grub , then boot to Ubuntu and open a terminal and then give these commands
```
sudo grub-install /dev/sda
sudo update-grub
```If you like the gnome2 environment then consider to install Ubuntu 10.04 LTS (is still supported until April 2013) 
or you can use a new version like Ubuntu 12.04 LTS (support until April 2017) and use the gnome-classic Environment.

About Ubuntu releases - support
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Download Ubuntu 10.04.4 LTS
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)


Download Ubuntu 12.04 LTS
[http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
Gnome-classic in Ubuntu 12.04 LTS
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

Thanks

---

### Post by ajgreeny on 2012-10-28
There's also a long thread about using classic-gnome in 12.04 at [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) which is well worth going to and reading carefully.  It contains not only the basics of using it, but also a lot of tricks and tips to get it working exactly as you want it.

---

### Post by NikTh on 2012-10-29
> **ajgreeny said:**
> There's also a long thread about using classic-gnome in 12.04 at [http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) which is well worth going to and reading carefully.  It contains not only the basics of using it, but also a lot of tricks and tips to get it working exactly as you want it.

Great Thread !!! Bookmarked. 

Thanks :)

---

