---
title: "Can't view local network using smb?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by DoubleMcLovin on 2008-11-16
Using 8.04 I was able to just open nautilus to the network area and navigate my windows network easily. I set up an fstab to mount them localy at boot using static ip addresses so I didn't need to do this for some time. Now I go to install a printer and notice that I can no longer just browse my network like this. I tried using smb://<ip address> and that worked fine, but to configure printer and possible future use I would like to be able to navigate the network using nautilus. Any suggestions on maybe a pack to install?

---

### Post by DoubleMcLovin on 2008-11-16
bump. Any suggestions would be great...

---

### Post by Kellemora on 2008-11-16
Hi DM

Have you SHARED the Printer?

You can also type smbtree to see if it shows up in the list.

sudo apt-get install smbtree if it's not installed.

TTUL
Gary

---

