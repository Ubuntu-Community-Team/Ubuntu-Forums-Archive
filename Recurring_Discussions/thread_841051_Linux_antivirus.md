---
title: "Linux antivirus"
date: 2008-06-26
forum: Recurring Discussions
---

### Post by TorchlightJay on 2008-06-26
Hello,
   I am trying to setup an Ubuntu Linux File and Print Server. I want to have antivirus on this system and i know companies like kaspersky make a proprietary antivirus for Linux but I was wondering if there was an open source equivalent as good or better than the proprietary solutions. Also do these solutions have a Windows or Mac port?

---

### Post by jimv on 2008-06-26
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by mempman on 2008-06-26
Linux is practically immune to viruses.  Read: [http://www.desktoplinux.com/articles/AT3307459975.html](http://www.desktoplinux.com/articles/AT3307459975.html)

However, if you really need to get antivirus software I would try AVScan - search through Synaptic.

---

### Post by TorchlightJay on 2008-06-26
Ya, Linux is virtually virus free but it'll be the file server for some windows machines. That's why I am concerned.

---

### Post by ubuntu27 on 2008-06-26
Clam Antivirus is a popular choice in GNU/Linux.

[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

[http://www.clamav.net/](http://www.clamav.net/)


There is a Windows counterpart called ClamWin. It does not have a on-access real-time scanner however. 

[http://www.clamwin.com/](http://www.clamwin.com/)

---

### Post by barbedsaber on 2008-06-26
I was about to come in here and do the whole linux has no viruses, but if it for a file server, then I suppose it's necessary.

---

### Post by p_quarles on 2008-06-26
> **barbedsaber said:**
> I was about to come in here and do the whole linux has no viruses, but if it for a file server, then I suppose it's necessary.
Moved to Recurring Discussions anyway, as this kind of combines the "does Linux need an anti-virus?" thread with the "is open source as good as commercial software?" goose chase. 

The question of whether a virus scanner would actually be useful depends on what kind of usage this file server would actually get. Since it includes a print server, I imagine that the file server is filling a niche too local to really justify a virus scanner.

---

### Post by quinnten83 on 2008-06-26
> **p_quarles said:**
> Moved to Recurring Discussions anyway, as this kind of combines the "does Linux need an anti-virus?" thread with the "is open source as good as commercial software?" goose chase. 

The question of whether a virus scanner would actually be useful depends on what kind of usage this file server would actually get. Since it includes a print server, I imagine that the file server is filling a niche too local to really justify a virus scanner.

if it will also serve Windows machines, you can't be too careful

---

### Post by cardinals_fan on 2008-06-26
Is the search feature broken today?

---

### Post by veNom_bz on 2008-07-02
> **TorchlightJay said:**
> Hello,
   I am trying to setup an Ubuntu Linux File and Print Server. I want to have antivirus on this system and i know companies like kaspersky make a proprietary antivirus for Linux but I was wondering if there was an open source equivalent as good or better than the proprietary solutions. Also do these solutions have a Windows or Mac port?
kaspersky is a good choice, that is what i use for our windows workstations and what i will begin to use for our file/samba servers. 

i have read disappointing things about clamav and definition updates.

i'd recommend kasperky (not free) or bitdefender (free) there are both at the forefront of windows anti-malware. if you are paying for anti-malware for windows i'd suggest kaspersky as you could purchase a package containting lisences for windows workstations and linux file/samba servers.

---

