---
title: "[SOLVED] Epson printer on XP"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by gimmejimmy on 2008-10-09
Hi, I'm trying to setup network printing to an Epson Stylus Photo 925 printer connected to a WinXP machine.  I used the localhost:631 page to do it.  I put smb://192.168.2.100/925B as the URI.  When I click "Print a test page" nothing seems to happen.
The printer is shared on XP with a share name of 925B.  On the Ports tab "Enable bidirectional support" is unticked.  The XP machine is running Comodo firewall but local network communications are allowed.  When I click "Print a test page" the firewall shows a connection from the Ubuntu machine to XP.

Now for some reason as I was typing this when I go to localhost:631/admin it shows 404 not found.  Help!

---

### Post by Paqman on 2008-10-10
You should be able to set this up through Admin > Printing. Just elect to use a "Windows printer through SAMBA" and see if you can browse to and select it.

I have an Epson Stylus printer that i'm connecting to through smb and it was dead simple to set up.

---

### Post by gimmejimmy on 2008-10-10
Thanks.  Can you give me an example of what to type in for the device URI?  It doesn't autodetect for me.

---

### Post by gimmejimmy on 2008-10-10
Ok this is solved now.  I logged out of xfce and logged in to a Gnome session.  The setup screen there asked me for the Windows credentials, the xfce setup didn't.

---

