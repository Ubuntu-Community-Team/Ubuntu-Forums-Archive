---
title: "Ubuntu slowness?!"
date: 2011-04-10
forum: Recurring Discussions
---

### Post by jhargis1012 on 2011-04-10
Hello!

I recently got a Toshiba nb205 netbook (Intel Atom 1.67ghz, 2gb RAM) and I've been on a quest to find the perfect Linux distro for it. It obviously has to be something sort of lightweight, or at least configurable to be so, on account of the less than powerful netbook hardware.

My first choice was Ubuntu's netbook 10.10. I had been a long time Ubuntu user, and it was the obvious first choice. It was horribly slow on my machine (I'd say about five to seven seconds to pull up a small application) I figured it was just too heavy an environment (tried it with both Unity and the old Gnome) for the nb205. Reluctantly, I decided to give Lubuntu a try. Lubuntu running Lxde is just awesome (probably less than two seconds to pull something up, plenty of things were instantaneous). It was so snappy and worked like a charm. Yet, in the end, I couldn't stick with it. It just felt... TOO light, too simple. I came across Linux Mint Debian running Xfce, a lighter-but-not-quite-overly-light desktop environment, if that makes sense. It's worked pretty well, and I thought I'd found a good compromise between performance and features.

Well, just for fun, I figured I'd give openSUSE running Gnome 3 a shot (Gnome put this configuration up on their website as a test run for anybody who was interested). I've been pretty excited about what the folks over at Gnome have been working on, and even though I figured it'd barely work on my pitiful hardware, I threw it onto a USB drive and started it up. I was SHOCKED. It works great, and it looks amazing. It was seriously at LEAST as fast as a fresh install of Ubuntu 10.10, and from the flash drive nonetheless. Anybody have any idea why this is? Is there some kind of issue my computer has with Ubuntu? Shouldn't Ubuntu 10.10 work much smoother than any distro running Gnome 3? I'd appreciate an thoughts on this.

Thanks.

---

### Post by uRock on 2011-04-10
Moved to Recurring Discussions.

---

### Post by 3rdalbum on 2011-04-11
Ubuntu Netbook 10.10 was slow because it used an unoptimised Unity interface. Ubuntu 11.04 and Gnome 3 are optimized reasonably well for speed.

---

### Post by Copper Bezel on 2011-04-11
He says he tried regular Gnome, as well.

---

### Post by NightwishFan on 2011-04-11
Well the new kernels since 2.6.35 have been very good in my experience. That might be the reason.

Also, if you are interested in a fast configurable distro try Debian.

---

### Post by jhargis1012 on 2011-04-11
Thanks for the responses.

So I thought I'd try the LTS version of Ubuntu to see if there was a speed improvement and there definitely was. I thought there might be since it's like the most stable release, which is probably what I want anyway.

This brings me another question: Does the LTS version of Ubuntu get Linux kernel updates? Or is a full fledged upgrade necessary for that?

---

### Post by NightwishFan on 2011-04-11
For supported upgrades? You only get security/bug fixes. A full upgraded is required. You can upgrade yourself but it will not be supported and your mileage may vary.

---

### Post by snowpine on 2011-04-11
> **jhargis1012 said:**
> This brings me another question: Does the LTS version of Ubuntu get Linux kernel updates? Or is a full fledged upgrade necessary for that?

All Ubuntu release (LTS or regular) get bug fixes and security patches to their kernel for the lifespan of the release. This means that a default install of Ubuntu 10.04 will always use some version of kernel 2.6.32 (but you can install a newer kernel from the PPA if you want). 

It is worth mentioning that 2.6.32 is a "long term support" kernel that is shared by Ubuntu, Debian, Red Hat, etc. and should work great for most users for many years to come. :)

I think your original mistake was choosing the netbook version of Ubuntu. Many users (including myself) have found that the netbook edition sacrifices some performance for the sake of "usability" (which of course is very subjective).

---

### Post by WinterMadness on 2011-04-11
try puppy linux, jolicloud or arch

Arch is very fast in general

---

### Post by jhargis1012 on 2011-04-11
> **snowpine said:**
> I think your original mistake was choosing the netbook version of Ubuntu.

I'm thinking the same thing. Thanks for the info on the kernel updates.

---

