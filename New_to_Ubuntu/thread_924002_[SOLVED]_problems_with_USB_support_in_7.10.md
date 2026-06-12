---
title: "[SOLVED] problems with USB support in 7.10"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by JonathanAppleseed on 2008-09-19
Hi there, first post.

I got Xubuntu 7.10 Gutsy Gibon up and running on an old iBook G3 366. It took a while, but it's on here.

The system is very efficient at recognizing my AirPort card and connecting to the network, but I can't for the life of me get my USB devices to be recognized. I've read all over the net and none of the suggestions are applicable.

I'm trying to use two different devices.

One is a mass storage device:
SanDisk 4GB U3 Cruzer Micro

The other is an audio voice recorder:
Olympus VR-4100PC

I've heard of people getting both of these to work with 7.10. But the only feedback I get from my system is that when I plug in the U3 drive the light flashes on for a second and then off. Usually it would remain on as long as its connected. Anyone got any help?

---

### Post by JonathanAppleseed on 2008-09-19
There is an update on this post.

As far as I can tell, what I did was run

```
sudo update-initramfs -u
```

to fix a known G3 boot problem. And then I noticed that the USB drive that I stubbornly kept plugging in hoping it would connect, just lit up. Now it remains lit while its in. When I run

```
dmesg |tail -2000
```

now I get the following error in regards to the USB device:

```
device descriptor read/64, error -62
```

Any insights into this new development?

---

### Post by JonathanAppleseed on 2008-09-27
This will be totally useless if anyone else encountered the same problem. But for some reason I was able to plug in the USB device just now and see the icon for the drive in the file manager.

---

