---
title: "resolv.conf &amp; nameserver?"
date: 2014-08-11
forum: New to Ubuntu
---

### Post by cedric9 on 2014-08-11
I'm pretty new to Linux, and right now I'm running Ubuntu 14.04 LTS on an old 
Pentium 4 with 1.5 GB of Ram.

Recently I started experiencing very slow Internet browsing, and after doing 
some reading I decided to modify my resolv.conf file.  The contents of my 
resolv.conf file are below.  I'm guessing that I probably don't have things 
quite right, although things seem to be loading more quickly now?

================================================================================
# nameserver 192.168.0.1
#search domain.name
#nameserver 127.0.0.1

#nameserver 127.0.0.1      # Use the local resolver first.
#nameserver 208.67.222.222 # OpenDNS
#nameserver 208.67.220.220 # OpenDNS
nameserver 8.8.8.8
nameserver 8.8.4.4
domain example.com
search example.com
================================================================================
Hopefully in the future I'll know enough to help others, but right now I'm 
still stumbling along.

---

### Post by SeijiSensei on 2014-08-12
That won't survive a reboot.  Ubuntu uses a program called "resolvconf" to manage /etc/resolv.conf.  Another program, dnsmasq, provides the actual DNS information.

To ensure that your changes persist, you must edit the file /etc/resolvconf/resolv.conf.d/head and add the entries you are using there.

Usually dnsmasq will use the nameservers provided by a DHCP server when you first boot up.  Do you have your router configured to hand out the DNS server addresses?

---

### Post by nerdtron on 2014-08-12
I see that you want to speed up your internet browsing speed by using 8.8.8.8 and 8.8.4.4 DNS servers. If you have a GUI, you can setup a static IP address on the network manager and add the custom DNS entries in there. No nee to edit the resolv.conf file as it wasn't meant to be manually edited by default.

---

### Post by cedric9 on 2014-08-16
Sorry for the late reply, I've been sick for a few days. I've downloaded Wicd  Network Manager, but I'm not sure what I should put into the fields titled DNS Domain, & Search Domain?

---

### Post by cedric9 on 2015-08-10
I'm sorry for the late reply, I was in the hospital with a bad case of pneumonia a few months back, and I completely forgot about this.  I simply left those fields tiled DNS Domain, & Search Domain blank in Wicd Network Manager, and it seemed to work find. I've been using it that way for about a year now.

---

