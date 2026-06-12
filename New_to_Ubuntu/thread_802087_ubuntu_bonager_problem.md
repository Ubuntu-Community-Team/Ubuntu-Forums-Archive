---
title: "ubuntu bonager problem"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by nymlord on 2008-05-21
Im using the programs bonager because my laptop never passes the scan after 30 mounts, so i found this program, Bonager, to avoid it, it used to be working but now for some reason it wont work. i left click, it asks me if i want to Force a scan for next boot, and i click yes, and the icon becomes orange, it should do that when its off, not on., its just kinda bothering me because i dont think it would avoid the fsck scan so i would like to get it fixed somehow, does anyone know ? :S..

thanks

---

### Post by alexandremrj on 2008-05-21
Sorry i don't know that program so i can't tell if it is supported in hardy.

Why don't you try autofsk (present in repositories), you can change the number of boot before each check and do it at shutdown when is asks or simply cancel the check and do it on the next boot.

Ensures that the automatic disk checks will no longer inconvenience you
AutoFsck is a script which automates periodic disk checking in such a way that it no longer bothers the user at boot every 30-ish times, and is streamlined in a friendly graphical user interface.  Instead, when a check is required, the user is prompted at shutdown and given the option to run the checks before powering off the machine (this is unattended).  In this way AutoFsck ensures that the automatic disk check will no longer inconvenience you by making your boot times very long.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

---

### Post by nymlord on 2008-05-21
> **alexandremrj said:**
> Sorry i don't know that program so i can't tell if it is supported in hardy.

Why don't you try autofsk (present in repositories), you can change the number of boot before each check and do it at shutdown when is asks or simply cancel the check and do it on the next boot.

Ensures that the automatic disk checks will no longer inconvenience you
AutoFsck is a script which automates periodic disk checking in such a way that it no longer bothers the user at boot every 30-ish times, and is streamlined in a friendly graphical user interface.  Instead, when a check is required, the user is prompted at shutdown and given the option to run the checks before powering off the machine (this is unattended).  In this way AutoFsck ensures that the automatic disk check will no longer inconvenience you by making your boot times very long.

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

thank u, i installed it lets just hope it works :D

---

