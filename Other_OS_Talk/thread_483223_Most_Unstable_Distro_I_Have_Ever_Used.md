---
title: "Most Unstable Distro I Have Ever Used"
date: 2007-06-24
forum: Other OS Talk
---

### Post by init1 on 2007-06-24
I am using Knoppix from a USB drive now and it is VERY unstable. Apt no longer works, and the shutdown hangs sometimes.

---

### Post by ThinkBuntu on 2007-06-24
If you're running it from a USB drive, why do you need to use APT?

Note. I almost wrote ATP, Adenosine Triphosphate...

---

### Post by init1 on 2007-06-24
It's has live persistence, so everything I install I can use on the next session.

---

### Post by LaRoza on 2007-06-25
Strange, I have used Knoppix on a flash drive for a while now, it is very stable and fast. 

What version of Knoppix are you using?

-edit I used 5.1.1

---

### Post by darkog on 2007-06-25
very strange indeed. Knoppy in UBS should work fairly well. Lots of ppl using it.

---

### Post by init1 on 2007-06-25
> **LaRoza said:**
> Strange, I have used Knoppix on a flash drive for a while now, it is very stable and fast. 

What version of Knoppix are you using?

-edit I used 5.1.1
The version on [http://www.pendrivelinux.com/2007/02/20/installing-usb-knoppix-51-using-linux/]("http://www.pendrivelinux.com/2007/02/20/installing-usb-knoppix-51-using-linux/") ,5.1.1. Maybe it won't happen on a new install. It's my only option of USB install now. Slax and puppy don't work well on my computer, but fine on others, Pendrivelinux and Ubuntu persistent live work on my computer, but not on some others. Knoppix works on all, so I guess I hope for the best.

---

### Post by init1 on 2007-06-26
I have installed again, but still have problems. When I do a ```
dpkg --install
``` I get a segmentation fault.

---

### Post by NilsE on 2007-06-26
I have used Knoppix, DSL and Ubuntu on a pen drive and had the same problem with all of them.  Installs and upgrades are hit and miss depending on what the install is trying to do.  It seems in order to run off of a pen drive you need to move binaries and folders around a little and this confuses APT etc.

I read somewhere that this is a known problem and the answer is that the pen drive should not be considered a "production" copy of Linux. It is great for portability with persistence which you can not achieve from a CD.

I gave up on the pen drive and have a copy of Ubuntu on a small "real" USB drive that I carry around.

---

### Post by init1 on 2007-07-02
> **NilsE said:**
> I have used Knoppix, DSL and Ubuntu on a pen drive and had the same problem with all of them.  Installs and upgrades are hit and miss depending on what the install is trying to do.  It seems in order to run off of a pen drive you need to move binaries and folders around a little and this confuses APT etc.

I read somewhere that this is a known problem and the answer is that the pen drive should not be considered a "production" copy of Linux. It is great for portability with persistence which you can not achieve from a CD.

I gave up on the pen drive and have a copy of Ubuntu on a small "real" USB drive that I carry around.
I guess I should expect less. I would have Ubuntu on my USB drive, but it does not work on all computers. Even with the computers that support USB boot, you can run some of the distros on them, but not all of them. Thats why I might buy another drive so that if one distro does not work on the computer I try to use it on, I can try the others.

---

### Post by Ultra Magnus on 2007-07-04
I've used knoppix from usb - infact it was the first distro that i could every get to work on my computer - It seemed stable enough to me - even using it on an old laptop with 128Mb Ram - I have ubuntu running on my new laptop but it took me a long time to get everything working (graphics card wireless etc) - Knoppix actually worked straight away!

---

### Post by init1 on 2007-07-05
> **Ultra Magnus said:**
> I've used knoppix from usb - infact it was the first distro that i could every get to work on my computer - It seemed stable enough to me - even using it on an old laptop with 128Mb Ram - I have ubuntu running on my new laptop but it took me a long time to get everything working (graphics card wireless etc) - Knoppix actually worked straight away!
Did you try to use Synaptic, apt, or dpkg? Most of the problems I had were with them, but also with shutdown occasionally.

---

