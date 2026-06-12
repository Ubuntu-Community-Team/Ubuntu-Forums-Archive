---
title: "Upgrading to 12.04 hung at starting denyhosts"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by NullEgo on 2013-01-03
I'm running a headless Ubuntu Server.  I decided to upgrade from 11.10 Oneiric to 12.04 Precise over SSH and it has hung at "* Starting DenyHosts denyhosts".  I cannot detach from the screen but I can open another ssh session or close the terminal window, reconnect, and reattach to the screen.  Everything appears to be working as usual except for this hung screen.  How should I resolve this?  The OS already greets me when I login as being 12.04 so if I restart the machine will it think it's partial update to 12.04 as complete?

FYI, I'm a software developer so I'm very familiar with computers but I'm not experienced in linux much at all.  I started hosting this server a few months back as a small project to play around with LAMP, samba, etc.

---

### Post by cariboo on 2013-01-03
Check out the logs in /var/log, either syslog, or auth.log

---

### Post by NullEgo on 2013-01-03
Thanks for the reply.  I checked out the logs but didn't see anything related by scanning it.  Any idea what I should be looking for so I can try to grep it?  My syslog is crowded with smtpd errors due to a misconfigured postfix and my authlog is filled with brute force attempts (news to me).  Both problems I'll fix but I would think they are unrelated.

---

