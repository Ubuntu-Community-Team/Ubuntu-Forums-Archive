---
title: "Set up a vpn connection - firewall blocking?"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by mlvmhn on 2013-12-26
i need to find the terminal, in order to disable my firewall. 

where do i find it?

which command disables the firewall?

---

### Post by deadflowr on 2013-12-26
Did you turn on the firewall?

But for the record, try ctrl + alt + T with the keyboard.

Don't know what system or desktop you're running so, it could be different as to where in the applications it is listed.

---

### Post by mlvmhn on 2013-12-26
now i got it. 

which command disables the firewall?

---

### Post by deadflowr on 2013-12-26
Again, did you enable the firewall in the first place?
The firewall is disable by default, so...

But in case try
```
sudo ufw disable
```
to disable
```
sudo ufw enable
```
to enable
and
```
sudo ufw status
```
to see what state it is in.

Edit: I would run the status command first.

---

### Post by mlvmhn on 2013-12-26
it&#347; says its disabled. 

my problem is that i&#7743; trying to set up a vpn connection, and i thought it was the firewall that blocked it.

what does "sudo" mean?

---

### Post by deadflowr on 2013-12-26
sudo gives you root access, meaning it gives the regular ole user(You) the ability to make changes to the system.

Don't know what about what about vpn, but I think you might need to install additional packages.
Look here maybe
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

Edit: This might be more current
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by Iowan on 2013-12-26
I've re-titled your thread.

---

### Post by mlvmhn on 2013-12-26
k, my problems is that i try to set up a pptp vpn connection. but i always get disconnected after a few seconds. 

i have disabled the firewall, and did everything as the pptp vpn guide tells me. 

what other things to do?

is it hard to set up a open vpn?

---

