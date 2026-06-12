---
title: "Boot sequence"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Wils on 2008-08-03
Hi guys, having now taken the plunge and installed Ubuntu and liking it. I would like to change the boot sequence to Xp first with the option to boot to Ubuntu by using the up and down arrows. Plain simple English would be great, or a link. Many thanks in advance for the help.

wils

---

### Post by DJH10 on 2008-08-03
Did you install Ubuntu along side XP,i.e a dual boot system?If you did you should get the option to load into either at the boot up screen.

---

### Post by alzie on 2008-08-03
I'd recommend using Startup Manager.

You can find it in System>Administration>Synaptic Package Manager.
It will Prompt for your password.

Search for Startup Manager and click to install.

You find the program installed under System>Administration

Then use Default Operating System to select your preference.

I hope this helps

---

### Post by mevets on 2008-08-03
You need to edit your /boot/grub/menu.lst
```

sudo gedit /boot/grub/menu.lst

```
Look for a line that says 'default 0'. This number corresponds to which entry you would liek to be auto-selected. It starts counting from 0 so the first item is 0, the second item is 1, etc. You need to reboot and see how far down XP is and rewrite the line 'default 0' accordingly.

---

### Post by Wils on 2008-08-03
> **DJH10 said:**
> Did you install Ubuntu along side XP,i.e a dual boot system?If you did you should get the option to load into either at the boot up screen.

Thanks DJH10 I dual booted to start with to allow other to run windows.

---

### Post by Wils on 2008-08-03
> **mevets said:**
> You need to edit your /boot/grub/menu.lst
```

sudo gedit /boot/grub/menu.lst

```
Look for a line that says 'default 0'. This number corresponds to which entry you would liek to be auto-selected. It starts counting from 0 so the first item is 0, the second item is 1, etc. You need to reboot and see how far down XP is and rewrite the line 'default 0' accordingly.


Cheers mevets, Will look in to this may need an idiots guide to help.

---

### Post by Wils on 2008-08-03
> **alzie said:**
> I'd recommend using Startup Manager.

You can find it in System>Administration>Synaptic Package Manager.
It will Prompt for your password.

Search for Startup Manager and click to install.

You find the program installed under System>Administration

Then use Default Operating System to select your preference.

I hope this helps

Cheers alzie sound like this will work for me. Will give a go tommorow.

---

### Post by Wils on 2008-08-04
> **alzie said:**
> I'd recommend using Startup Manager.

You can find it in System>Administration>Synaptic Package Manager.
It will Prompt for your password.

Search for Startup Manager and click to install.

You find the program installed under System>Administration

Then use Default Operating System to select your preference.

I hope this helps

Big thanks to alzie.

Startup manager was easy and did the job,maybe next time I will try the other routes

THANKS TO ALL

WILS

---

