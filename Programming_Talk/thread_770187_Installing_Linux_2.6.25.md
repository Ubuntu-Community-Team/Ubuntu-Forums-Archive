---
title: "Installing Linux 2.6.25"
date: 2008-04-27
forum: Programming Talk
---

### Post by ibuclaw on 2008-04-27
Hi all, I've gone off on an expedition and have compiled the new linux 2.6.25 kernel for myself.

I've done all the right steps (I hope)
```

make mrproper
make menuconfig
# setup some settings saved config file
make all
make deb-pkg
cd ../
dpkg -i linux-2.6.25-1.deb

```
Now, as far as I can tell that has done everything but make a new line in my boot menu.lst file.

This is where I'd like a little push in the right direction (just to be sure)
Shall I create an identical copy of the ubuntu line, but change vmlinuz-2.6.24 for 2.6.25??
Or is a bespoke line needed?


Regards
Iain

---

### Post by ibuclaw on 2008-04-28
OK! I found a book called Linux in a Nutshell, that helped me a great deal.

Now I'm almost there in finishing compiling my own kernel!

OK, first I hit a stump:
```
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,17)**
```
root (8,17) ??? Weird.

So I went back to the menuconfig and tinkered a bit (basically, making sure that nothing I didn't need was enabled, (ie: floppy disk, etc). and also double checked that all support for the ext3 filesystem was enabled too).
Rebuilt and installed it. And changed my grub boot menu list from:
```

title		Ubuntu 8.04, kernel 2.6.25-1
root		(hd1,0)
kernel		/boot/vmlinuz

```
To...
```

title		Ubuntu 8.04, kernel 2.6.25-1
root		(hd1,0)
kernel		/boot/vmlinuz root=UUID=cf35faa4-28fe-4f42-8e19-1167bb664d80 ro

```

And now when I boot up. It now says this:
```
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(2,0)**
```
I am soo close. But I'm really sure what to do now.

Can anyone help me?
Where is the best place to get answers from kernel know-it-alls?

Regards
Iain

---

### Post by tseliot on 2008-04-28
Read [this guide]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by ibuclaw on 2008-04-28
Hey, thanks.

I've solved it now.

Turned out to be (what I was thinking all the time) the absence of an initrd.img does strange things.

Anyways, the make script in the link did it!

I'm just running it now, it's very slow for a 6MB kernel!:lolflag:
hmmm... some tweaking is needed here.

Might do a "make allmodconfig" then remove any nasties that I come across.

Thanks again.
Iain

---

