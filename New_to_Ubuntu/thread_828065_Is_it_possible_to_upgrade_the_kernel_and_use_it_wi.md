---
title: "Is it possible to upgrade the kernel and use it without restarting?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by legolas_w on 2008-06-13
I heard that some one said we can upgrade from a version of linux to another version and we do not need to restart the computer.
I thought when we upgrade the kernel we need to restart the computer in order to make it use the new kernel, am i right?

thanks.

---

### Post by aktiwers on 2008-06-13
I would say so. I have no idea how you would do it without reboot.. but I could be wrong.

---

### Post by Gannon8 on 2008-06-13
I doubt that. The kernel is the heart of the os (right?) and you can't kill it. The only way to really "kill" the kernel is by restarting.

---

### Post by sports fan Matt on 2008-06-13
AFAIK, thinking logically, it would have to be kicked into gear id think and it would be hard before a restart id imagine

---

### Post by raul_ on 2008-06-13
I don't think so. the kernel is a big ./a.out (program running) and everything else runs on top of it, so to make use of a new kernel you have to run the big new ./a.out and run everything on top of it again

---

### Post by philinux on 2008-06-13
When your up and running all the modules necessary have been loaded into the kernel dynamically. So if a new kernel come along you have to reboot in order for the modules to be reloaded. 

In contrast you can load or replace running modules into the kernel without rebooting.

---

### Post by sdennie on 2008-06-13
Just to add to this, you also don't need to restart immediately.  After a kernel upgrade, (in fact, after about any upgrade), the system should still be perfectly stable so, it's reasonable to save the reboot for a more convenient time.

---

### Post by CodeDragon on 2008-06-13
It is possible, but tedious and touchy and only performed by Linux gurus who are obsessed with their uptime.  I'm not one of those kinds of people by a long shot, but I think it was explained to me as loading the new kernel as a module, transferring control, and killing the old kernel.  If you ask me, I'm perfectly happy rebooting after a kernel upgrade.

---

### Post by Arthur Archnix on 2008-06-13
Me + the Google Machine = [Steaming hot cup of Answer]("http://www.howtoforge.com/forums/showthread.php?t=21673")

---

### Post by crjackson on 2008-06-13
> **Arthur Archnix said:**
> Me + the Google Machine = [Steaming hot cup of Answer]("http://www.howtoforge.com/forums/showthread.php?t=21673")

It would seem you can do damn near anything in Linux.  I would have never bet on this one...

---

### Post by crjackson on 2008-06-13
> **Arthur Archnix said:**
> Me + the Google Machine = [Steaming hot cup of Answer]("http://www.howtoforge.com/forums/showthread.php?t=21673")

It would seem you can do damn near anything in Linux.  I would have never bet on this one...

Good find Arthur...

---

### Post by Lostincyberspace on 2008-06-13
There is talk about integrating this function into the kernel itself they would make a copy of the processes that are being changed and then starting it after the changes are done it is quite controversial though not many hardcore devs are for it.

---

### Post by ukripper on 2008-06-13
> **philinux said:**
> When your up and running all the modules necessary have been loaded into the kernel dynamically. So if a new kernel come along you have to reboot in order for the modules to be reloaded. 

In contrast you can load or replace running modules into the kernel without rebooting.

I second that...

---

