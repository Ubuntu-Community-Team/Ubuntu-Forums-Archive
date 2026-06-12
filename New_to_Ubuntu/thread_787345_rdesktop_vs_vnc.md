---
title: "rdesktop vs vnc"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-08
i'm trying to decide whether to use rdesktop or vnc for connecting to a windows xp vm from ubuntu 8.04... at this point i'm interested in knowing which will allow me to have a remote connection automatically start when ubuntu starts up- can either of these do this?  thanks.

---

### Post by dynamethod on 2008-05-08
xtightvncserver can yep

---

### Post by Matt26 on 2008-05-08
> **dynamethod said:**
> xtightvncserver can yep

what is xtightvncviewer?  does it work with vnc server?

---

### Post by scxtt on 2008-05-08
the ability to get RDC connection to XP comes up w/ the XP OS ... so if it's enabled and the VM is on, you'll be able to connect via RDP ... VNC can be configured to be running as a service on boot also.

---

### Post by Matt26 on 2008-05-08
thanks for the info... which is more secure for connecting to a remote system?  i've read that vnc doesn't use a secure connection for passing data back and forth?

---

### Post by scxtt on 2008-05-08
i'm not to sure how secure RDP is, but i've heard that VNC just sends unencrypted screenshots over the network, so someone could sniff out port 590* and reconstruct the images ~ somewhat of a risk i guess ... but you can also tunnel VNC traffic through SSH, which is encrypted ... i personally use RDP to connect to my server2k3 VM at home, and from there roam around my network ... so there's really only 1 way in.

---

