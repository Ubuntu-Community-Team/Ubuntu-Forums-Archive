---
title: "Boot into other OS from Xfce menu or bash command??"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by n3mmr on 2012-05-21
I'd really like to be able to boot straight into "the other OS" from a command line under Ubuntu in a dualboot setup.

I e I'd like to be able to say:

reboot vista

and get the confirm request:

OS matching Vista: "Windows Vista (loader sda2)". Start up that OS?

And answering Y, get Vista booted up....

Even better would be if the "Reboot" panel menu choice behind one's login name could offer a choice of other bootable systems for clicking.

So one could say "reboot into Vista" or "Reboot into Solaris" from Ubuntu, and then go grab a coffee, or talk to the neighbour, or pat the cat, and come back 15 mins later to find the other OS waiting.

 Is this even possible?

---

### Post by Cheesemill on 2012-05-21
You can use the grub-reboot command to select the default OS for the next boot only. For example:
```
sudo grub-reboot 3
sudo shutdown now -r
```
Will restart the machine and boot from OS 3 in the grub menu.

---

### Post by black veils on 2012-05-21
maybe you could create a *launcher*  for the commands

```
sudo grub-reboot 3 && sudo shutdown now -r
```

then a normal icon could be clicked, like any other application, to execute those commands.


[SIZE=3]**?**[/SIZE]

---

