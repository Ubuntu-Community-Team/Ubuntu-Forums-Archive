---
title: "unable to edit wvdial.conf file"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by arunkumar413 on 2008-11-27
[SIZE="6"]hi
I want to connect to internet. Am using Ubuntu 8.04 LTS.i ran the wvdial command.It has detected my modem.but am unable to edit the wvdial.conf file present in /etc folder.It returns an error "sorry you do not have necessary permission to edit this file".When I checked the properties of the wvdial.conf file,it is  owned by root user.moreover i cannot login as root user.help me please[/SIZE]
[/SIZE]

---

### Post by nakama85 on 2008-11-27
> **arunkumar413 said:**
> [SIZE="6"]hi
I want to connect to internet. Am using Ubuntu 8.04 LTS.i ran the wvdial command.It has detected my modem.but am unable to edit the wvdial.conf file present in /etc folder.It returns an error "sorry you do not have necessary permission to edit this file".When I checked the properties of the wvdial.conf file,it is  owned by root user.moreover i cannot login as root user.help me please[/SIZE]
[/SIZE]

you have to have sudo privs
in terminal run
```
sudo gedit /etc/wvdial.conf
```

---

### Post by nakama85 on 2008-11-27
Did this solve your problem?

---

### Post by Snort44 on 2009-03-09
I'm using Kubuntu 8.10
For the life of me, I can't edit /etc/wvdial.conf

I tried sudo chown -R /
I tried sudo kate /etc/wvdial.conf
I tried sudo nano /etc/wvdial.conf

I keep getting "/etc/wvdial.conf is owned by uid 1000 should be 0"

I tried "chmod 755 /etc/wvdial.conf"
I tried "chmod 755 /etc/"
I tried "chmod 755 /etc"

Where am I going wrong?  Thanks!!!!!!

---

### Post by snova on 2009-03-09
> **Snort44 said:**
> I'm using Kubuntu 8.10
For the life of me, I can't edit /etc/wvdial.conf

**I tried sudo chown -R /**
I tried sudo kate /etc/wvdial.conf
I tried sudo nano /etc/wvdial.conf

**I keep getting "/etc/wvdial.conf is owned by uid 1000 should be 0"**

I tried "chmod 755 /etc/wvdial.conf"
I tried "chmod 755 /etc/"
I tried "chmod 755 /etc"

Where am I going wrong?  Thanks!!!!!!

You've taken ownership of your entire system with that first command; I'm surprised anything still works at all.

The command would be:

```
kdesudo kate /etc/wvdial.conf
```

But at this point, you have bigger problems. Sadly there's not much you can do for that but a reinstallation...

---

### Post by crjackson on 2009-03-09
deleted...

---

### Post by Snort44 on 2009-03-09
I'll reinstall.  In fact, I think I'll go with the 32 bit version if it'll work.  I'm not convinced I got the correct 64 bit version for AMD as there's no mention of it on the disk.  Thanks for the help!

---

