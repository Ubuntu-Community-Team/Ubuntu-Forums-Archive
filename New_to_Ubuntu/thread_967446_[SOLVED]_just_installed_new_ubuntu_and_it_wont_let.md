---
title: "[SOLVED] just installed new ubuntu and it wont let me get wireless internet"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by GumpTron on 2008-11-02
hello,

i installed ubuntu on my dell studio hybrid and it did not have the usual ability to choose a wireless network. There was some message about needing a broadcom proprietary thing, i enabled it but i still don't know how to get the net to work. I am posting from Vista because i duel boot. thanks.

---

### Post by Peter09 on 2008-11-02
Can you go into a terminal and type the following commands

```
lshw -C network
```

and

```
ifconfig
```

try and get the output posted here.

Can you get a wired connection working?

---

### Post by dentaku65 on 2008-11-02
Try to install from the terminal (connected with cable)
```
sudo apt-get install linux-firmware
```

---

### Post by GumpTron on 2008-11-02
thanks guys, but I restarted my computer and it started working. I guess that's all I needed.

it said something about keyring and wanted me to allow access. I clicked "always allow" and then it worked and I have wireless net.

---

