---
title: "Nothing seems to save ?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by JULEZAH on 2008-04-25
Whenever i restart the machine, ubuntu starts in low-graphics mode.
I don't know why :S
So i have to choose the monitor and graphics card again.

And then when i log in, the wireless doesn't work :S
I have to put in: "sudo modprobe ndiswraper" every time.

How can i make this automatic ?

---

### Post by spiderbatdad on 2008-04-25
edit the file /etc/modules to include ndiswrapper

In a terminal run ```
gksu gedit /etc/modules
```
anywhere in the list, add a line:

ndiswrapper

Then save the file.

That should solve the wireless. I believe you can do the same thing with your video module. For example: nvidia
Not sure on the video module.

---

### Post by JULEZAH on 2008-04-25
ok, that's a good start.

My monitor is a gateway FPD1800 and graphics card is ATI Radeon 7200


Any ideas ?

---

### Post by spiderbatdad on 2008-04-26
Did you install any graphics driver?

Take a look at dmesg run in the terminal...near the top for: "apic disabled in bios. Try using lapic."

---

### Post by JULEZAH on 2008-04-26
eh ?

No, i didn't "install" any drivers, just selected them :S

---

### Post by spiderbatdad on 2008-04-26
try running this command:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by JULEZAH on 2008-04-26
Well, ok.

but then i'm back where i started.

The colors are all screwed.

---

