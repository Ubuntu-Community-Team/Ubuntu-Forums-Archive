---
title: "I can't see my desktop!!"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Burro Adelante on 2008-10-23
Hi,
I enter my username and password and then nothing happens but an orange screen with the cursor. The cursor moves but nothing happens! I can't do anything so I have to turn off the laptop.
It seems that the OP is running but the desktop is not there.

Can anybody help me with this?

---

### Post by tanha on 2008-10-24
> **Burro Adelante said:**
> Hi,
I enter my username and password and then nothing happens but an orange screen with the cursor. The cursor moves but nothing happens! I can't do anything so I have to turn off the laptop.
It seems that the OP is running but the desktop is not there.

Can anybody help me with this?

Have you ever seen the desktop? Is this a new problem?

---

### Post by bpowell2005 on 2008-10-24
> **Burro Adelante said:**
> Hi,
I enter my username and password and then nothing happens but an orange screen with the cursor. The cursor moves but nothing happens! I can't do anything so I have to turn off the laptop.
It seems that the OP is running but the desktop is not there.

Can anybody help me with this?

I had something like this happen when I was playing around with monitor resolution settings. I ended up having to reboot, hit "Esc" when grub was loading, and selecting the "Recovery mode" kernel and then reconfiguring the Xserver. For what it's worth, that's one solution if this problem came up after messing around with resolution or display settings.

---

### Post by bumanie on 2008-10-25
Hit ctrl-alt-F1. This will stop xserver and take you to console mode. Type > sudo apt-get install ubuntu-desktop, enter password and once the operation is finished, hit ctrl-alt-F7 to restart x-server.

---

### Post by Burro Adelante on 2008-10-29
I tried apt-get install ubuntu-desktop
then it said
you must manually run 'dpkg --configure -a'
I run that line and says 'requested operation requires superuser priviledge'

So i gess I don't have them...

What do you think?

---

### Post by whitethorn on 2008-10-29
You have to run it with superuser priviledge ->  sudo before the command

```
sudo dpkg --configure -a
```

---

