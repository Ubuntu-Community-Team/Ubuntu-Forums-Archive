---
title: "Cannot get samba going"
date: 2018-08-17
forum: New to Ubuntu
---

### Post by garyi on 2018-08-17
Hello folks.

Please be assured I have been researching this all day and cannot get it working.

I have installed Samba on unbuntu. This is a brand new ubuntu install from today. I can right click a folder and select local network share

I have set name, password on and off, guest users on and off all combinations.

From pcs and macs, if I try and log in as guest it will either fail or on mac say that the original item could not be found
If I set it with password and enter credentials they fail

I set password in terminal as per instructions found and entered one of the shares in samba conf file, still no dice.

I cannot get this thing to broadcast SMB properly.

Can anyone help?

---

### Post by TheFu on 2018-08-17
a) which OS is the server? Versions are important.
b) which OSes are the clients? Versions are important.
c) output from **testconf** on the samba server. Please use code tags so it is readable.
d) are you using zeroconf/avahi or proper DNS for name resolution?

Info please.

---

