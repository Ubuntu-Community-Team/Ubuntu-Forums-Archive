---
title: "USB device won't mount?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Gael33 on 2008-08-04
All of a sudden my computer refuses to mount my USB when I insert a stick.
Could somebody help me correct this error as I have some very important files on my USB device.
Here is a snap-shot of the message I received.

[IMG]http:///home/gael33/Desktop/Screenshot.png[/IMG]

I hope I've done this correctly (I'm a raw beginner).

Gael.

---

### Post by unutbu on 2008-08-04
Sometimes if a USB stick is put into a Windows machine and not unmounted cleanly, it will be left in a state which makes it hard (impossible?) for Linux to read.
If this sounds like what might have happened to you, then the solution is to go back to a Windows machine,
plug in the USB stick, then shutdown Windows. The USB will then be unmounted cleanly. (Alternatively, I believe if you click on the USB icon in the lower right corner, there should be a pop up menu item which will say something like "Make USB safe to remove". Selecting that will unmount the USB too.)

If that is not the problem, then perhaps boot Ubuntu , plug in the USB stick, and open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo fdisk -l

```

---

### Post by Gael33 on 2008-08-04
> **unutbu said:**
> Sometimes if a USB stick is put into a Windows machine and not unmounted cleanly, it will be left in a state which makes it hard (impossible?) for Linux to read.
If this sounds like what might have happened to you, then the solution is to go back to a Windows machine,
plug in the USB stick, then shutdown Windows. The USB will then be unmounted cleanly. (Alternatively, I believe if you click on the USB icon in the lower right corner, there should be a pop up menu item which will say something like "Make USB safe to remove". Selecting that will unmount the USB too.)

If that is not the problem, then perhaps boot Ubuntu , plug in the USB stick, and open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```

sudo fdisk -l

```

I'll give that first option a try ... I don't want to use fdisk as it will remove all of my work on the USB stick.
Thanks for a quick reply ... I'll let you know if I fix the problem :)

Gael.

---

### Post by unutbu on 2008-08-04
Yes, fdisk can be a dangerous program, but the command I posted will only list the hard drives -- it will not  erase anything.

If the USB stick shows up in the output of fdisk, there are command-line (um...) commands that we can suggest that may help to get the USB mounted.

---

### Post by Gael33 on 2008-08-04
> **unutbu said:**
> Yes, fdisk can be a dangerous program, but the command I posted will only list the hard drives -- it will not  erase anything.

If the USB stick shows up in the output of fdisk, there are command-line (um...) commands that we can suggest that may help to get the USB mounted.

Thank you, I'll get back to you as soon as I've tried the Windows option.

Gael.

---

### Post by AdamWood on 2008-08-04
> Yes, fdisk can be a dangerous program, but the command I posted will only list the hard drives -- it will not erase anything.

I thought it might help if I confirm that the fdisk -l command will not erase anything and unutbu hasn't given you a command that will destroy your system. :)

---

### Post by Gael33 on 2008-08-04
> **AdamWood said:**
> I thought it might help if I confirm that the fdisk -l command will not erase anything and unutbu hasn't given you a command that will destroy your system. :)

Thank you ... that's a relief :)

Gael.

---

### Post by Gael33 on 2008-08-05
Unutbu suggested that I unmount the USB device in Windows ... I did and it worked. My work is safe ... phew!
Much obliged and very grateful.
Thanks again.
Gael.

---

