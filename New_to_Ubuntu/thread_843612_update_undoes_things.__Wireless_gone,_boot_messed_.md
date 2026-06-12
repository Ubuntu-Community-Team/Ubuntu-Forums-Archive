---
title: "update undoes things.  Wireless gone, boot messed up"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by jemvyc on 2008-06-28
I'm running Ubuntu 8.4  I was on cloud 9 after finding Bruno Abinader's post on getting Atheros wireless to work on a Acer laptop.  All was well.  Then I ran the latest update using the Atheros wireless adapter.  Wireless is now gone and I can't get it back.  Meanwhile my boot file has been changed and grub tries to boot windows on hd0,0 where there is nothing but Vista trash.  How do others work with this?:(

---

### Post by cmnorton on 2008-07-02
1) As to booting, search for posts in these forums -- there are tons of them -- of reconstructing your boot sector and rebuilding grub. I am sorry that is not a direct answer, but this subject in particular is covered in many places. I myself would have to go look it up, as it's not something I do every day.

2) As to wireless, you're probably going to have to rebuild your /etc/network/interfaces file, starting back to its barebones form:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

If you did an upgrade and this happened, post this as a bug in Launchpad. Post as much information as you can. Please try to find the update logs in /var/logs.

---

### Post by jemvyc on 2008-07-07
Thanks  Finally I have it back to working.  By now Ubuntu wants to update again.  I am reluctant to try until I get some advise on how to structure my boot setup.

Just for the record, I have Hardy, Vista and XP on an Acer 5315-2153 laptop.  Right now, Grub offers windows or 4 different versions of Hardy. After being selected in Grub the windows boot manager then offers XP or Vista. 

I'll try searching for multi op system setup unless you have another idea.

Jim

---

