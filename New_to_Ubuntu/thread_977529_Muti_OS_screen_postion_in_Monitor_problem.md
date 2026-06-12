---
title: "Muti OS screen postion in Monitor problem"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by dixcuxx on 2008-11-10
So There is a function in ubuntu to let user install ubuntu in Windows then can choose OS in boot up screen whenever computer starts. I do that, then find out that Ubuntu and windows always have different position on screen of monitor. So if I set the right postion for windows, then ubuntu would be in wrong place. Is there a way to fix that? Now I have to set the postion of screen on my monitor again whenever I switch between these two OS.

I am using a desktop with a 6 years old Sony CTR monitor.

Thanks!

---

### Post by biji on 2008-11-10
you can try adjusting monitor using xvidtune in ubuntu..

---

### Post by dixcuxx on 2008-11-10
> **biji said:**
> you can try adjusting monitor using xvidtune in ubuntu..

What is that? Do I need to download it? I didn't see something like that in Ubuntu before.

---

### Post by w4ett on 2008-11-10
You run it from the terminal.   See the tutorial: [http://www.xfree86.org/3.3.6/QuickStart6.html](http://www.xfree86.org/3.3.6/QuickStart6.html)

---

### Post by dixcuxx on 2008-11-10
> **w4ett said:**
> You run it from the terminal.   See the tutorial: [http://www.xfree86.org/3.3.6/QuickStart6.html](http://www.xfree86.org/3.3.6/QuickStart6.html)

So I can keep the screen position with xfree86...I think...

Basically I can just set the screen position for windows, then use xfree86 to set position for Ubuntu.

---

### Post by w4ett on 2008-11-10
> **dixcuxx said:**
> So I can keep the screen position with xfree86...I think...

Basically I can just set the screen position for windows, then use xfree86 to set position for Ubuntu.

Yep...Xvidtune will tweak your X configuration, and leave your windows and monitor hardware setting unchanged.

---

### Post by dixcuxx on 2008-11-10
> **w4ett said:**
> Yep...Xvidtune will tweak your X configuration, and leave your windows and monitor hardware setting unchanged.

Cool, thanks a lot!

---

### Post by dixcuxx on 2008-11-12
> **w4ett said:**
> You run it from the terminal.   See the tutorial: [http://www.xfree86.org/3.3.6/QuickStart6.html](http://www.xfree86.org/3.3.6/QuickStart6.html)

I tried it but seem like doesn't work. It keeps saying:

Sory: You have requested a mode-line That is not possible, or not supported by your hardware configuration.

My video card come with my motherboard which is around 2 years ago, a popular botherboard.

---

