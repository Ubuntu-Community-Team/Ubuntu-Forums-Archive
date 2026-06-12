---
title: "Advice for re-sizing/migrating my WUBI install?"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by salmonberger on 2012-10-07
Hello all,

Apologies in advance for my ineptitude. Absolute newbie here. 

Here's my problem:

I bought a new laptop in Japan. Windows 7 installed, but in Japanese only. Perfect opportunity to finally give Linux a try. Love it. Love Ubuntu. Used the WUBI installer.

I would like to transfer a large volume of photos and music from my old laptop to my new one. However, the partition in which Ubuntu is installed is only 24 GB, and I don't have room. The Windows OS partition is using 75 GB (according to the partition editor I installed).

Although I am still new to Ubuntu, I would be happy to discard Windows unless there's a really good reason to keep it around. Especially since I cannot even boot Windows anymore (How did I screw that up?) "error: Invalid EFI file path."

So really, there's two problems - how do I enlarge my Ubuntu partition without being able to unmount it, and how do I boot Windows again from the boot screen?

I have been researching how to do this myself ([https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)), but the vocabulary is still a bit beyond me.

Any advice or recommendations?

Thanks a lot,
s

---

### Post by DuckHook on 2012-10-07
Can't really help without more complete system info. Example: how big is your disk? If there is excess disk space, then you can create a data partition that can be made accessible to both Ubuntu and Windows (assuming that you can get Windows working again, or even want it anymore).

BTW, if you are set on using Ubuntu over Windows, then I highly recommend a clean install of Ubuntu on its own partition. WUBI is (in my opinion) a very problematic kludge that is just asking for trouble. If you ever experience a hard crash, you may not be able to get either Windows or Ubuntu up and running again because, under WUBI, Ubuntu requires Windows to load first.

Please post complete system stats.

---

### Post by salmonberger on 2012-10-07
Hi DH, thanks.

Does this screenshot help?

I believe I am set on Ubuntu over Windows - can you point me in the right direction for info on how to do a clean install? I will start poking around myself. Is that different from a migration?

Cheers,
s

---

### Post by DuckHook on 2012-10-07
Your HD is 115 GB so you are maxed out on hard disk. Therefore, no way to easily expand room for Ubuntu without stealing it from Windows, which involves risky stuff like moving and resizing partitions. I don't even want to think about doing such a thing with your current WUBI install.

Since you are set on Ubuntu over Windows, a "clean" install means hosing Windows altogether and having nothing on your laptop but Linux. Since you have already installed Ubuntu onto this laptop and are presumably happy with it, then we can safely assume that everything works and you will be happy with a 100% dedicated Ubuntu system. You must be absolutely sure about this as there is no going back. If so, then a clean install is a very simple matter of:

1. Downloading the ISO image of Ubuntu 12.04 and burning it onto a CD,
2. Booting up your laptop using the Ubuntu CD,
3. Following the instructions on boot-up, choosing "use the full disk" (*without* preserving existing OSes).

It's that simple.

The ISO download is available on the Ubuntu home page.

Good luck! And welcome to the Linux/Ubuntu community.

---

