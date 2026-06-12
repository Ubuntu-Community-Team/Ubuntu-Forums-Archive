---
title: "No More Grub Help"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Nigel_DW on 2008-04-30
**[COLOR="Red"]Please help[/COLOR]** 
I've installed Ubuntu 8.04 on a secondary partition on my laptop - and it installs fine. I can reboot and log back in with no problem

As soon I login to windows then the grubloader no longer shows up on boot - I've reloaded 8.04 several times please help

---

### Post by mikewhatever on 2008-04-30
Post the output of <sudo fdisk -l>.

---

### Post by louieb on 2008-04-30
Probably your windows Anti-virus program. It sees the **MBR** has changed. Thinks virus and changes it back to its last know good copy. Check the AV settings. Should be somewhere to tell it the change is ok.

---

