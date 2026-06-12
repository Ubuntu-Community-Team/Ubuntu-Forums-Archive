---
title: "installation problem"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by amiralex32 on 2013-06-04
i'm trying to install sudo apt-get install subversion package but 
 Reading package lists... Error!E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/eg.archive.ubuntu.com_ubuntu_dists_raring_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
how can i solve this problem

i have tried
sudo rm /var/lib/apt/lists/* and sudo rm /var/lib/apt/lists/* -vf

 rm: cannot remove ‘/var/lib/apt/lists/partial’: Is a directory
also i think i have a notification warning that appear to me says 
an error occured please run manager or aptget from terminal

---

### Post by BioHazardTM on 2013-06-04
This can be caused by an accidental close of apt, synaptic or something like that, try this please: **sudo rm ****/var/lib/apt/lists/**[B]*

[/B]This will remove all your package lists, and after that, you'll have to do **sudo apt-get update** to restore all lists.

---

### Post by fantab on 2013-06-04
Try:
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by amiralex32 on 2013-06-04
[COLOR=#000000]i have tried[/COLOR]
[COLOR=#000000]sudo rm /var/lib/apt/lists/* and sudo rm /var/lib/apt/lists/* -vf[/COLOR]

[COLOR=#000000]rm: cannot remove &#8216;/var/lib/apt/lists/partial&#8217;: Is a directory[/COLOR]
[COLOR=#000000]also i think i have a notification warning that appear to me says [/COLOR]
[COLOR=#000000]an error occured please run manager or aptget from terminal[/COLOR]

---

### Post by fantab on 2013-06-04
How about:

```
$ sudo -i

 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update


```

---

