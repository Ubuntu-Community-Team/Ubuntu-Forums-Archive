---
title: "Resolving Duplicate Errors"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by roger6 on 2013-09-01
When I opened synaptic package manager I received the following message:

"W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_binary-i386_Packages)"

How do I resolve this issue?

Thanks,
roger

---

### Post by davetv on 2013-09-01
If you are running a 64 bit Ubuntu then the bottom line is the problem (i386). If you are running the 32 bit edition then the top line (amd64) is the problem. Using "sudo" edit the /etc/apt/sources.list file and comment out either the offending i386 or amd64 line in the file (by putting a # in front of the line).

---

### Post by ibjsb4 on 2013-09-01
This should work for you

[http://www.howopensource.com/2012/10/w-duplicate-sources-list-entry-ubuntu-12-10-12-04/](http://www.howopensource.com/2012/10/w-duplicate-sources-list-entry-ubuntu-12-10-12-04/)

This link suggest that you remove the duplicate.  I suggest that you just **UN**check it first and then try synaptic.  When you are sure you have the right duplicate, then remove it.

---

