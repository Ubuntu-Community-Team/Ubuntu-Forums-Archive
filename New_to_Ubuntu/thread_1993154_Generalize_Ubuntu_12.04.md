---
title: "Generalize Ubuntu 12.04?"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by ldewittleedy on 2012-06-01
I know with windows you can use sysprep to generalize an master image so that you can install it on any computer with any hardware.

 I want to be able to do this with Ubuntu 12.04. I have the master all configured how i want it to be, now i want to deploy it to 5 more pc's. Well i tryed just putting the hard drive i configured ubuntu on in another pc and it said no boot device.


Thanks for your time.

---

### Post by MG&amp;TL on 2012-06-01
[http://www.remastersys.com/]("http://www.remastersys.com/")

is, I think what you're looking for. It worked beautifully when I tried it.

---

### Post by mastablasta on 2012-06-01
either that, or you can also use one of the cloning options (such as clonezilla, or redobackup)

remastersys will make a new OS install CD i believe with your settings.

---

### Post by ldewittleedy on 2012-06-04
I have Redobackup and clonezilla, but i dont think that they "generalize" the image so that it takes the hardware settings and such out so that i can make an image of one machine and put it on another one.

---

### Post by cortman on 2012-06-04
> **ldewittleedy said:**
> I have Redobackup and clonezilla, but i dont think that they "generalize" the image so that it takes the hardware settings and such out so that i can make an image of one machine and put it on another one.

How much "hardware settings" have you configured? If you're worried about drivers, etc., most of what you'll use is built into the Linux kernel, which will stay the same from installation to installation. Unless, of course, you're using a custom kernel or Gentoo.

---

### Post by ldewittleedy on 2012-06-04
No custom kernel installed "as-is" ubuntu 12.04. INstalled all the updates and then the nvidia graphics card. Its funny because i can take the HD out and put it in a HP machine and it works fine boots up no problems. But when i try to put the HD inside a dell precision 690 or 490 tells me no boot device. I have 1 690s and 5 490s. Its really funny because i installed on a dell optiplex 745. So its weird it wont boot on the precisions. The only reason i want to "generalize" the linux image is to put it on these precisions i just bought. Otherwise i would'nt be needing to use the Remastersys backup tool

---

### Post by gordintoronto on 2012-06-04
A "generalized" Linux does not include Nvidia drivers.

---

### Post by ldewittleedy on 2012-06-05
Correct.

---

