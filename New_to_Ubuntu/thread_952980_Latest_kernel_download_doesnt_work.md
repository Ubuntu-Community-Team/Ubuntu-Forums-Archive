---
title: "Latest kernel download doesnt work"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by mastergunner on 2008-10-19
Guys I cannot boot up with the latest .21 kernel. I have a nvidia 8500GT video card and had such an issue trying to get to work but finally did in .19 so what is wrong with the latest kernel?

---

### Post by Pro-reason on 2008-10-19
The new kernel is probably fine, but your video card drivers are configured for the old kernel.  Try booting into the new kernel, getting to a TTY terminal (the graphical interface won't start), and running “sudo envyng -t” from there.

---

### Post by mastergunner on 2008-10-20
Thanks for the answer but I am not running Envy. How do you get to a terminal if you cannot get into the GUI?

---

### Post by mastergunner on 2008-10-20
Can anyone help me figure this out. I guess I need to do something with my video driver to make the new kernel work. Can someone tell me exactly how to do this since with the new kernel it doesnt even boot into the GUI? Thanks.

---

### Post by Pro-reason on 2008-10-20
I can't see your screen, but I imagine that the computer booted up correctly apart from being unable to start the X window system.  In that case, you should be left at a text console, or you can access a text console by holding Ctrl+Alt and hitting any key from F1 to F6.

You can then log in, and install software with “sudo apt-get install”, and perform other operations.

---

### Post by mastergunner on 2008-10-22
Not it seems to stop during boot. I mean I see a bunch of cmds that are loading and then stops. It probably is the driver but havent tried to see if I could get to a text console.

---

### Post by mastergunner on 2008-10-27
Can anyone help me???????

---

