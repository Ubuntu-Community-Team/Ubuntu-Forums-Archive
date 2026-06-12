---
title: "[SOLVED] Is there such a thing as a hardware address (MAC) wildcard?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by jflarm on 2008-06-09
I am learning about the dhcpd daemon, and I'd like to know if I can set a wildcard for, let's say, all the hardware addresses (MAC) 00:13:02: xx : xx : xx get certain ip from a range of ip addresses...

---

### Post by jflarm on 2008-06-12
anyone???

---

### Post by niteshifter on 2008-06-12
Hi,

It's possible - but I've never done this myself, just admired the setup - looked rather complex. I do know these man pages are what you need:

dhcpd.conf
dhcp-eval
dhcp-options

The site linuxmanpages.com might useful - get all three into separate tabs of your browser.

---

### Post by jflarm on 2008-06-18
Thank you....I'll look at that...

---

### Post by barney385 on 2008-06-18
man netstat

---

### Post by Dedoimedo on 2008-06-18
Hello,

It is possible to assign per-host IP based on MAC address.

There are two possible ways to do it - by vendor or maybe by sub-class. Try them, see if it works (in /etc/dhcpd.conf file).

By vendor, example:

class "vendor-1" {
  match if option dhcp-vendor-identifier = "broadcom";
}

class "vendor-2" {
  match if option dhcp-vendor-identifier = "abit";
}

subnet 192.168.1.0 netmask 255.255.255.0 {
  pool {
    allow members of "vendor-1";
    range 192.168.1.100 192.168.1.120;
  }
  pool {
    allow members of "vendor-2";
    range 192.168.1.130 192.168.1.140;
  }
}

You can try replacing the string of the name of the vendor with the unique parts of the mac address instead, see if this works.

In other words: dhcp-client-identifier="xx : xx : xx" and dhcp-client-identifier="yy:yy:yy"

Not sure if this works, never tried it, though.


By sub-class:

class "vendor-1" {
  match pick-first-value (option dhcp-client-identifier, hardware);
}
class "vendor-2"
  match pick-first-value (option dhcp-client-identifier, hardware);
}

subclass "vendor-1" aa:bb:cc:::;
subclass "vendor-2" aa:bb:dd:::;

subnet 10.0.0.0 netmask 255.255.255.0 {
  pool {
    allow members of "vendor-1";
    range 10.0.0.11 10.0.0.50;
  }
  pool {
    allow members of "vendor-2";
    range 10.0.0.51 10.0.0.100;
  }
}


Not sure if this will work, but you can try.

HOWEVER, if you use the subclass and specify each mac address separately in full, let's say 10 entries for subclass 1 and 13 entries for subclass 2, this will work.

Omitting parts of the MAC might work as a wildcard, but it might not work ...

Cheers,
Dedoimedo

---

