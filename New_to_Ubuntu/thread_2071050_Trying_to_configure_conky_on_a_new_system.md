---
title: "Trying to configure conky on a new system"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by WanderingOak on 2012-10-14
I have a new install of Ubuntu desktop on an old IBM T43 laptop, and I am trying to get conky up and running. I've copied one of the sample .conkyrc files from the conky sourceforge page and pasted it into ~/.conkyrc . However, I've rebooted conky several times (killall -SIGUSR1 conky) and it still uses the default configuration in: /etc/conky/conky.conf . I figured maybe I needed to restart X11, so I rebooted. Conky didn't start on boot, even though I added it to my startup applications, and running conky in terminal resulted in the following error messages:


 Conky: /home/antony/.conkyrc: 29: no such configuration: 'on_bottom' 
 Conky: /home/antony/.conkyrc: 50: no such configuration: 'border_margin' 
 Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none. 
 Conky: unknown variable freq_dyn_g 
 Conky: statfs '/mnt/storage/': No such file or directory 
 Conky: statfs '/mnt/windows': No such file or directory 
 Conky: forked to background, pid is 2112 
 antony@antony-ThinkPad-T43:~$  
 Conky: desktop window (1600095) is subwindow of root window (14c) 
 Conky: drawing to desktop window 
 Conky: drawing to double buffer 
 Conky: statfs '/mnt/windows': No such file or directory 
 Conky: statfs '/mnt/storage/': No such file or directory 
 Conky: /proc/i8k doesn't exist! use insmod to make sure the kernel driver is loaded... 
 
I'm new to Ubuntu and conky, but I thought I knew enough about Linux in general to figure this out on my own.
 

 I've attached my .conkyrc file.

---

### Post by critin on 2012-10-14
Have you seen this sticky?

[http://ubuntuforums.org/showthread.php?t=1280453&highlight=conky%2C+lua](http://ubuntuforums.org/showthread.php?t=1280453&highlight=conky%2C+lua)

---

### Post by philinux on 2012-10-14
> **WanderingOak said:**
> I have a new install of Ubuntu desktop on an old IBM T43 laptop, and I am trying to get conky up and running. I've copied one of the sample .conkyrc files from the conky sourceforge page and pasted it into ~/.conkyrc . However, I've rebooted conky several times (killall -SIGUSR1 conky) and it still uses the default configuration in: /etc/conky/conky.conf . I figured maybe I needed to restart X11, so I rebooted. Conky didn't start on boot, even though I added it to my startup applications, and running conky in terminal resulted in the following error messages:


 Conky: /home/antony/.conkyrc: 29: no such configuration: 'on_bottom' 
 Conky: /home/antony/.conkyrc: 50: no such configuration: 'border_margin' 
 Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none. 
 Conky: unknown variable freq_dyn_g 
 Conky: statfs '/mnt/storage/': No such file or directory 
 Conky: statfs '/mnt/windows': No such file or directory 
 Conky: forked to background, pid is 2112 
 antony@antony-ThinkPad-T43:~$  
 Conky: desktop window (1600095) is subwindow of root window (14c) 
 Conky: drawing to desktop window 
 Conky: drawing to double buffer 
 Conky: statfs '/mnt/windows': No such file or directory 
 Conky: statfs '/mnt/storage/': No such file or directory 
 Conky: /proc/i8k doesn't exist! use insmod to make sure the kernel driver is loaded... 
 
I'm new to Ubuntu and conky, but I thought I knew enough about Linux in general to figure this out on my own.
 

 I've attached my .conkyrc file.

It means conky cant start as one or more of the variables is set wrong for that machine.

Try # commenting the offending one out. for correct config see this.

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Try mine which is attached.

---

### Post by WanderingOak on 2012-10-14
> **philinux said:**
> It means conky cant start as one or more of the variables is set wrong for that machine.

Try # commenting the offending one out. for correct config see this.

[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Try mine which is attached.
Well, your config file worked, once I commented out the second CPU. Thanks for the help!

---

