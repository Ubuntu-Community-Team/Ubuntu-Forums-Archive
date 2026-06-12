---
title: "Ubuntu network settings question...."
date: 2020-08-12
forum: New to Ubuntu
---

### Post by ferfykins on 2020-08-12
So with windows, you have an option to set network settings to say you're on a public network or a private network....
If you set to private, then other compturs on network can access you.... So i'm always setting public network
How to do this with ubuntu? thanks guys

---

### Post by TheFu on 2020-08-12
Linux isn't Windows.  Only about 20% of the ideas apply.
The easiest firewall interface, is **gufw**.  The firewall itself is built into the kernel.

If you want other systems to have access, you'll need to install and configure network services for each protocol you want to support. Then those systems need to have a way to get DNS lookups for any systems on the LAN. Some routers wll do that or you can set a dns for your LAN, if you like. That's normal P networking stuff that has been around 40+ yrs.  For just a few devices, often editing the /etc/hosts files is the easiest answer after setting static IPs or "dhcp reservations". 

you can try usng autoconf stuff f you like - {hostname}.local - just replace the hostname with whatever host you want to access, but you'll still need to setup a server for any protocol to be used.  The easiest for Unix systems is ssh. That gets you scp, sftp, sshfs, rsync, and about 20 others.  Connections to these aren't limit to the LAN, but if you don't open any inbound ports on the WAN router, there's no danger.  Plus all shh-based protocols are secure enough for use on the internet, provided ssh-key authentication is used, never passwords.

---

