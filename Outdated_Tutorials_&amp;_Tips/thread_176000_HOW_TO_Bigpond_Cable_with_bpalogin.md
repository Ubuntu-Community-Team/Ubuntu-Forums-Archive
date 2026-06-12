---
title: "HOW TO Bigpond Cable with bpalogin"
date: 2006-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by deanjm1963 on 2006-05-14
I use bpalogin. The easiest way to get it up and running is this.

Install bpalogin

then open a terminal and type
```
sudo gedit /etc/bpalogin.conf
```

set your name where is says username joebloggs (or whatever your username is)
set your password where it says password goldilocks (or whatever your password is)

Then scroll down to the very bottom of the file and uncomment

minheartbeatinterval 60

maxheartbeatinterval 420

save and close the file

to get it to start automatically

again, in a terminal

```
sudo gedit /etc/network/interfaces
``` 

and make the following changes

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up /usr/sbin/bpalogin start

save and close the file. make sure you have a carriage return after the last line.

This works for both Breezy and Dapper

---

### Post by az_s_za on 2006-11-12
> ...scroll down to the very bottom of the file and uncomment

minheartbeatinterval 60

maxheartbeatinterval 420...

What do you mean by "uncomment"?  What do I do at this step?

Thanks.

---

### Post by jms830 on 2006-11-12
uncomment means you put a # symbol in front of it, effectively "disabling" the lines.

---

### Post by mchoo on 2007-04-22
Hi,

Which BPALogin version should I download for Ubuntu? There are several flavours for Linux, but none of them is specific for Ubuntu.

Thanks

---

### Post by mchoo on 2007-04-25
deanjm1963, I installed bpalogin, followed your instructions, but still no go. Please help??

---

