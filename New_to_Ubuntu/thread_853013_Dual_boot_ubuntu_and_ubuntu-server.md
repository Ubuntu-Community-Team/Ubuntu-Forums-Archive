---
title: "Dual boot: ubuntu and ubuntu-server"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by saj0577 on 2008-07-08
I plan on having 2 installs.

Ubuntu-desktop
&
ubuntu-server

SO i will be dual booting what is the best way to do this i see loads of guides on ubuntu and windows but not many on ubuntu & ubuntu or ubuntu & other linux distro.


How should I partition my drive.
i.e seperate boot partition?


Thanks in advance
Saj


I do have reasons to install them both im not crazy :)

---

### Post by DezSP on 2008-07-08
You'll want a seperate partition for root (/) on ubuntu-server and root on ubuntu. The former can be about 2 GB, the latter wants to be at least 5. I'd recommend setting up a seperate partition for /home, either shared between the two systems (which will make your preferences the same) or two seperate ones for each. You'll also need a linux-swap partition which can definitely be shared by the two OSes. You can set this all up in either installer and it shouldn't matter which you do first, provided you set the partitions up manually in this manner.

So my recommendation is something like this, though remember it's only a guideline:

sdx1 (primary) -- mount as / for ubuntu (5~6 GB)
sdx2 (primary) -- mount as / for ubuntu-server (2~3 GB)
sdx3 (primary) -- mount as /home for both (remaining space)
sdx5 (logical) -- mount as swap for both (~1 GB)

---

### Post by The Cog on 2008-07-08
I think a shared boot partition would be inviting conflicts. 
Shared home might make sense depending on your application.

One thing to note is that assuming they have their own /boot directories, the second one to be installed will offer the first install as an option in its GRUB menu.lst. However, it points to the version numbered boot files (vmlinuz and initrd) and will not know to change when the first OS gets upgraded. I therefore suggest you menually edit the menu.lst to point to /vmlinuz and /initrd, which are symlinks to the latest version of the real files in /boot.

---

