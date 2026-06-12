---
title: "Problems with DNS (I think...)"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by nick168 on 2015-01-25
So here's my long, exciting, stressful journey to the situation I'm in now (I'll try to keep it as short and readable as possible).

I bought a dirt cheap computer and threw in a 250gb hard drive and installed Ubuntu Server 14.04.1 LTS. I have almost no experience with Linux so you could imagine how much fun I had looking up commands and reading all about Samba, Apache2, MythTV, Daemon-Transmission, etc... Somehow I got everything set up right and now I can share files between all my computers on the network. I also have daemon-transmission running on port 9091, and I used no-ip.com to get a domain name so I can *download* (;)) files from the internet and have them sent straight to the server, so I don't have to download/transfer it to every computer. Now I'm trying to set up Apache2 and WebDAV so I can access all of these files from a web browser. I started doing this last night and I just noticed the problem that I'm about to explain today, so I can't really pinpoint where I went wrong. **FYI... I set my IP to static by changing the /etc/network/interfaces file**

But basically, I can access my server from all other computers, and everything works, but I can't run sudo apt-get update. Here is the output: 
 
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```
And the output for when I try to install apache2-utils, which I need to set up WebDAV for browser file-sharing:

```
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apache2-utils i386 2.4.7-1ubuntu4.1  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main apache2-utils i386 2.4.7-1ubuntu4.1  Could not resolve 'security.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.4.7-1ubuntu4.1_i386.deb  Could not resolve 'security.ubuntu.com'
```

And pinging domain names (google.com, facebook.com, etc) I get: 
```
ping: unknown host google.com
```

However, pinging IP addresses works fine. So I think its something to do with DNS.

Thanks everyone, sorry its such a long post. Post if you need anything clarified (I'm somewhat confused myself).

---

### Post by steeldriver on 2015-01-25
Hello and welcome to the forums

> **nick168 said:**
> **FYI... I set my IP to static by changing the /etc/network/interfaces file**

Please post the current contents of the file.

---

### Post by nick168 on 2015-01-26
Here it is. The only thing i changed was eth0, i didn't change the loopback 

  
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
      address 192.168.1.9
      netmask 255.255.255.0
      gateway 192.168.1.1
nick@Elenor:~$

---

### Post by papibe on 2015-01-26
Hi nick168.

Check this [thread]("http://ubuntuforums.org/showthread.php?t=2261695&p=13211965#post13211965"), specially post #8.

Let us know if that helps.
Regards.

---

### Post by nick168 on 2015-01-26
Papibe,

Thanks, that helped a lot, but I don't think my router supports reserving... or at least I can't find it anywhere on the admin tab. (I have a Netgear N600). And I'm not sure exactly how to mess around with the isc-dhcp-server installed on Ubuntu. 

But do you think the problem started when I changed from dynamic to static IP? I don't really understand how this would screw up its ability to convert from a domain name to an IP.

Thanks!

**EDIT:** Just noticed this when playing around some more. My /etc/resolv.conf is completely blank... I know its auto-generated and I'm not supposed to edit this, but something tells me this file shouldn't be empty.

---

### Post by steeldriver on 2015-01-26
If you add a dns-nameservers field to your interface definition (just like in the post that papibe linked) pointing to the actual DNS server IP for your LAN (which is probably the same as your gateway IP, i.e. your LAN router is performing both functions), then when you restart the networking service, the /etc/resolv.conf file should get populated accordingly.

This is separate from any considerations of static versus DHCP-with-reservation.

---

### Post by nick168 on 2015-01-26
IT WORKS! Okay so I think everything was right that I did up to this point... maybe not. But either way this fixed it:

I simply went into /etc/resolvconf/resolv.conf.d/base and added the two free google nameserver (8.8.8.8 and 8.8.4.4) and I can now ping away at anything I want. Thanks so much everyone.

---

### Post by steeldriver on 2015-01-26
Although that may have worked, afaik it's not the recommended solution. Is there any particular reason you don't want to add them via your /etc/network/interfaces file?

---

