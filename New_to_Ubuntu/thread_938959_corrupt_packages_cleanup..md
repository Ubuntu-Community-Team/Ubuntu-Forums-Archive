---
title: "corrupt packages cleanup."
date: 2008-10-05
forum: New to Ubuntu
---

### Post by eignemhs on 2008-10-05
I recently installed Hardy on 4 pc's now.  Had a virus issue in the office and Ubuntu seemed like a good solution.

Well I toasted a few cdroms incorrectly and ended up burning a ReWriteable.  Installed flawlessly on 2 computers and when I went to install on my laptop, so I could support the users a better but something happened to the CD.  It installed on the 3rd try, but there was one or two corrupted packages.  Not severly corrupted, but enough so that the login prompt has a huge font.. ~120px font where I couldn't see the letters as I typed.  After that, everything looked fine.

Odd.

I retoasted the RW CD for the next install and that fixed the issues, but I've been using my laptop and have a few settings changed so I don't want to do a full re-install on it.

Searching through the forums I found debsums and hunting through man pages on apt-get, --reinstall.

$ sudo apt-get debsums
$ sudo debsums -s
debsums: no md5sums for at
debsums: no md5sums for binutils
debsums: no md5sums for binutils-static
debsums: checksum mismatch gdm file /etc/gdm/gdm.conf-custom

Ah-ha!

The gdm.conf-custom is suspect for the login prompt font size issue.

After the following command was successfully executed, 

$ sudo apt-get --reinstall install at binutils binutils-static gdm
...

Kudos Ubuntu folks!

That sure beat re-installing!
Hardy is very well done, sweet!
Half tempted to Hardy my Fedora boxes.

---

### Post by Paqman on 2008-10-08
Glad you sorted it. Please mark the problem as "solved".

---

