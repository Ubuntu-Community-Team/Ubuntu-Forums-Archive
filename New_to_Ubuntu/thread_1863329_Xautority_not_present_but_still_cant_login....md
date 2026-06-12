---
title: "Xautority not present but still cant login..."
date: 2011-10-17
forum: New to Ubuntu
---

### Post by natedogg23 on 2011-10-17
i started a new user account but have no permission to do anything even though i set it up to in users and groups. i cant even mount an sd card!!!!???? i desperately need my original login to work but wont. tried to remove Xauthority but it says no such file. also after 11.04, every time i give a sudo command it says unable to resolve host then eventually asks for my pw. i have a 10.10 disk id like to downgrade to, hope its possible but cant run it from the newuser account. can anyone help???

---

### Post by rburkartjo on 2011-10-18
nat is there an old xauthority file in your home folder. it might be called x authority backup. might be hiddened.
here is how i fixed this issuse

here is how i fixed. i apparently had a corrupt file
.Xauthority backup in my home folder. so i deleted. open a virtual termnal and ran sudo dpkg-reconfigure gdm set it to lightdm and rebooted.

---

