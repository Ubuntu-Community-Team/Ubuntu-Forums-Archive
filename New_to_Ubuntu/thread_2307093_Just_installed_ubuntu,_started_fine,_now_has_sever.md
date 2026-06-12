---
title: "Just installed ubuntu, started fine, now has severe graphical glitch and freezes"
date: 2015-12-21
forum: New to Ubuntu
---

### Post by Breanna on 2015-12-21
Hi all, I'm very new to ubuntu and I'm eager to learn a lot but currently I'm having some issues that I have no idea on how to solve.

I used Unetbootin to get a ubuntu dual boot running on an old Vista desktop I have. Initially, everything was fine, the OS installed with no problem and I got connected to the internet and had images displaying perfectly. I was so excited to see my new OS that I got OS-happy and upgraded my Windows 8 laptop to Windows 10 immedately. In doing so, the desktop was unattended for some time and eventually fell asleep. When I shook the mouse to wake it up, there was some login lock screen. While the mouse was still working, the keyboard suddenly wasn't working. I couldn't log back in. I mashed all kinds of keys hoping to bring up some new menu, but nothing worked. Out of frustration, I just held the power button down.

Once the PC booted back up, I got onto ubuntu again, and it started working just fine. Working my way from bottom to top,  started clicking some icons on the left bar, to get a feel for the new OS. At some point I clicked I think "System" or "System and Settings" (sorry, very very very new, don't yet know what everything is called) and got a weird graphical glitch. The screen became extremely distorted and the whole system became unresponsive. I entered in a wide variety of key combinations and I found online, but it appeared to have completely freezed. I took a photo of it with my phone, you can see it here (warning: large image file): [http://i.imgur.com/YaJeEq0.jpg](http://i.imgur.com/YaJeEq0.jpg) . Again, I got feed up and held the power down.

I booted ubuntu up one more time, and this time I stated clicking random icons on the left bar going top to bottom. I clicked on some file navigator folder and it opened fine, but I noticed some lag. The icons highlighted when you moused over them, but the highlights weren't moving as fast as my cursor. Soon, the cursor itself also started to lag. Then the screen flashed to this beautiful screen (warning: large image file): [http://i.imgur.com/hrvSsx2.jpg](http://i.imgur.com/hrvSsx2.jpg) and the system was unresponsive again.

Again, hard power down. Finally, just booted back up to Vista. First it ran CHKDSK for ~10 minutes and reset itself (this was my first time going to vista since installing ubuntu), but then I was able to get on. Now here I am!

I'm really super new to linux, I'm guessing this is probably a video card driver issue, but I'm not sure how to fix that. I read somewhere that you have to go to system to fix it, but I can't get to system! I know my way around windows very well, but I really want to delve into linux if I can figure out how to get it to work. Here's the specs I have:

Ubuntu 14.04.3 LTS 32 bit
HP Slimline s3700y desktop
AMD Athlon 64 X2 Dual Core Processor 5000+ 2.60GHz
3GB RAM
Nvidia GeForce 6150SE nForce 430


Thanks!

---

### Post by mörgæs on 2015-12-22
Hi, welcome to the fora.

The Nvidia 6150 and similar graphic cards are a frequent guest here. The classical solution is a fresh install of X/Lubuntu 15.10 in which you accept closed-source drivers first time they are offered.

---

### Post by Bucky Ball on 2015-12-22
Welcome. Just throwing this in: a hard shutdown is not good for your machine, can result in lost data and damaged hard drive. If it locks up again, try control+alt+F1. That should get you to CLI where you can login and then issue:

```
sudo reboot -h now
```

or, to shutdown:

```
sudo shutdown -h now
```

In the CLI or terminal you should do an update:

```
sudo apt-get update
sudo apt-get upgrade
```

... then, if you can, check 'Additional Drivers'. 

@mörgæs: the trusty 'nomodeset' doesn't work with this card???

---

### Post by mörgæs on 2015-12-22
> **Bucky Ball said:**
> 
@mörgæs: the trusty 'nomodeset' doesn't work with this card???

It could work more or less, but I wouldn't run Ubuntu on a 6150 to begin with. Even when it was new it was low performance. 

Drivers have improved over the latest iterations of Buntu so I suggest that original poster takes advantage of this.

Breanna, if you are ready for some research you could try both solutions and compare.

---

