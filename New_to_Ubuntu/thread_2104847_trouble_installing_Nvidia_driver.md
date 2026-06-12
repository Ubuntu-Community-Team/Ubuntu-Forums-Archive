---
title: "trouble installing Nvidia driver"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by alukard69666 on 2013-01-14
I am using a dell precision M6500 with with a Nvidia- G92[Quadro FX 3800M] and I installed Ubuntu 12.10 64bit via flash drive. It used to have windows 7 installed(out of box)

So I have tried these steps outlined in this article:
 [Nvidia driver doesn't work in 12.10]("http://askubuntu.com/questions/202677/nvidia-driver-doesnt-work-in-12-10") 
followed by these steps:

Remove the existing driver Codes:
  sudo apt-get update  sudo 
apt-get purge nvidia-current  
sudo apt-get purge nvidia-current-updates   

Install NVIDIA driver Codes: 

  sudo apt-add-repository ppa:ubuntu-x-swat/x-updates  
sudo apt-get update  
sudo apt-get install nvidia-current 
  
Then restart the computer and run this:
  nvidia x server settings   

If you get **"nvidia: command not found"**; then run this:
  nvidia-settings 

but still to no avail, it does not work. My screen normally pops up as just what&#8217;s on the desktop and the mouse, the only way to get out of it is to either  uninstall the nvidia driver or change it back to the original graphics  driver. I do get an error that says "Plymouth unmounted" or something  like that when it loads up. If you need anymore information, please let me know and i will provide.
This is my first time ever using Ubuntu (I have 12.10 installed) and i have been
scouring the internet for a good week now, so any help would be appreciated

---

### Post by Pilot6 on 2013-01-14
It is a bug of 12.10.
You need to install headers first.

sudo apt-get install linux-headers-generic

And how you execute these commands? You need to run them one by one.

---

### Post by alukard69666 on 2013-01-14
I do have the headers installed already and I have been running the line commands one at a time

---

### Post by bogan on 2013-01-14
Hi!, **alukard69666,**

Can you boot corrctly from a LiveCd/Usb, or via Recovery mode - with or without 'nomodeset' added to the linux bootline? [press 'e' in the grub menu to get to edit mode, add 'nomodeset' after 'ro quiet splash' and press 'Ctrl+x' to boot].

Can you get to a terminal, 'Ctrl_Alt+t' or 'Alt+F2' type 'term', or a Text Terminal [tty], 'Ctrl+Alt+F1'?

If so, try:```
 sudo service lightdm stop
sudo service lightdm start
```You may need to press:'Ctrl+Alt+F7' to get back to the Gui if it does not work.

Alternatively, try: ```
sudo service lightdm stop
startx
```Which may give you some error messages that point to the cause.

Similarly check out /home/username/.xsession-errors ['Ctrl+h' to show hidden .files].

Please Post:```
 lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
apt-cache policy nvidia-current
``` Chao!, **bogan**.

---

### Post by alukard69666 on 2013-01-14
Hi **Bogan**! Thank you for responding

> Can you boot corrctly from a LiveCd/Usb, or via Recovery mode - with or  without 'nomodeset' added to the linux bootline? [press 'e' in the grub  menu to get to edit mode, add 'nomodeset' after 'ro quiet splash' and  press 'Ctrl+x' to boot

Can you get to a terminal, 'Ctrl_Alt+t' or 'Alt+F2' type 'term', or a Text Terminal [tty], 'Ctrl+Alt+F1'?Do I need nomodeset on or off? I can re-install ubuntu from my flash drive. If I do re-install it, should I re-add the nvidia drivers with the steps i mentioned above before proceeding to the steps you listed afterwards?

And yes, I can access the terminal all those ways when i have the Nvidia driver active

-Alukard

---

### Post by bogan on 2013-01-14
Hi!**,alukard69666**,

With an FX6800M nvidia card, if you need 'nomodeset' it is just that command, you do not need 'Yes' or 'No', or '=0'.

I, personally, have had a bad experience with x-swat/x-updates drivers and prefer to use the nvidia.com downloaded ones. I could better advise you if you posted the data I asked for.

If you use the service lightdm stop & start no harm will come and I have known it to cure similar problems with no need to re-install either ubuntu or the nvidia driver. I would be inclined to try it before, and, if necessary, after a re-install, with and without the nvidia drivers

Again, from personal experience, I prefer to not install the propriety nvidia driver as part of a reinstall, as since 12.04, the default nouveau driver often works OK.

Chao!, **bogan**.

---

### Post by alukard69666 on 2013-01-14
Bogan,

ok well here's the info you asked for, I had actually re-installed it right after you replied:

  	 	 	 	 	 	   :~$ sudo lspci -nnk | grep -iA3 vga 
  01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [Quadro FX 3800M] [10de:061f] (rev a2) 
 	Subsystem: Dell Device [1028:02ef] 
 	Kernel driver in use: nouveau 
 	Kernel modules: nouveau, nvidiafb 

~$ sudo /usr/lib/nux/unity_support_test -p  OpenGL vendor string:   nouveau 
 OpenGL renderer string: Gallium 0.4 on NV92 

 OpenGL version string:  3.0 Mesa 9.0 
  
 Not software rendered:    yes 
 Not blacklisted:          yes 
 GLX fbconfig:             yes 
 GLX texture from pixmap:  yes 
 GL npot or rect textures: yes 
 GL vertex program:        yes 
 GL fragment program:      yes 
 GL vertex buffer object:  yes 
 GL framebuffer object:    yes 
 GL version is 1.4+:       yes 
  
 Unity 3D supported:       yes 

:~$ sudo apt-cache policy nvidia-current 
 nvidia-current: 
   Installed: (none) 
   Candidate: 304.51.really.304.43-0ubuntu1 
   Version table: 
      304.51.really.304.43-0ubuntu1 0 
         500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages 
  



Also, where did you get the FX6800 from? cause i thought it would be FX3800 when i mentioned it in the original post

---

### Post by bogan on 2013-01-14
Hi!, **alukard69666**,

The Fx6800M was my typo.

The data just confirms things as you are using the Nouveau driver and the x-swat driver does not seem to be available according to apt-cache.

Chao!,** bogan**.

---

### Post by alukard69666 on 2013-01-15
Hey guys, I actually got it working from this post when I was looking at how to manually install the Nvidia driver

[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)

---

### Post by bogan on 2013-01-15
Hi!, **alukard69666,**

Great, glad you got it fixed.!

Please mark this thread as 'Solved'. [Thread tools menu at top ,]

Chao!, **bogan.**

---

