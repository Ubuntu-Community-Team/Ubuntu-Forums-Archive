---
title: "How do I change the primary DNS IP address on 15.04? Very confused.."
date: 2015-12-25
forum: New to Ubuntu
---

### Post by mohaafan on 2015-12-25
Hi,

I have Ubuntu 15.04 x64 OS running on a remote VDS server.  I need to change the primary DNS IP address to another address other than the default address provided.  I read instructions online to change /etc/resolv.conf but after editing it I can't make it read only.  Non of the chmod commands work on that file.  Also, I read that I would also need to edit /etc/dhcp3/dhclient.conf, but when I did "sudo nano /etc/dhcp3/dhclient.conf", it showed me a blank screen.  What do I have to do to properly change the primary DNS IP address on Ubuntu 15.04 and make it so that it does not get overwritten upon reboot or other system triggers? By the way, I do not have a GUI desktop installed nor do I plan on installing one.

Thanks.

---

### Post by matt_symes on 2015-12-25
Hi

Is this a desktop or server installation ?

Anyway, there is more than one way to do this.

One method is the dhclient.conf file as you hinted at above

The file may be called

```
/etc/**dhcp**/dhclient.conf
```

Look for this line
 
```
#prepend domain-name-servers 127.0.0.1;
```

Remove the # character at the start and add your name servers there.

Another method (if you are using the interfaces file) is to use the dns-nameservers stanza.

```
cat /etc/network/interfaces

...

auto em1
iface em1 inet static
        ...        
        dns-nameservers 8.8.8.8
        ...
```

Kind regards

---

### Post by mohaafan on 2015-12-25
Hi matt_symes :)

Your suggestion seems to be working.  I'll report back if I have any issues with this method over time.  Thanks again :)

---

