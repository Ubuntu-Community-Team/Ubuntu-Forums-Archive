---
title: "moblock and grub freeze"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by spazzywulf on 2008-10-18
I tired to uninstall moblock the other day because I couldn't connect to the internet. I did a sudo apt-get --purge moblock. After I did this, i restarted my computer, but now it freeze on the Boot screen. 

I'm dual booting with Vista, but Linux is my primary partition and it's got all of my stuff on it. Can my laptop be saved?

---

### Post by caljohnsmith on 2008-10-18
How far do you get on start up? Do you see a Grub menu at all (or does it say something like "press ESC to see the menu"), or does the computer freeze before you see the Grub menu? Or maybe do you see the Ubuntu splash screen and then it freezes?

---

### Post by spazzywulf on 2008-10-18
Um...the splash screen comes up for a few seconds and then it freezes up.

---

### Post by jre on 2008-10-19
I don't know if it has anything to do with moblock.
But if this is the case and if moblock was not uninstalled completely, then I suggest to boot in grub in the rescue mode (or with a live cd) and remove /etc/init.d/moblock.

---

### Post by spazzywulf on 2008-10-19
I tried to boot in recovery mode and it comes to

Begin: Running /scripts/init-bottom ...
Done
Init: Error parsing configuation: No such file or directory
[    17.763587] Kernel panic -not syncing: Attempted to kill init!

and then it freezes. I'm not sure why this is happening or what to do about it.

---

