---
title: "installed firestarter firewall, do i need to do anything to it?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by srossnz on 2008-05-28
I installed firestarter firewall and it is now running.  Does this mean it is offering me protection or do i need to configure it specifically?  I am just trying to secure my ubuntu desktop but have no idea what i'm doing..

Thanks

---

### Post by sayakb on 2008-05-28
Firestarter blocks everything by default. So you might not be able to receive packets, until you allow them. Whenever you find out that Firestarter blocks something that you requeted for/initiated, (the tray icon should go red), just open firestarter, goto the events tab, right click on the event you want to allow and select "Allow inbound services from host/on port".

---

### Post by srossnz on 2008-05-28
So how can i be sure it's working?  I installed it and my internet and pidgin never got blocked, I see the icon and it's running.  Thanks!

---

### Post by sayakb on 2008-05-28
Yes, until its blue, it hasn't blocked anything. It will not even block your FTP/HTTP file upload/download, but would stop anything coming under UDP/ICMP/SMB etc.

---

### Post by srossnz on 2008-05-28
> **LinuxIsInnovation said:**
> Yes, until its blue, it hasn't blocked anything. It will not even block your FTP/HTTP file upload/download, but would stop anything coming under UDP/ICMP/SMB etc.

Cool, think this is good enough for my desktop security?  Is there anything else you recommend that a noob can get his head around?

---

### Post by sayakb on 2008-05-28
Firefox monitors all ports of your computer and blocks/allows traffic on same. If you are just starting over with ubuntu, try the two links in my signature below for a complete documentation on almost everything you might need :)

---

### Post by hyper_ch on 2008-05-28
I just wonder why you did install firestarter first place. Normally you don't need it.

---

### Post by srossnz on 2008-05-28
> **hyper_ch said:**
> I just wonder why you did install firestarter first place. Normally you don't need it.

A guy I know on another forum got hacked somehow.  Likely his fault but beein a noob I thought it wouldn't hurt to have something shadow me..

---

### Post by sayakb on 2008-05-28
I just like the ICMP filtering in firestarter, nothing else. So unless you are connected to LAN where people are trying to steal your password using WinPCap drivers, you don't need firestarter.

---

### Post by hyper_ch on 2008-05-28
> **srossnz said:**
> A guy I know on another forum got hacked somehow.  Likely his fault but beein a noob I thought it wouldn't hurt to have something shadow me..

Why and how did he get hacked... that's more important than just to apply "security things"... by a default installation you don't need any configuration of iptables at all (in the end Firestarter is just a config tool for iptables)

---

