---
title: "[SOLVED] No shutdown problemo..."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by davidgypsy on 2008-05-27
This one has me stumped...
7.04 runs fine
7.10 will not shut down, just a blank screen and hangs forever
8.04 same problem as 7.10

I have to hard shutdown which only happens 4 or 5 times and then it won't boot, causing data loss and needs a reinstall. Painful.

I have an HP compaq nx9030 that has been running Linux successfully for years now and just hit this snag last year with the release of 7.10. Since then I have tried a number of up-to-date distros running the kernel version equal to 7.10 or newer and it seems they all have the same problem, no shutdown for me. I just tried Fedora 9 and Mandriva 8.something spring that was just released...

I searched it on the forum but nobody else seems to have this same problem. Any ideas from the clever folks out there, (or even the not so clever folks)? :)

---

### Post by alienexplorers on 2008-05-27
You probably have an old BIOS on your computer.  As of 7.10 the BIOS must have a current date, if not, your machine will not recognize the acpi command.  You need to add it to the /boot/grub/menu.lst file.  I have below a sample of how it should look.  The important part is in red. To edit the menu.lst file do:
> sudo gedit /boot/grub/menu.lst
Then go to the bottom where the operating system loaders and add the section in red:
> ## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=5bf58732-bcfd-4a4d-8040-fcf8c0cf24a9 ro quiet splash [COLOR="Red"]acpi=force[/COLOR]
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

---

### Post by KingTermite on 2008-05-27
I think there is some program (just read about it last night in the "ubuntu bible" book I bought) called "Boot Monitor" or something like that (in repository). It monitors startup/shutdown and keeps a log which can then be read/converted into a graphics output format with the client for the program. Its supposed to be good about figuring out hangs and things that are taking too long in the startup/shutdown processes.

Hopefully someone here can give you the exact name of the program I'm talking about...I'm at work now and don't have the book in front of me to tell you.

---

### Post by KingTermite on 2008-05-27
I just looked at the table of contents of that book at Amazon. I think the program is called "Boot Chart".

---

### Post by davidgypsy on 2008-05-28
Thanks guys, I'm going to try this out when I get home next week!

---

### Post by davidgypsy on 2008-11-05
Nope, this didn't work... 8.10 also doesn't shutdown. Damn!

---

### Post by davidgypsy on 2008-11-28
Ok, seems I have solved the problem! I switched off all the desktop effects, which disables Compiz, and it's been working fine for a week now. Must have been a graphics thing... pity though, I kind of like the zooming, fading and stuff. But at least it WORKS! Hooray!
 :popcorn:

---

