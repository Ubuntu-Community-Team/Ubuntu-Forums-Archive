---
title: "package error"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by bendjamila39 on 2014-10-16
Hello for All,
I'm new in Ubuntu and I typed "sudo apt-get install rrdtool" in a terminal window in Instant Contiki.
I have this error: can please some one help me
thank'
regard
benda
[sudo] password for user: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by Bashing-om on 2014-10-16
bendjamila39; Hi ! Welcome to the forum .

Probably a corrupted control file.
Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

to remove the control files and "update" to rebuild them.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

