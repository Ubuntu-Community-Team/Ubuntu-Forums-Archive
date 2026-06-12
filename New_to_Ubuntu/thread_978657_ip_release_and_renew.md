---
title: "ip release and renew"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-11
how can i do a release and renew of my IP address in ubuntu 8.10?  without having to restart the computer if possible.

thanks.

---

### Post by dustman on 2008-11-11
As I see it, if you want to renew your IP address, you have DHCP. Try typing ```
sudo dhclient
``` in the console.

Cheers!

Radu

---

### Post by w4ett on 2008-11-11
Linux renew ip command

The -r flag explicitly releases the current lease, and once the lease has been released, the client exits. For example, open terminal and type the command:
```
$ sudo dhclient -r
```
Now obtain fresh IP:
```
$ sudo dhclient 
```

---

### Post by mapes12 on 2008-11-11
Try this:

[http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/](http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/)

---

### Post by dustman on 2008-11-11
> **w4ett said:**
> Linux renew ip command

The -r flag explicitly releases the current lease, and once the lease has been released, the client exits. For example, open terminal and type the command:
```
$ sudo dhclient -r
```
Now obtain fresh IP:
```
$ sudo dhclient 
```

is the first command really necessary? My room mate shares his internet connection to me and all I have to do in order to connect to the internet after he restarts his computer is "sudo dhclient"...

---

### Post by Matt26 on 2008-11-11
thanks for the responses- i want to release my current IP address (which was obtained via DHCP) and use a static IP that i just assigned under the Network Configuration screen- how i do update my IP address this way?

---

### Post by w4ett on 2008-11-11
[http://ubuntuforums.org/showthread.php?t=278537](http://ubuntuforums.org/showthread.php?t=278537)

This thread might be of help.

---

