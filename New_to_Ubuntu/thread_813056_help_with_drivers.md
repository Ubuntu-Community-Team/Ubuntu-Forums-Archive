---
title: "help with drivers"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ezio cagone on 2008-05-30
I have just started using Ubuntu; I like it a lot but as soon as I need a driver, although I am able to find and download it I have no idea how to install it unless i go through synaptic package manager. Unfortunately most drivers I require, I can only find on the net. They all have readme files saying that I have to type in so and so and do "as root" and "make file" and then "compile driver" and "make install" etc. I have absolutely no idea what is being said, am I supposed to use terminal or something? At the moment I need to install a driver for my usb camera a Microsoft Lifecam Vx1000 (sigh!); on the net I found out that I need to use the gspcav1 driver. I can't find it with synaptic package manager so I downloaded it and it's just sitting on my desktop. Can anybody help me?

---

### Post by pytheas22 on 2008-05-30
Linux tries to include as many drivers as possible in the operating system itself, so you should rarely need to install drivers.  But you're right, when you do have to install them, it's rarely a beginner-friendly process.  It's not too hard, however, once you're familiar with the procedure; it usually just involves typing "make" and "make install" at the command line, and then inserting the driver using modprobe.  The procedure can vary, however.  If you can provide a link to the place where you got the driver, I'll take a look at the readme and try to guide you through the compilation process.

Also, just to make sure that you're not accidentally making things harder than they need to be: did you already try plugging in the camera to see if the system recognizes it?  Ubuntu should be able to work with most digital cameras out of the box.

EDIT: sorry, I just realized you have a webcam, not a digital camera.  Compiling the driver should still not be a problem.

---

### Post by Sef on 2008-05-30
Moved to Absolute Beginners.

---

### Post by Sef on 2008-05-30
What version of Ubuntu are you using? (Hardy, Gutsy, other?)

Update: From an [old post]("http://ubuntuforums.org/showthread.php?t=329924"), I found about gspca-source.  It is in the repositories.

To download gspca-source follow these directions:

1) System > Administration > Software Sources
   a) Check Community Maintained Open Source Software (Universe) and Software Restricted by Copyright or    Legal Issues.  (Multiverse)
    b) Then click close.

Applications > Accessories > Terminal

Then copy and paste this code:

```
 sudo apt-get update && sudo apt-get install gspca-source 
```

Then check to see if the webcam works or not.  Please report back either way.

---

### Post by dennis69498 on 2009-04-03
Hi, can anyone help please. I had to uninstall my lifecam vx1000. When I reinstalled I cannot get the video otions to adjust settings. No one can see or hear me but I can see and not hear them.

---

### Post by pytheas22 on 2009-04-04
dennis: did you try following [these instructions]("https://lists.ubuntu.com/archives/ubuntu-users/2009-February/175983.html")?  Which version of Ubuntu are you using?

---

