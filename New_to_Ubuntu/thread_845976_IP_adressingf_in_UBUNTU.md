---
title: "IP adressingf in UBUNTU"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by student eternal on 2008-07-01
Hi,  I have a computer running Hardy that I was trying to set up as a lab computer, however it would not request an IP address from the DHCP server to let it see the other computers on my network and the internet.  I eventually got this fixed and working, but I was wondering is there a command line way to request an IP address, something similar to the windows "ipconfig /renew"

Sorry if this is a dumb question, but I could not find a listing for this in the docs.

Thank you:

---

### Post by hyper_ch on 2008-07-01
```

sudo /etc/init.d/networking restart

```

---

### Post by benfindlay on 2008-07-01
You can set a static IP by typing ```
sudo nano /etc/network/interfaces
```

You will get a file like this:
> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0


Change it to something like this:
> 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.XXX
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


Where XXX is the IP address you want the server to have
Hope this helps!

---

### Post by Cadmus on 2008-07-01
You'll have to do the networkign restart thing hyperch mentionned after setting the static IP in interfaces.

If the OP is looking for something just to do renew dhcp requests can they not use

```
sudo dhclient -r eth0
sudo dhclient eth0
```

---

