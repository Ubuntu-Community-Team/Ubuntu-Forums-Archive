---
title: "error: unknown filesystem . grab rescue?"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by tom32 on 2013-09-05
Hello,

I bought a laptop without an operating system, and I installed Ubuntu on it. I am now trying to return the laptop to the store, but I assume I can't return it with Ubuntu installed. To remove Ubuntu, I did the following command:  [COLOR=#000000][FONT=Ubuntu Mono]sudo shred -v /dev/sdb -z[/FONT][/COLOR]
 
Now whenever I start the computer, I get the error: unknown filesystem grub rescue.

Ideally, I would like to wipe this error, so it doesn't appear.

Would anyone know how to do this?

---

### Post by Kirk Schnable on 2013-09-05
If you want to return the computer with nothing on the hard drive, I would recommend you use DBAN to wipe the drive.
[http://www.dban.org/download](http://www.dban.org/download)

You can download a CD from their website, burn it, boot to it, and wipe your drive very easily.

---

### Post by Jonathan Precise on 2013-09-05
> **tom32 said:**
> Hello,

I bought a laptop without an operating system, and I installed Ubuntu on it. I am now trying to return the laptop to the store, but I assume I can't return it with Ubuntu installed. To remove Ubuntu, I did the following command:  [COLOR=#000000][FONT=Ubuntu Mono]sudo shred -v /dev/sdb -z[/FONT][/COLOR]
 
Now whenever I start the computer, I get the error: unknown filesystem grub rescue.

Ideally, I would like to wipe this error, so it doesn't appear.

Would anyone know how to do this?

I recommend you use [GParted]("http://gparted.sourceforge.net") to make a new partition table. Download and burn the Live CD. Create a GPT partition table. Note: to undo this download testdisk to restore everything.

---

