---
title: "Deleting Programs"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by bamend on 2008-04-27
How can I delete Frostwire? I added it and don't know how to get rid of it

---

### Post by lamalex on 2008-04-27
Depends how you installed it, can you enlighten us?

---

### Post by bamend on 2008-04-27
I installed with the deb file.

---

### Post by Nythain on 2008-04-27
should show up in add/remove programs... if not then
sudo dpkg -r frostwire
might/should do the trick, though im not 100% sure wether dpkg will work with just the app name or if you need to know the exact name of the deb that was installed

you could probably
dpkg --help
to get all the info on dpkg, installing, removing, and purging you could ever need to correct any error in my syntax there

---

### Post by Michael.Godawski on 2008-04-27
First look for frostwire in Synaptic. If there is an entry check the box and mark for removal.

Or you can run in terminal

```
sudo dpkg -r name of package
```

---

### Post by bamend on 2008-04-27
Thanks.  Worked like a charm.

---

### Post by vba_djs on 2008-04-27
> **Michael.Godawski said:**
> First look for frostwire in Synaptic. If there is an entry check the box and mark for removal.

Or you can run in terminal

```
sudo dpkg -r name of package
```

Yesterday I incorrectly tried to install a Brother printer driver onto a 7.10 server and the package never finished installing.

I tried both sudo dpkg -r hl1440lpr and sudo apt-get remove hl144lpr without any luck.  I received the following error messages.

1 not fully installed or removed
/var/lib/dpkg/info/hl1440lpr.postrm: 3: /etc/init.d/lpd: not found
subprocess post-removal script returned error exit status 127

sub-process /usr/bin/dpkg returned an error code (1).

I even tried synaptic from the desktop. I found the package, but the remove command was inactive for that package.

Is there a way that I can remove this before I try re-installing the printer drivers?

Thanks,

NEVERMIND: I found the solution relating to the exact package at this link.

[http://www.linuxquestions.org/questions/linux-newbie-8/package-unremovable-with-exit-status-127-470122/]("http://www.linuxquestions.org/questions/linux-newbie-8/package-unremovable-with-exit-status-127-470122/")

---

