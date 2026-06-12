---
title: "Grub Menu Doesnt Appeared"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by RotiHangus HC on 2013-11-08
Afternoon guys!
As today, i tried to dual-boot Windows 8 and Ubuntu 13.10 (used only 1 os that's Windows 8 before)
When i restart my laptop, it automatically boot into Ubuntu without any option or Grub menu.

Any solution guys? ;)

---

### Post by Bucky Ball on 2013-11-08
Reboot and hold down the shift key. Does that take you to the list? If Win is not on it, then boot into Ubuntu and in a terminal:

```
sudo update-grub
```

Reboot and hold down the shift key. There now?

If all this works we can then show you how to get the list to appear at boot without holding down the shift key. ;)

---

### Post by RotiHangus HC on 2013-11-08
Ermm how about if u used ubuntu as my default os? And then dual-boot with Wins 8.
Bcs no menu's show up also. Hmm

---

### Post by Bucky Ball on 2013-11-08
> **RotiHangus HC said:**
> Ermm how about if u used ubuntu as my default os? And then dual-boot with Wins 8.
Bcs no menu's show up also. Hmm

The first part I don't follow, sorry. I thought you had Ubuntu and Win8 installed on this machine, it boots directly to Ubuntu without giving you the option to choose an OS ...

Also, are you saying no grub menu shows when you hold shift at boot, it just boots to the Ubuntu login screen?

Open a terminal and issue this:

```
sudo nano /etc/default/grub
```

Find the line that says:

```
GRUB_TIMEOUT=0
```

and change to:

```
GRUB_TIMEOUT=10
```

Reboot. Now do you have a list and is Win8 on it?

---

### Post by RotiHangus HC on 2013-11-08
Thanks dude! Youre really awesome :P
Now i can boot into both OS hehehe thanks again mate!

---

### Post by newb85 on 2013-11-08
@RotiHangus HC,
Happy Ubuntu-ing.  Please mark this thread as solved by clicking "Thread Tools" at the top.

---

### Post by Bucky Ball on 2013-11-08
No probs. Great news all is now working! Enjoy your new set up, the forums and the learning curve, and don't hesitate to post new threads for any further issues/questions. ;)

---

