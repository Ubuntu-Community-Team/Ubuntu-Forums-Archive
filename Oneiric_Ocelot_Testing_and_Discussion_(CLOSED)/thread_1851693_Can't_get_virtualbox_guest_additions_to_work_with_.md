---
title: "Can't get virtualbox guest additions to work with 11.10"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2011-09-28
I'm running 11.10 as both a host and guest, but cannot get guest additions to run on the guest.  Nothing happens, but a quick return to the shell prompt.  I'm running VB 4.1, although I've seen references to a version 4.2 which I can't find on the virtualbox web site.

---

### Post by haqking on 2011-09-28
> **seattle vic said:**
> I'm running 11.10 as both a host and guest, but cannot get guest additions to run on the guest.  Nothing happens, but a quick return to the shell prompt.  I'm running VB 4.1, although I've seen references to a version 4.2 which I can't find on the virtualbox web site.

[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)

---

### Post by seattle vic on 2011-09-28
Those all show release that start with 4.1.2-73507, and that's what I have loaded.  Is that the nomenclature for "4.2" ?  Seems strange, but in any event, it's what I'm running and I still can't get the guest additions to do anything.  I figured it was an 11.10 thing and that at some point Oracle would have to update for it.

---

### Post by haqking on 2011-09-28
> **seattle vic said:**
> Those all show release that start with 4.1.2-73507, and that's what I have loaded.  Is that the nomenclature for "4.2" ?  Seems strange, but in any event, it's what I'm running and I still can't get the guest additions to do anything.  I figured it was an 11.10 thing and that at some point Oracle would have to update for it.

there is no 4.2 the latest is 4.1.2 as seen on the link and the original source [www.virtualbox.org](www.virtualbox.org)

remember that 11.10 is a beta so support will be minimal.

see here

[https://forums.virtualbox.org/viewtopic.php?f=3&t=43853](https://forums.virtualbox.org/viewtopic.php?f=3&t=43853)

[http://www.youtube.com/watch?v=zN2yM6Cg02w](http://www.youtube.com/watch?v=zN2yM6Cg02w)

and i believe you need the following for 11.10

```
sudo apt-get install virtualbox-ose-guest-utils
```

---

### Post by seattle vic on 2011-09-28
Tried installing the guest-utils, but it didn't help.  It's curious that others seem to be saying that guest editions are working for them, but no me.  I guess I'll just wait until either 11.10 or VB figures it out.

Thanks for the reply.

---

### Post by seattle vic on 2011-09-28
Actually, after installing the virtualbox-ose-guest-utils and then rebooted, the guest window will not resize, however running the guest additions still seems not to run.  Oh well.

---

### Post by makitso on 2011-09-29
The last step I needed to do was to go into the Hardware Drivers and make the extensions active.  Then reboot.

---

### Post by shaneo1 on 2011-09-29
There is a manual workaround for this,  I downloaded the latest Vbox guest addtions for vb 4.1 as a iso then copied it to /usr/share/virtualbox  but to get it to work you must rename it to VBoxGuestAdditions.iso

I found it was missing from Vbox4.1.2

Hope this helps

You can download it from here:

```
https://launchpad.net/ubuntu/+source/virtualbox-guest-additions-iso/4.1.2-1
```

Check out the image attached below.

---

