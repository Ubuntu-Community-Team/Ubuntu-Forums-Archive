---
title: "Dbl Boot Now, Want to add 3rd OS on 2nd HDD"
date: 2008-07-26
forum: Other OS Talk
---

### Post by 4Orbs on 2008-07-26
I am currently double booting xp and xubuntu from the master HDD and intend to keep these two OS intact. Now I would like to set up my second HDD so I can triple boot an additional third system for distro hopping. I have read that it can be done easily, but since the MBR is on the first HDD I would be required to do some HDD mapping to have the third OS show up on the grub boot screen at boot up. Is this correct? Can I just install the third OS on the slave HDD in a new partition and then add a line of code to the current grub config file which is located on the master HDD and thus create a third grub entry so that I can boot to the third OS? Thanks for any suggestions.

---

### Post by mips on 2008-07-26
> **4Orbs said:**
> Can I just install the third OS on the slave HDD in a new partition and then add a line of code to the current grub config file which is located on the master HDD and thus create a third grub entry so that I can boot to the third OS? Thanks for any suggestions.

It's as simple as that.

---

### Post by logos34 on 2008-07-26
You can specifically add a [configfile or chainloader boot entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").

check out this link:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by 4Orbs on 2008-07-26
Thanks for the replies. I ended up installing all three systems on the master HDD and using the slave HDD for common storage between all three. Triple boot works as expected and now I'm collecting the various iso images for the OS's. Triple boot seems like a great way to distro hop. Thanks again.

---

### Post by mips on 2008-07-28
> **4Orbs said:**
>  Triple boot seems like a great way to distro hop. Thanks again.

Using a VM is much easier and simpler.

---

