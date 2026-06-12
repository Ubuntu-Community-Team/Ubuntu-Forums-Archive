---
title: "enigmail installed but not available in Thunderbird"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by rogererens on 2008-09-23
I am running Thunderbird 2.0.0.16 on Ubuntu8.04 with a profile from my Windows Vista folder. Synaptic shows that enigmail is installed already (2:0.95.0-0ubuntu5), but I don't have an openPGP menu in Thunderbird. I also cannot see it in the list of add-ons. When I download the enigmail-0.95.7-tb+sm.xpi and try to install it, I get a message that it is not compatible with 2.0.0.16.

Any suggestions on how to proceed?

Thanks,

Roger

---

### Post by Mornedhel on 2008-09-23
I just installed enigmail from the repositories. Restarted Thunderbird and the OpenPGP menu was available.

---

### Post by rogererens on 2008-09-23
Thanks for your quick reply. Can you tell me also which version, and which repository you used?
Reinstalling using Synaptic does still not give me the menu.

---

### Post by Mornedhel on 2008-09-23
thunderbird : 2.0.0.16+nobinonly-0ubuntu0.8.04.1 from hardy-updates
thunderbird-gnome-support : 2.0.0.16+nobinonly-0ubuntu0.8.04.1 from hardy-updates
enigmail : 2:0.95.0-0ubuntu5 from hardy

I have no particular repositories installed except Medibuntu, but as you can see my Thunderbird is from the Hardy repositories. My sources.list :

```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://packages.medibuntu.org hardy free non-free
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe

```

---

### Post by rogererens on 2008-09-23
Well, I have the same versions here. So it must have got something to do with the profile on the Windows folder.

---

