---
title: "ipconfig/all vs ifconfig"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by ant2ne on 2008-06-22
ipconfig /all on a windows machine gives me lots of handy information including the addy of the DHCP server and the DNS server. ifconfig does not. What is the CLI equivalent of ipconfig/all ??

---

### Post by steveneddy on 2008-06-22
```

ifconfig -a

```

---

### Post by tysonh on 2008-06-22
ifconfig ususally tells me everything I need to know.  [Here]("http://linux.die.net/man/8/ifconfig") is a link to basically the manual page in terminal for ifconfig.

---

### Post by wdaniels on 2008-06-22
There's nothing directly and precisely equivalent that I know of, but you can find the gateway address using something like:

```
route -n
```

and the DHCP server address with something like:

```
grep dhcp-server-identifier /var/lib/dhcp3/dhclient.leases
```

For more information about wireless interfaces use iwconfig.

I guess you could write a simple shell script to lump all that stuff together (and even call it "ipconfig" :D) if you really want it that way, but Linux uses lots of smaller programs to do each job and often there is more than one alternative for the same thing, so best to just learn the Linux way for each ;)

---

### Post by the_doc on 2008-06-22
cat /etc/resolv.conf

---

