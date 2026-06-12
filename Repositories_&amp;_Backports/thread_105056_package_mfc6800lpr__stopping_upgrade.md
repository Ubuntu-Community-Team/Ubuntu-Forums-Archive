---
title: "package mfc6800lpr  stopping upgrade"
date: 2005-12-17
forum: Repositories &amp; Backports
---

### Post by timczer on 2005-12-17
I was trying to get a printer driver installed for my printer.  The deb package mfc6800lpr was installed.  this package now seems to be stopping me from doing any dist upgrade.  If I try to remove it, I get the error: Removing mfc6800lpr ...
/var/lib/dpkg/info/mfc6800lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
and apt-get errors out.  I get the same thing through synaptic.  How do I remove this program?

The mfc6800lpr.postrm file simply has the line /etc/init.d/lpd restart in it. I do not have /etc/init.d/lpd on my system.  can I remove the mfc6800lpr.postrm file and get this to work?

edit: Never mind, I backed up the mfc6800lpr.postrm file with another name, removed the first one and ran the upgrade and it went through without a hitch.

---

### Post by jonbuntu on 2007-03-07
I was having the same problem. I couldn't touch that file or anything in the /var directory and below, with my default login name. I found that I had to enable the system administrator to login. Once I did that, I logged-in as root, browsed to find that file, edited it to comment out the last line, then saved it. I then logged out as root, logged-in as my default user, went to System / Administration / Synaptic... and then selected to remove the mfc6800lpr. It worked - no error message. When I went back to the folder where the mfc6800lpr.postrm file was, it was still there, but now it is no longer causing problems. I can upgrade/install/remove packages with no problem.

---

