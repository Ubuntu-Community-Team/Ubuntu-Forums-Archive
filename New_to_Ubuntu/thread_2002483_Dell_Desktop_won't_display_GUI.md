---
title: "Dell Desktop won't display GUI"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by abejon on 2012-06-12
Upgraded my Dell Desktop computer from ubuntu 10.x to 11.x. While booting up after upgrade the system will stop and ask me to login in TTY mode. I can login OK with my normal user ID and I can log out typing "exit" BUT nothing else happen! GUI will not appear.  Is there a command I can type to call GUI? How can I get rid of the TTY mode and switch to GUI?

---

### Post by editheraven on 2012-06-12
I assume you have gnome installed right?

Call gnome by :  start gdm or, after you login in your shell : sudo gnome-session

le : for classic gnome-panel session start with "gnome-session -session=classic-gnome"

le2: or sudo startx

---

### Post by abejon on 2012-06-12
> **editheraven said:**
>  sudo gnome-session


No, luck, after I typrd this command, it came back with "Cannot open display"

---

### Post by editheraven on 2012-06-13
This is not "no luck". Do you have nvidia or ati?

---

### Post by idoitprone on 2012-06-13
since you have problems with copying and pasting terminal commands

```
sudo apt-get install pastebinit

lspci -nnk | pastebinit
```

paste the link on the forum

this will give us the an idea of you machine

---

### Post by abejon on 2012-06-13
> **editheraven said:**
> This is not "no luck". Do you have nvidia or ati?

nvidia.
I tried to boot using Ubuntu 12.04 on USB stick, works great.
So, is there a way to reinstall ubuntu on the hard drive without loosing the data?

---

### Post by editheraven on 2012-06-14
You can however to get the display working on your ubuntu. 

BTW : what 11.x means? 11.04 or 11.10?

---

