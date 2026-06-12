---
title: "Remove junk in home dir after program deinstallation?"
date: 2008-09-24
forum: Packaging and Compiling Programs
---

### Post by qforce on 2008-09-24
Hi,

I'm trying to create a debian package for my program, and now what I'm wondering about is whether I'm supposed to add a postrm script that removes all the data my program has created in /home/[username]/.[program_name] while it was running.
All other debian packages I've seen so far don't do anything like that, so the /home/[username] folder typically fills up with junk over time, which cannot really be called good practice, right?

Now, suppose I wanted to remove all the junk, then how do I find out which files or folders I have to delete, since I'm not deinstalling as a user, but as root?

Thanks in advance for any answers!

---

### Post by InfinityCircuit on 2008-09-24
No.

[http://www.debian.org/doc/debian-policy/ch-files.html#s-config-files](http://www.debian.org/doc/debian-policy/ch-files.html#s-config-files).

Config files in /etc should be purged, dotfiles will have their master copies in /etc/skel and purging those will be sufficient to be consistent with policy.

---

