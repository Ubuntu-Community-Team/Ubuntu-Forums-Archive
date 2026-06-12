---
title: "[SOLVED] StartUp-Manager problem (happening right now, as we speak)"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by earthpigg on 2008-10-14
i think i got myself in trouble: i changed some stuff around in 'startup manager' and then saved/closed it.... and the "Performing post-configuration tasks" window thing has been doing its thing for about 10 minutes. i didn't start it from a terminal, so i cant say what the terminal output is..... kinda worried about force-closing it and screwing up my grub.

should i close this thing, leave it open for another 10 minutes?

specific things i changed:

reduced the delay from 5 seconds to 2.

told it to only save the last 4 kernels, and checked the associated box.

and ummm i think thats all i changed.

---

### Post by OutOfReach on 2008-10-14
You should leave it, I once changed some things and it took some time.
But if it continues and if it's pasted 30minutes-1hour than I think something is wrong.

---

### Post by earthpigg on 2008-10-14
thanks, OoR.

what should i do if we cross the 1 hour threshold? we're at 20 min right now.... hope for the best, plan for the worst!

---

### Post by earthpigg on 2008-10-15
ok then. it has been going overnight. should i close this thing or what?

---

### Post by Nepherte on 2008-10-15
Next time, make your changes directly into /boot/grub/menu.lst. The file itself is documented well enough to make basic changes. If you're into more advanced configuration, you can still look it up on the internet. Then it's just a matter of saving a configuration file. I have no clue why startup manager needs so much time for post processing.

---

### Post by philinux on 2008-10-15
> **earthpigg said:**
> ok then. it has been going overnight. should i close this thing or what?

Yes just close it. It's happened to me once.

Try running

sudo startupmanager

Yes thats sudo and not gksudo. Tip from the developer. Just to see if any errors show up.

---

### Post by earthpigg on 2008-10-15
i closed it and ran startupmanager right after, it looked kind of weird... less dialog boxes and options.

then i restarted x (that is what ctrl+alt+backspace does right?), and did sudo startupmanager... everything looks cosher, the changes i made before are saved.

```
mason@mason-laptop:~$ sudo startupmanager
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected

```

everything look like it should?

---

### Post by philinux on 2008-10-15
All looks fine. I'd go back to starting it from the menus now. Nice little gui app this.

---

### Post by iKonaK on 2008-10-15
don't worry, it happened 2 me but i just "forced quit" the saving bar, it's ok...;)

---

### Post by Dacker on 2008-10-15
It's not a big deal, just force it to quite.......:)

---

### Post by Malac on 2008-10-15
Sometimes startupmanager seems to get stuck if it has to do an 'update-initramfs'.
If you force quit then run that yourself just to check it has completed okay.

Hope this helps.

---

