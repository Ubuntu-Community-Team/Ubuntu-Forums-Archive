---
title: "network configuration"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-19
hi everyone.
getting the network up and running in intrepid was a real mess,as i tried hard keying in my IP address,subnet mask and default gateway settings in 
system>preferences>network configuration>wired>IPv4>manual,but it never worked,in fact the system never accepted my settings.i came to know from someone here that it was a bug.i anyways modified the interfaces file(/etc/network/interfaces)which now looks like:

auto lo
iface lo inet loopback


iface eth0 inet static
address 10.110.6.220
netmask 255.255.255.0
gateway 10.110.6.2

auto eth0

so,now i can use the network very well.
but,then i decided to input my DNS server setting which was 144.16.192.55,from system>preferences>network configuration>wired>IPv4>manual>DNS,but to no avail.

can someone tell me the method to input the DNS server parameter this by modifying some file as i modified 'interfaces' to get the network work?

---

### Post by stonecoldjha on 2008-11-19
though i can use the network on ubuntu,i can't use networking in virtualbox,unless and until i input that DNS.

---

### Post by iponeverything on 2008-11-19
/etc/resolve.conf

---

### Post by stonecoldjha on 2008-11-19
but /etc/resolvconfig is a directory.

---

### Post by xpod on 2008-11-19
> /etc/resolve.conf

Without the "e":)
```
resolv.conf
```

---

### Post by stonecoldjha on 2008-11-20
but,then how do i add DNS to the file?

---

### Post by iponeverything on 2008-11-20
just open it with your favorite editor.

```
sudo nano /etc/resolv.conf
```

---

### Post by stonecoldjha on 2008-11-20
after opening,is there any specific format in which i need to write the DNS.How do i do it?

---

### Post by iponeverything on 2008-11-20
google is your friend. 


Just add these two lines and you will be fine:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

