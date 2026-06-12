---
title: "[SOLVED] Internets Drops Constantly"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by garyedwardjohnston on 2008-07-11
I've been searching for a while now and found many older posts about my particular problem but nothing recent, thus the new post.

I have a 8.04 fresh installation (including updates) with nothing else except Ubuntu Restricted Extras and Tremulous installed.

My internet keeps dropping.  Every 1 or 2 minutes it drops for about 5-10 seconds.  This makes the internet very annoying.

How can I fix this?

Thanks,
Gary

---

### Post by Inxsible on 2008-07-11
> **garyedwardjohnston said:**
> I've been searching for a while now and found many older posts about my particular problem but nothing recent, thus the new post.

I have a 8.04 fresh installation (including updates) with nothing else except Ubuntu Restricted Extras and Tremulous installed.

My internet keeps dropping.  Every 1 or 2 minutes it drops for about 5-10 seconds.  This makes the internet very annoying.

How can I fix this?

Thanks,
GaryJust the wireless? Same problem on Windows - in case you have a dual boot?

You sure its not a hardware problem or an ISP problem

---

### Post by dca on 2008-07-11
If it is wireless (I'm thinking it is), what kind of card and what driver(s)/firmware are you using, ie:  native Intel driver, madwifi, ndiswrapper, etc.
 
The only time I've encountered this was w/ Fedora/RHEL/CentOS using their 2.6.18 kernel which (apparently, correct me if I'm wrong) was a hybred 2.6.17 kernel.  Either NM or the kernel was causing disconnects every timeout (10mins or so).  It would drop and indicate such, then reconnect.  It was more annoying than anything.  Could never figure out if it was NM .64 or something else relative to the kernel...

---

### Post by garyedwardjohnston on 2008-07-11
It is a wired connection, connected directly to the cable modem.

I have a wireless card and would expect this behavior if I was using it but I'm talking about constant drops from my wired connection.

I was actually hoping to learn how to combine and use both at the same time but want to solve this problem first.

---

### Post by dca on 2008-07-11
[http://ubuntuforums.org/showthread.php?t=634402](http://ubuntuforums.org/showthread.php?t=634402)
 
...I don't know if the above will help if it's similar but I'll look...  In Windows trying to use both the NIC & WiFi NIC in tandem never went well...  Never tried on a *nix platform.

---

### Post by dca on 2008-07-11
By the by, in your network settings dealie, is it set for 'Romaing mode' or simply DHCP?  Also when the connection drops is anything listed in 'syslog'?

---

### Post by garyedwardjohnston on 2008-07-11
PERFECT...I changed from roaming mode to DHCP, whatever that is, an now I have a solid connection :)

---

