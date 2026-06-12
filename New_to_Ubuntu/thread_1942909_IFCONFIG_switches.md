---
title: "IFCONFIG switches"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by mikeybinec on 2012-03-18
I could be blind but I was wondering if IFCONFIG has the same switch(es) as the DOS command line does i.e.  ipconfig /release  and ipconfig /renew
I unplugged Unbuntu server from the internet router  and hooked it up to a router that I started DHCP on but I had to do alt control delete so it would acquire the new IP address. Just wondering if there is a IFCONFIG /renew /release command. I could'nt find one

thanks

---

### Post by Holdolin on 2012-03-18
is your network card set to static or DHCP? /etc/network/interfaces is where your network interface would be.

---

### Post by mikeybinec on 2012-03-18
Running in Oracle's Virtual Box so the NIC on the windows machine controls the network. I ran ifconfig --help or whatever the command is to see if there is a ifconfig /renew or /release but I couldn't find one or there is one and I'm blind. just wondering if there is linux command gura who knows a ifconfig /release command
 
thanks

---

### Post by winh8r on 2012-03-18
If you run 

```
sudo ifconfig eth0 down
```

this will take the named interface (eth0) down 

then to restart it use

```
sudo ifconfig eth0 up
```

where eth0 is the name of your interface

you can get more information on options by entering

```
info ifconfig
``` in the terminal too (same for other commands)

hope this helps

---

### Post by mikeybinec on 2012-03-18
received!!!!! .. find the interface name and I'm good 
 
THANKS:guitar:

---

### Post by winh8r on 2012-03-18
just run 

```
ifconfig
```

on its own and you will get all the interfaces in use displayed


Good Luck.

---

