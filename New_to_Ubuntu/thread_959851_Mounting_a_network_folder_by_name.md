---
title: "Mounting a network folder by name"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-10-26
My /etc/fstab file already mounts 2 of my networks shared folders, but those computers are over a static IP address because they are never leaving this network. I just set up a laptop with Ubuntu, and I am going to take this laptop out of this network, I tried playing around with static IP, but I couldn't get it to reconnect to my wireless network like that. So I decided I would rather see if there is a work around that lets me use the computers network name rather then its IP address to mount its folders.

---

### Post by Xiong Chiamiov on 2008-10-26
If the host name is properly setup on the remote machine, you can mount it like so:
```

sudo mount fileserver:/media/storage /mnt

```
substituting the appropriate host and folder names.

---

### Post by DoubleMcLovin on 2008-10-26
but how can I set that up in fstab?

---

### Post by DoubleMcLovin on 2008-10-27
bump:
just need fstab code to mount a network share by the name instead of IP address

---

