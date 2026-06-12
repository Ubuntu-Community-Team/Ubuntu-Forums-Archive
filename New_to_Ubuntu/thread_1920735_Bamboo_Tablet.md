---
title: "Bamboo Tablet?"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by AutumnFox on 2012-02-05
So, I really need some help to figure out how to get my Bamboo Create tablet to work on Ubuntu 11.10. Because it apparently doesn't get recognized upon plugging the USB in? At least that's what I've read while I was looking around.
I'm assuming the CD that came with it for installation probably won't get me anywhere.

I've been trying to look up any tutorials/guides that could help, but half of it didn't really make a lot of sense, so I haven't gotten very far in figuring this out. As a beginner with quite a few things regarding this OS, any help would be appreciated. But you might need to be quite specific in step-by-step instructions or something for me to understand.

---

### Post by Favux on 2012-02-05
Hi AutumnFox,

Welcome to Ubuntu Forums!

> I really need some help to figure out how to get my Bamboo Create tablet to work on Ubuntu 11.10. Because it apparently doesn't get recognized upon plugging the USB in? At least that's what I've read while I was looking around.
I'm assuming the CD that came with it for installation probably won't get me anywhere.
That's right.  The Create is one of the new third generation BambooPTs and isn't supported in Oneiric's 3.0 kernel.  Support for the third generation has been added to the 3.3 kernel.  However that 3.3 support has been backported to input-wacom.  Input-wacom supplies a usb kernel driver/module called wacom.ko and is used to provide support for models or features added to kernels newer then the one your current release comes with.  In other words it will essentially update your kernel's wacom.ko to the 3.3 kernel's wacom.ko.

So at a minimum you need a input-wacom wacom.ko that has your model tablet in it.  See part I. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  The steps are broken down and you just copy and paste the commands into a terminal and hit enter after each command.

That will get your tablet working in Oneiric (11.10) with Oneiric's default Wacom X driver (xf86-input-wacom-0.11.0).  However it is worth updating the xf86-input-wacom (the X driver) also, part II., because that has touch gesture improvements that came out recently.

---

### Post by AutumnFox on 2012-02-05
It worked!

That actually turned out simpler than I figured.
Thank you so much!

Everything seems to be working, now all that's left is to figure out how to get the eraser to work on GIMP. Since right now it's doing the opposite.

---

### Post by Favux on 2012-02-05
Sure.  Nice job!

In Gimp touch the eraser to the little eraser icon on the tool palette to the left so the eraser is selected.  Save that assignment.  You should be good then.

Please mark as Solved.  Use the Thread Tools above your first post.

---

### Post by AutumnFox on 2012-02-05
Ah, there we go. Now it's working.
Thanks again for helping me out.

---

