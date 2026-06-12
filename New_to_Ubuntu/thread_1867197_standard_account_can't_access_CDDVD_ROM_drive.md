---
title: "standard account can't access CD/DVD ROM drive?"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by spikeyseth on 2011-10-22
I made my little brother an account on my PC so he could use the Internet etc. and knowing what a nefarious little devil he is, i only gave him standard account permissions. however, when he inserted a music disk into the slot, he couldn't access it, it didn't appear on the launcher or in the file browser. when i logged my account, it was there.

I don't want to give him full permissions, but how can i make it so he can still access his USB drives?

I'm running 11.10 oneiric ocelot

---

### Post by little_penguin on 2011-11-08
You can add him to the cdrom group in System Settings, Users and Groups. The terminal command for this tool is:
 
```
users-admin
```
 
If it is not installed, you can install it by entering this command:
 
```
sudo apt-get install gnome-system-tools
```

---

