---
title: "rEFIt vs. GRUB troubles?"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Tu1J4kXk8NUhMz on 2008-10-25
So here's the problem: I had to reinstall Ubuntu because of an error in repartitioning. I'm running a MBP, triple booted with Windows XP, Ubuntu and Mac OS X Leopard. So, I reinstall Ubuntu, and stupid me I forget to change the install location of GRUB. So Ubuntu installs GRUB to hd0 (which, to the best of my knowledge, doesn't exist) instead of sda3 like I'm supposed to do. I get done, and I have to reinstall Ubuntu AGAIN because GRUB is in the wrong place.

SO...I reinstalled Ubuntu. It works. However, now rEFIt tells me that I have FOUR operating systems. It says Mac OS X loads from partition 1, Windows XP from partition 4, Ubuntu from partition 3 and Linux from HD. Any clue how to get rid of the extra Linux read-out from this fictional "HD?" I understand the common fix is to reformat everything. You can understand that I don't wanna do that. :-P

Suggestions please?

---

### Post by Tu1J4kXk8NUhMz on 2008-10-25
bump

---

### Post by DGortze380 on 2008-10-25
You might have better luck in the Apple users forum.

Anyways, grub definitely didn't install to a location that doesn't exist. Sounds like you installed grub to the first part of your hard drive AND to sda3.

You're going to have to figure out what happened with that first 'failed' install, and remove the extra grub location.

---

### Post by SilverGoldBronze on 2008-10-26
Well, if you're not getting any problems in performance, the easiest way is just to remove the line:

Alright, I'm rusty in this sort of thing so I don't remember the location of the file, however, so browse to your root Ubuntu partition "File System"
Go to boot, then GRUB or something like that. I'm not wholly sure. Find the GRUB.txt file. Now, Alt+F2, sudo geedit /filelocation here


Maybe someone else can clarif the steps. I hate typing on my Wii.

---

### Post by cariboo on 2008-10-26
To remove the line from /boot/grub/menu.lst, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

This will open gedit as root, just remove the entry with HD in it, save the file, then reboot.

Jim

---

### Post by dereferenced on 2008-10-26
I am sorry this is off topic. I have been checking around since 10 minutes but don't find a link to post a new thread.. :O
Where do I find a link to start a new thread. Thanks in advance.

[New to Ubuntu Forums]

---

### Post by DGortze380 on 2008-10-26
> **cariboo907 said:**
> To remove the line from /boot/grub/menu.lst, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

This will open gedit as root, just remove the entry with HD in it, save the file, then reboot.

Jim

I'm not sure this will work. I think the problem is that he actually has grub installed in 2 locations, thus rEFIt is showing an extra boot loader.

What happens if you select the extra loader from rEFIt?

For kicks, post the output of 
```

cat /boot/grub/menu.lst

```

---

### Post by Tu1J4kXk8NUhMz on 2008-10-26
> **DGortze380 said:**
> What happens if you select the extra loader from rEFIt?

For kicks, post the output of 
```

cat /boot/grub/menu.lst

```

:-s Strangely enough, rEFIt loads up the little penguin loading screen, as normal, then switches to black with the word "GRUB" and a flashing cursor next to it at the top.

Is there some way to find out what rEFIt is referencing to (as in what it means by the phrase "HD")?

I haven't had a chance to try out the code. I'm going to see if I can hunt down the answer to my above question and then I'll post the code output.

---

### Post by DGortze380 on 2008-10-26
> **teamjh14 said:**
> :-s Strangely enough, rEFIt loads up the little penguin loading screen, as normal, then switches to black with the word "GRUB" and a flashing cursor next to it at the top.

Is there some way to find out what rEFIt is referencing to (as in what it means by the phrase "HD")?

I haven't had a chance to try out the code. I'm going to see if I can hunt down the answer to my above question and then I'll post the code output.

But nothing after that?

hd0 is your entire drive. each partition is at sdax. You installed grub at the beginning of your hard drive (possibly in the mbr?? or EFI??) and the beginning of your ubuntu partition. you'll need to remove the grub files from the beginning of your hard drive (not from the ubuntu partition).

Thats the extent of my knowledge. I would ask in the apple forums.

---

