---
title: "General Annoyances with networking"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-09-13
So I can't ping any of my ubuntu machines based on their host names. I can ping their ips just fine and I can even pin other windows machines, just none of the linux ones.

I also can't ping from any Ubuntu machine to a host name.  Pings to ip addresses work fine.  In general, networking under ubuntu is really starting to irritate me.

Any ideas?

---

### Post by Zzl1xndd on 2008-09-13
Host names are a feature of NetBios, do you have Samba installed on your Linux Boxes? and If so do you have a firewall on them?

---

### Post by txcrackers on 2008-09-13
> **tweakedenigma said:**
> Host names are a feature of NetBios
Not entirely true - host names are handled through DNS for standard internet protocols.

CryptiniteDemon: if you have static IP addresses for each of your machines, you can edit the file */etc/hosts* and map each IP address to a hostname. If you're using DHCP, you might be able to map names through the DHCP server (home router?).

Or you can set up SAMBA on each machine, but you won't be able to ping them because ping doesn't use SMB (nor does any other standard internet protocol like FTP, SSH, etc.).

---

### Post by skippuff54 on 2008-09-13
you might need to edit your /etc/hosts file in Ubuntu order to map IP addresses to hostnames

additionally you might need to edit your hosts file in Windows. in XP, it should be in c:\windows\system32\drivers\etc\hosts. open with notepad

---

### Post by CryptiniteDemon on 2008-09-13
> **skippuff54 said:**
> you might need to edit your /etc/hosts file in Ubuntu order to map IP addresses to hostnames

additionally you might need to edit your hosts file in Windows. in XP, it should be in c:\windows\system32\drivers\etc\hosts. open with notepad

There's no way I'm being that cheap and doing host-file name resolutions. It may be a home network, but I still like to keep scalability in mind. Right now my cheap little router has a dhcp server built into it, and it stores the names just fine.

I dunno, I'm just gonna end up setting up my own DNS and WINS servers to get it over with.  I haven't had any luck with samba.  For some reason it really hates me.

---

