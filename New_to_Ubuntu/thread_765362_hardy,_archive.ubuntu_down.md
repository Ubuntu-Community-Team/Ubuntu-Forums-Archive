---
title: "hardy, archive.ubuntu down?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Tavorisch on 2008-04-24
well, the only thing i've done in hardy so far is messed with the repositories enabling unsupported and stuff, ran update manager, and errored out.. set repositories in synaptic back to default. ran update manager again with just another hault. mean while i try a sudo apt-get update and bam. seems as if archive.ubuntu for hardy is down.. or maybe their servers are just to busy with the new release? also i added me into the /etc/sudoers file. ```
# User privilege specification
root, patrick   ALL=(ALL) ALL
``` let me know if anyone else has this problem, frustrating but understandable..

EDIT: when i run sudo apt-get update it goes all the way down to the security/multiverse packages and just haults at 53%, did this because it just haulted on sudo apt-get install build-essential

---

### Post by macogw on 2008-04-24
Too many people are trying at once.  The servers can't handle it.  Try again tomorrow or the day after.

---

### Post by Ub1476 on 2008-04-24
The main servers might be down.. Why did you add yourself to the sudoers file?

---

### Post by Tavorisch on 2008-04-24
cause i'm an idiot and was looking at a hardy (alpha) nvidia how to. maybe the writer has a habit from older releases i have no clue.

---

### Post by Ub1476 on 2008-04-24
Well, in distroes like Ubuntu it's not necessary to edit the sudoers file, because this process is automated. :)

---

### Post by ptcbus on 2008-04-24
If the slow server is the problem try torrents. I used torrents to upgrade and was very quick. I have listed the steps here:[ http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

