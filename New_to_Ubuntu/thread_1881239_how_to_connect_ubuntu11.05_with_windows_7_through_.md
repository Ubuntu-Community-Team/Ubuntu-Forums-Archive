---
title: "how to connect ubuntu11.05 with windows 7 through  crossing cable"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by spkanu on 2011-11-15
hi 
i am a windows user, and now i hav installed ubuntu11.05 in my laptop.
usually i used ethernet port to connect with other pc for file sharing.
but i can't able to connect in ubuntu.
when i connect ubuntu with windows it will show that connected but when i m going to network and sharing centre of windows it will not show my device.


somebody help me out that how i will connect ubuntu with windows 7 crossing cable.

---

### Post by LowSky on 2011-11-15
crossover cable.

anyway. you need samba

[http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/](http://www.liberiangeek.net/2011/04/connect-ubuntu-11-04-and-windows-systems-via-sambapart-one/)

---

### Post by 3rdalbum on 2011-11-15
Two things:

If you want to access your Ubuntu hard disk from the Windows machine, you need to have Samba's server installed and set up on the Ubuntu machine.

The 'shares-admin' program will help you install and set it up. Go to the Terminal and type:

```
gksudo shares-admin
```

It will ask you if you want to install NFS and SMB support - don't worry about NFS, just choose SMB.

The second thing you need is an IP address for both machines. If your Windows is set up to act as a DHCP server, then it will send an IP address to the Ubuntu machine. If not, then you need to set up a static IP address in Network Manager, and make sure it's nearly the same as the Windows machine's one. For instance, if the Windows machine is set to use '192.168.1.12' as the IP address, then you need to tell Ubuntu to use '102.168.1.11' or something like that. Basically, ONLY the last set of digits should be different.

---

