---
title: "autoloading when computer starts up"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-06-26
i am curious if anyone knows if there is a way to have ubuntu load automatically from  when i  turn on my computer instead of having to  choose a specific kernel from a list of like 8. plus can i delete unused kernals (example old versions of ubuntu) i have 4 different versions of hardy heron plus the recovery versions of each... i really want to streamline

---

### Post by barbedsaber on 2008-06-26
you would be looking for the grub config files, hang on, I will tag your post so that grub experts will come flocking.

---

### Post by PatrickMoore on 2008-06-26
> **barbedsaber said:**
> you would be looking for the grub config files, hang on, I will tag your post so that grub experts will come flocking.

beautiful.

---

### Post by iaculallad on 2008-06-26
> **PatrickMoore said:**
> i am curious if anyone knows if there is a way to have ubuntu load automatically from  when i  turn on my computer instead of having to  choose a specific kernel from a list of like 8. plus can i delete unused kernals (example old versions of ubuntu) i have 4 different versions of hardy heron plus the recovery versions of each... i really want to streamline

You can trim down your GRUB boot menu list by editing your /boot/grub/menu.lst file. You can comment/delete the old kernel entries (or the kernels you don't need) that are listed on that file then later on, use Synaptics Package Manager to delete the old kernels. On Synaptics, use the string "linux-image" (w/o quotes) to search for the installed old kernels.

```
gksu gedit /boot/grub/menu.lst
```

---

### Post by PatrickMoore on 2008-06-26
> **iaculallad said:**
> You can trim down your GRUB boot menu list by editing your /boot/grub/menu.lst file. You can comment/delete the old kernel entries (or the kernels you don't need) that are listed on that file then later on, use Synaptics Package Manager to delete the old kernels. On Synaptics, use the string "linux-image" (w/o quotes) to search for the installed old kernels.

```
gksu gedit /boot/grub/menu.lst
```

i knew there was a script that i could edit to get rid of that thank you.

---

### Post by barbedsaber on 2008-06-26
> **PatrickMoore said:**
> i knew there was a script that i could edit to get rid of that thank you.

I don't think it is a script, but rather a config file.

Script - Automaticly does somthing

Config file - Is read and written to by programs, and contains lots of settings, (Like which kernel to boot, and which ones to list)

---

### Post by PatrickMoore on 2008-06-26
> **barbedsaber said:**
> I don't think it is a script, but rather a config file.

Script - Automaticly does somthing

Config file - Is read and written to by programs, and contains lots of settings, (Like which kernel to boot, and which ones to list)

noted. im still getting used to technical terms and whatnot

---

### Post by iaculallad on 2008-06-26
And that file from where you edit your GRUB boot menu is:

> /boot/grub/menu.lst

---

### Post by PatrickMoore on 2008-06-26
> **iaculallad said:**
> And that file from where you edit your GRUB boot menu is:

thank you i do have that figured out do you know about automatically having my ubuntu kernel load(bypassing my grub boot menu unless i elect to enter it...)

---

