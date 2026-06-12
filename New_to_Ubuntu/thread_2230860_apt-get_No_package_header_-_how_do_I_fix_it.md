---
title: "apt-get No package header - how do I fix it ?"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by arnoversfeld on 2014-06-21
At a terminal I did the following:

arno@arno:~$ sudo apt-get install bleachbit
[sudo] password for arno: 

And got the result:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

How do I fix the problem ? Please help.

---

### Post by Bashing-om on 2014-06-21
arnoversfeld; Hi !

That error condition is generally indicative of corrupted control file(s).
Try this:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
to remove, rebuild, update the data bases, and upgrade the installed software to what is current.

[INDENT][INDENT]most likely yes
[/INDENT][/INDENT]

---

### Post by arnoversfeld on 2014-06-22
Hi Bashing-om.
Thank you so much !
I'm running ubuntu 14.04 so I didn't do the upgrade.
The first two lines did the trick and everything is back to normal after the update.

---

### Post by Bashing-om on 2014-06-22
arnoversfeld; Great.

However, do the "sudo apt-get upgrade" // that is not to do a release upgrade, but only upgrades the installed software as is current within the repository(same function that is performed with ubuntu Software Center). To upgrade to a newer release is a different command.

As this matter is now concluded;
Please mark this thread solved; aides others seeking the solution,
 helps keep the forum clean and 
precludes others miss-directing efforts to aid.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by ddecampos1 on 2014-07-01
Nice one Bashing-om!  your fix works like a charm!  Thnx!

---

### Post by Bashing-om on 2014-07-01
@ ddecampos1; My Welcome to the forum.

Glad to be able to help, great it worked out.

[INDENT]come back when you can stay longer
[/INDENT]

---

