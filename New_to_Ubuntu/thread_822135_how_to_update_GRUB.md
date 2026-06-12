---
title: "how to update GRUB?"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by sharks on 2008-06-07
how to update GRUB?

---

### Post by tramir on 2008-06-07
What do you want to update? grub itself or the options?

---

### Post by Prospero2006 on 2008-06-08
The configuration file is located in
/boot/grub/menu.list

Open in a text editor.

---

### Post by Unix_Slayer on 2008-06-08
or install kgrubeditor. For all you non-binary people.

---

### Post by sharks on 2008-06-08
I want to upgrade grub itself.

---

### Post by bumanie on 2008-06-08
Try this > sudo apt-get update grub

---

### Post by sharks on 2008-06-08
it says > E: The update command takes no arguments


---

### Post by bumanie on 2008-06-08
Sorry, my mistake, I think it's > sudo update-grub

---

### Post by sharks on 2008-06-08
If a newer version of GRUB is released how do i upgrade it via terminal?

---

### Post by drs305 on 2008-06-08
The update-grub command is used to generate and update the menu.lst, according to the man page.  The latest grub version in the repos is 0.97-29. 

This should upgrade installed packages, including grub:
```
sudo aptitude update
sudo aptitude upgrade
```

For updating grub **menu** items, displays, etc I strongly recommend startupmanager.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by raamee on 2009-06-09
if we enter recovery mode, there is a option to update grub. shall

i upgrade grub from this option?

---

### Post by drs305 on 2009-06-10
> **raamee said:**
> if we enter recovery mode, there is a option to update grub. shall

i upgrade grub from this option?

You can run the commands from the recovery mode, although when you state 'upgrade grub' that can mean different things. If you select "netroot" (root shell with networking) you will be able to connect to the Internet and run any of the normal update commands such as *apt-get update* and *apt-get upgrade*. Since this is a root shell, you do not need to use "sudo".

You can also run the "grub" command or "update-grub" from the root prompt if that is what you are having difficulties with.

---

### Post by Hoobes1 on 2010-01-02
I just entered 
```
sudo apt-get upgrade grub
```
and it worked perfectly fine =)

---

