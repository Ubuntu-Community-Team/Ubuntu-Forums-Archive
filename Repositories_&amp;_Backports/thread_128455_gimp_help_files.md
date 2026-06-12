---
title: "gimp help files?"
date: 2006-02-11
forum: Repositories &amp; Backports
---

### Post by Herios on 2006-02-11
hello, was trying to use the gimp help and it said could't locate gimp-help files.

I found some old posts with same problem for hoary(I'm using breazy) and they said it was fixed after filing a bug report. no solution was listed.

I can't find any gimp-help in synaptic, tried apt-get install gimp-help and it gave me permission denied error.

figured someone might have easy fix since problem has already been gone over.

thanks for time if possible

---

### Post by jpkotta on 2006-02-11
It sounds like you don't have all the repositories enabled.  Search the [wiki]("https://wiki.ubuntu.com/UserDocumentation") for instructions.  After editing /etc/apt/sources.list, do ```
sudo apt-get update
```to update your package database.

The permission denied error is probably because you forgot to prefix the command with sudo.  Also, you probably want the english help (though I think it gets that by default if your locale is set for en:
```
sudo apt-get install gimp-help-en
```

Try it without the -en first, just as an experiment.

---

### Post by Herios on 2006-02-12
Thanks for info, everything seemed to work.

I tried without the en and it gave me a list of the different language files and said i should pick one.

i apt-got it with en and i can access the manual through help now however at the end of unpackaging i got these messages

W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems


I had already updated though but i did notice when i updated there were some unable to find links, perhaps you might know why this is happening

thanks again though seems this gimp-help issue is solved

the wiki is nice heard some chatter about it but didn't realize there was so much info there

---

