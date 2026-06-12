---
title: "Can Not Download All Repository Indexes."
date: 2006-01-17
forum: Repositories &amp; Backports
---

### Post by Joy on 2006-01-17
When I start Synaptic manager I get this massege : can not download all repositry indexes and can not resolve dists'. I tried apt-get update in terminal also but there I am getting error source lists.I checked my network setup.Anybody can help me please?

---

### Post by rjwood on 2006-01-17
please post your
 ```
less /etc/apt/sources.list
``` here

---

### Post by Joy on 2006-01-18
Thanks, rjwood for your response.I typed in my terminal as 
sudo less /etc/apt/source.list Response I got NO such file or directory. I was trying to enable Mutiverse and universe after that I am getting error & warning in synaptic manager.This might be the resson?
When i start synaptic i following warning-

W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/breexz-backports Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_breexz-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/main Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/universe Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/multiverse Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http: archive.ubuntu.com/ubuntu/restricted Packages (/var/lib/apt/lists/dists_archive.ubuntu.com_ubuntu_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Sef on 2006-01-18
>  I was trying to enable Mutiverse and universe after that I am getting error & warning in synaptic manager.This might be the resson?

What did you do to try and enable multiverse?  Be specific as possible.

Yes, that is likely the reason.  I once did the same thing.  I got upset and instead of posting how to fix it, I just reinstalled.  I hope that someone has a fix for you.

---

### Post by Joy on 2006-01-18
Thanks Sef. Ihave just edited my last thread .now i hope it is easy for you to suggest the remedy.

---

