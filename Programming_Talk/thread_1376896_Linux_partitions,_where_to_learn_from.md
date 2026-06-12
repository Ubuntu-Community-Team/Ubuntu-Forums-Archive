---
title: "Linux partitions, where to learn from?"
date: 2010-01-09
forum: Programming Talk
---

### Post by kahumba on 2010-01-09
Hi,
What do I need to learn to know more about Linux partitions, like which ones are mounted, which ones are not, how to mount/unmount them "on the fly", and what file systems are on them.
Is it covered by some standard like LSB (if so, then where exactly?)?

For example I figured out that to create .desktop files I need to learn the XDG/freedesktop.org specs.

---

### Post by OgreProgrammer on 2010-01-09
Look up fstab, installing gparted can help too. You can mess with partitions on a usb thumb drive. 

Everything is in a tree format, with root "/" being, well, the root. All the directories like /tmp are in the primary partition. /home is often in its own partition.. like having a D drive. /swap is like windows page file. 

They are still branches attached to root, despite being in other partitions.

Things like /dev are special folders that contain fake files that point at devices. So /dev/disk will be a folder containing hard disks. You cant really do anything with those.. they are used by programs and the system. 

Two interesting ones are /dev/null and /dev/shm. /dev/null is called the bit bucket. Anything that gets written to /dev/null just disappears. Its useful when you want to fake writing to disk. 

/dev/shm is a ram disk. It takes some of your system ram and fakes a small hard drive. Its very fast to write to, but when the computer powers down, its contents are lost. I use it to cache my firefox internet files. 

You dont want to directly mess with most of the root partition though. /root, /home and /swap are always mounted. You can unmount /swap, but not the other two.. the system would crash.

If you have other partitions in the computer you can mount them.. such as the C drive for windows. Through careful use of the fstab file you can mount them at boot up.

A good beginner read of this free book.... [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) will contrast a lot of the differences between operating systems.

In the end, I dont think that partitions are a very critical topic, and you can get by just knowing a little bit. As well, most of the root system is abstracted away from you. You dont need to know what /etc does, nor go into it.

---

