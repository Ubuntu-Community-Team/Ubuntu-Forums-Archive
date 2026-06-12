---
title: "Upgrading OS w/o downloading?"
date: 2010-10-13
forum: Philippine Team
---

### Post by maxwell23 on 2010-10-13
patulong naman po sana, gusto ko po kc mag upgrade ng 10.04 to 10.10 na walang download dahil may ISO nko ng 10.10 eh at anu po ba mga dapat intindihin ko bago ako mag upgrade?

---

### Post by Jechem on 2010-10-13
read my post here:
[http://jechem.blogspot.com/2010/10/ubuntu-1010-maverick-meerkat-on-eeepc.html](http://jechem.blogspot.com/2010/10/ubuntu-1010-maverick-meerkat-on-eeepc.html)

kung gagamitin mo ung ISO mo mawawala ung config mo. backup ka muna tapos install mo 10.10 then restore mo ung files mo from backup

---

### Post by jepong on 2010-10-14
just get the alternate installer iso... mount it and start upgrade. :)

---

### Post by jmazaredo on 2010-10-16
Burn mo nalang ISO, boot mo yung pc then insert mo yung cd

---

### Post by stjohnmedrano on 2010-10-16
in terminal.

$ sudo nano /etc/update-manager/release-upgrades  

and set prompt=normal

to save press ctrl+o then ctrl+x

$ update-manager -d

press the upgrade button.

---

