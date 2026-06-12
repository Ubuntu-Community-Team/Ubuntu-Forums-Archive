---
title: "Cant search any Bluetooth devices"
date: 2019-07-29
forum: New to Ubuntu
---

### Post by katateshikito on 2019-07-29
Hi! I'm new to Linux Os and I just installed ubuntu 19.04. Im using an old laptop ASUS x451MAV with [FONT=Segoe UI, &#24494;&#36575;&#27491;&#40657;&#39636;, Microsoft JhengHei, Arial, &#26032;&#32048;&#26126;&#39636;][COLOR=#333333]Intel® Bay Trail-M Dual Core Celeron N2815 Processor and built in wifi and bluetooth. I totally wiped out Windows OS but Bluetooth back the was working fine. Now that im running  ubuntu 19.04 Bluetooth cant just find any devices. Please help. [/COLOR][/FONT]

---

### Post by TheFu on 2019-07-29
Welcome to the forums.

If you are new to Linux, please don't run non-LTS releases like 19.04 unless there is a really good reason. Do you really want to install an entire new OS every 6 months?  That's what using any release that isn't LTS requires.  90% of Ubuntu users should be running 18.04 still.

---

### Post by katateshikito on 2019-07-30
so how can I install 18.04 LTS from 19.04?  I dont have windows os so I wont be able to make a bootable 18.04  usb

---

### Post by oldrocker99 on 2019-07-30
Oh, there's a way to make a bootable USB. Do this:```
sudo apt install etcher-electron
```
Etcher is a superior USB-burnng app. Use it to do the job, and you'll be all set.

---

### Post by katateshikito on 2019-07-30
Hope my Bluetooth works after downgrading> I will update tomorrow once I got home. Thanks for the help.

---

### Post by TheFu on 2019-07-30
There are at least 15 different ways, so don't feel like you HAVE to use Etcher.  On a limited system, Etcher can feel bloated.  The Ubuntu guide for this: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

Lots of people like Etcher, so it is probably a pretty nice tool. I tried it once - think it used some funky packaging that rubbed me the wrong way. I can be sensitive in that way. ;(

I use **dd** myself, to make a bootable flash drive from the ISO.

---

### Post by katateshikito on 2019-07-30
This is way more easier. Dont need to download etcher anymore.

---

### Post by katateshikito on 2019-07-30
> **TheFu said:**
> There are at least 15 different ways, so don't feel like you HAVE to use Etcher.  On a limited system, Etcher can feel bloated.  The Ubuntu guide for this: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

Lots of people like Etcher, so it is probably a pretty nice tool. I tried it once - think it used some funky packaging that rubbed me the wrong way. I can be sensitive in that way. ;(

I use **dd** myself, to make a bootable flash drive from the ISO.



whats DD?

---

### Post by katateshikito on 2019-08-01
So I tried installing the 18.04 LTS but it just doesn't work on my LAPTOP . I dont know what's the problem but its not installing but it just freezes on blank screen after I  selectED install ubuntu. I just installed  19.04 version back. I need a working PC and I just cant install 18.04. Guess I just need to install a new interim release once 19.04 support ends.

---

### Post by TheFu on 2019-08-01
Some PCs, usually laptops, need some boot options to work.  [https://askubuntu.com/questions/1085807/black-screen-after-installation-of-ubuntu-18-04](https://askubuntu.com/questions/1085807/black-screen-after-installation-of-ubuntu-18-04)  Using google with terms like:
**  ASUS x451MAV ubuntu blank screen**
should help find solutions.

I have an Asus laptop with a newer CPU. It doesn't need any special options to boot.

But only you can decide if any of this is worth the effort.  The next LTS will be 20.04 - next April.  I usually wait until at least June to install. Let others find the big issues before I bother.

---

### Post by oldrocker99 on 2019-08-02
DD will work, but it is **NOT** for beginners, any more than rsync is.

---

### Post by TheFu on 2019-09-12
btw, 
Turns out that bluetooth hasn't ever been safe to use: [https://www.howtogeek.com/438712/could-your-bluetooth-devices-be-hacked-in-2019/](https://www.howtogeek.com/438712/could-your-bluetooth-devices-be-hacked-in-2019/)> 
There&#8217;s ample evidence that Bluetooth is about as secure as a padlock sculpted from fusilli pasta.
This isn't about bluetooth on Linux, but all bluetooth.

---

