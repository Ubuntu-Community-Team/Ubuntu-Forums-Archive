---
title: "run damn small linux with qemu"
date: 2006-12-13
forum: Programming Talk
---

### Post by dbbolton on 2006-12-13
see what you make of this screen shot :

---

### Post by pay on 2006-12-13
To create a disc try```
qemu-img create disk.img 4G
```or```
dd if=/dev/zero of=disk.img bs=1M count=4096

```

---

### Post by dbbolton on 2006-12-13
same error :/

---

### Post by Snargle on 2006-12-14
Maybe qemu thinks that your cdrom image is a hard drive image.

do this:

qemu -cdrom disk.img

I was able to boot an ubuntu cd this way.

---

### Post by tonyisntcreative on 2006-12-14
Don't mean to hijack but I'm having a funny issue with DSL...

I'm using this command to run it in qemu if this helps you
qemu -cdrom [my location] -boot c -m 256

It starts up under qemu with no problem.  Funny thing is, it won't run for me regularlly.  If I put it in my CD drive and start the computer up with it in, it gives me the rundown for starting up, but then it gets to a black screen (when it should be finished starting) and just stays there.  Changing VGA options didn't seem to do anything.

---

