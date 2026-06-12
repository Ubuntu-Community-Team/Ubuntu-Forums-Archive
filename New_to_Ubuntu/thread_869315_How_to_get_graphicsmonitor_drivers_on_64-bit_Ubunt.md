---
title: "How to get graphics/monitor drivers on 64-bit Ubuntu?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-07-24
I completed my first desktop build yesterday, and just got it connected to the internet.  I've been using 32-bit Ubuntu on my laptop for months, this desktop is my first time using 64-bit.

I was hoping that once I got connected, monitor/graphics card drivers would automatically show up in System > Admin > Hardware Drivers, but no such luck :(.  Since I never had to do anything driver related before, I don't know where to begin.  My graphics card is an XFX GeForce 9800 (NVidia chipset) ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814150292](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150292)) and my monitor is an HP w2207 ([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3658625&CatId=2775](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3658625&CatId=2775)).  I have a driver disk for the video card but I think it's only for Windows.

Desktop effects can not be enabled, and my max screen resolution is 800 x 600, which is pretty bad on a 22" monitor.  Everything is gigantic:lolflag:.

Thanks in advance.

---

### Post by ptn107 on 2008-07-24
Make sure nvidia-glx-new and nvidia-kernel-common are installed.  If not install them.

---

### Post by ConMan318 on 2008-07-24
K, I install those.  I am trying to follow these instructions: [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)

but when I run the command it says:
```

  ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.

```

I have tried hitting Ctrl+Alt+F1 to enter a command line and stop x server, but O get the same error.

---

### Post by BGFG on 2008-07-24
System>>Administration>>Hardware drivers
to activate the nvidia drivers. Do you see them there ?
You shouldn't really have to use the terminal...
i have a 64bit system also :)

---

### Post by ConMan318 on 2008-07-24
I tried that, it's completely empty.

---

### Post by ptn107 on 2008-07-24
If your using the Ubuntu restricted drivers (nvidia-glx-new) you should not use the drivers from the Nvidia website.  Use one or the other.  After you install nvidia-glx-new, check your System -> Administration -> Hardware Drivers applet to see if they appear.

---

### Post by ConMan318 on 2008-07-24
I have done that, the System > Admin > Hardware Drivers section is still empty.

---

### Post by BGFG on 2008-07-24
Ok, These are my packages:

xserver-xorg-video-nv
nvidia-settings
nvidia-kernel-common
nvidia-glx-new

Ensure that you have these installed through synaptic. Hope this helps.

---

### Post by ConMan318 on 2008-07-24
All of those but the first one said they were already installed, and I installed the first one.  'Hardware Drivers' is still empty.

---

### Post by OldTimeTech on 2008-07-24
If nothing else try reading this link and using some of the advice and links posted in it.

[http://ubuntuforums.org/showthread.php?t=837653&highlight=setting+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=837653&highlight=setting+nvidia+drivers)

---

### Post by BGFG on 2008-07-24
TRy ctrl+alt+backspace and restart x.

---

### Post by ConMan318 on 2008-07-24
Alright, well everything works now.  I used Envy, and it didn't auto-detect the card, which must have been the problem for everything I tried previously.  I forced it to install the driver I thought was right and it worked.  Thanks to everyone for their help.

---

