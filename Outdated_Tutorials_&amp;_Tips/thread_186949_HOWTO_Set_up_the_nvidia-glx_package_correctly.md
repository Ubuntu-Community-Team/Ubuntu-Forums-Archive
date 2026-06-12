---
title: "HOWTO: Set up the nvidia-glx package correctly"
date: 2006-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by PPower on 2006-06-02
I found a bug with the nvidia-glx package that will cause it to incorrectly alter the /etc/X11/xorg.conf file. If you dont have any problems with it then this guide is not for you.
(Updated)
1> Restore the backup from the nvidia-glx-config thing. It can be found in /etc/X11
2> Ensure the nvidia-glx package is installed
3> Vim/emacs/nano etc. /etc/X11/xorg.conf as root
4> Change nv to nvidia in the device section for your graphics card.
5> Reboot
6> If it worked you should briefly see the nVidia logo and then X will appear.

Edit: Now a wiki article!

---

### Post by sas171 on 2006-06-02
Thank you for this howto and yes, I had exactly the same problem with my xorg.conf, so I just used the old one (from breezy). My advice to you: always keep working xorg.conf in safe place.

---

### Post by tseliot on 2006-06-02
As I told you on another thread, PPower, the following command seems to be more useful:
```
sudo nvidia-xconfig
```
It automatically configures your xorg.conf buy removing DRI and GLcore and setting the driver to nvidia.

It comes by default with the driver from the repos.

If you use legacy drivers you should install it manually
```
sudo apt-get install nvidia-xconfig
```

and then
```
sudo nvidia-xconfig
```

---

### Post by PPower on 2006-06-03
[QUOTE=tseliot]As I told you on another thread, PPower, the following command seems to be more useful:
```
sudo nvidia-xconfig
```
It automatically configures your xorg.conf buy removing DRI and GLcore and setting the driver to nvidia.

It comes by default with the driver from the repos.

If you use legacy drivers you should install it manually
```
sudo apt-get install nvidia-xconfig
```

and then
```
sudo nvidia-xconfig
```[/QUOTE]
[QUOTE=eqisow]Just to confirm, you have both nvidia-glx and linux-restricted-modules installed, correct? If so, could you possibly post your xorg.conf?[/QUOTE]
Since the majority of people would use the nvidia-glx-config script and dont know about nvidia-xconfig it would be more helpful for them to use that one.
If the nvidia run package uses xconfig then i would avoid that as that didnt work either.

How come nvidia-settings conflicts with nvidia-glx?

---

### Post by tseliot on 2006-06-03
[QUOTE=PPower]Since the majority of people would use the nvidia-glx-config script and dont know about nvidia-xconfig it would be more helpful for them to use that one.[/QUOTE]
I suppose you're talking about the official Wiki. In that case you're right. :) 

[QUOTE=PPower]If the nvidia run package uses xconfig then i would avoid that as that didnt work either.[/QUOTE]
I use it for my scripts and it works great for many users (no one ever complained about nvidia-xconfig).

[QUOTE=PPower]How come nvidia-settings conflicts with nvidia-glx?[/QUOTE]
That's because nvidia-settings is already included in driver 8174 or higher.

However the legacy driver (7174) doesn't include it and you have to install nvidia-settings as a separate package.

P.S. thanks for the guide, it's not that I don't appreciate your effort (which I would like to encourage instead) but I am a supporter of nvidia-xconfig and I use it in my guides.

Keep up the good work :)

---

### Post by madscientist on 2006-06-03
I had to rebuild my kernel because I need to use a binary VPN tool with a KLM to connect to work; this package is supported on Red Hat but not Ubuntu.  I've had lots of problems with distro-specific kernels, but the kernel.org kernels always seem to work fine.  So, after I installed Ubuntu 6.06 yesterday I grabbed 2.6.16.19 from kernel.org, built it (using make-kpkg) and installed it.  That worked fine and now I can connect to work.

BUT!  There are two problems.  The main one that I want to discuss here is that my nvidia driver no longer works.  I had installed nvidia-glx with the original 6.06 kernel and that worked great.  However, it seems that the KLM is specific to that kernel, or something?  Now that I've booted into my new kernel I've tried to uninstall/re-install the nvidia-glx package, run dpkg-reconfigure, etc. and it never seems to do anything like rebuild the KLM for my new kernel, and insmod etc. never finds it.

Is this package hardcoded for the 6.06 kernel only?  Do I need to reconfigure the KLM by hand somehow?  I read the README for nvidia-glx but it mentions scripts like nvidia-installer etc. which I can't find.

Do I have to go get the .run file directly from nvidia?  Help!! ](*,)

---

### Post by tseliot on 2006-06-03
> **madscientist]I had to rebuild my kernel because I need to use a binary VPN tool with a KLM to connect to work said:**
> (*,)
Did you compile the kernel headers?
If so try either Method 2 of my guide or my script (for an automatic installation of the driver):
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by PPower on 2006-06-03
> **madscientist]I had to rebuild my kernel because I need to use a binary VPN tool with a KLM to connect to work said:**
> (*,)
 
The kernel module for the nvidia driver is stored in linux-restricted-modules package so sadly you can not use the nvidia-glx package. Use the run installer.
 
Quick install instructions:
 
1> Download it and make it executable
2> Backup your config file
3> Uninstall nvidia-kernel-common and all of the linux-restricted-modules
4> CTRL+ALT+F1 into a terminal. Log in and type (if applicable) sudo /etc/init.d/<your display manager> stop and ctrl+alt+f1 if usplash appears.
5> As root and you type CC=gcc-4.0 && export CC
6> Run the run!
 
(this guide has been based upon a previoulsy written guide. credit is given to whoever made that one)

---

