---
title: "network access"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by daberger on 2008-07-31
how can i access the network files on my (wireless) networked windows comp from my xubuntu laptop?

i havent seen any network folder like in windows on xubuntu

---

### Post by lisati on 2008-07-31
One way is through "samba" - more information can be found here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by superprash2003 on 2008-07-31
in the terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine..

---

### Post by NikoC on 2008-07-31
> **superprash2003 said:**
> in the terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine..

I'm not that sure that nautilus is part of xubuntu... doesn't xubuntu use thunar which, as far as I'm aware, you can not use to access so called samba shares.

If so, first open a terminal and type:
sudo apt-get install nautilus

Then use superprash2003's terminal command.
Or just start nautilus and in the address line type: smb://ip_of _the_windows_machine

---

### Post by daberger on 2008-08-01
error message

:nautilus cannot displaysmb://x.x.x.x ( i dont want none of u noing my ip. grrr)

nautilus cannot handle smb:locations.

---

### Post by NikoC on 2008-08-01
Hmmz, perhaps you have to install samba first?
sudo apt-get install samba

---

