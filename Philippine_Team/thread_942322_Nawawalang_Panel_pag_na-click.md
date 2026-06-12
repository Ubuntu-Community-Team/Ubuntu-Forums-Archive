---
title: "Nawawalang Panel pag na-click"
date: 2008-10-09
forum: Philippine Team
---

### Post by jerryheavyarms on 2008-10-09
Patulong naman po.

Yun pong Panel ko, pag iki-click ko na po yung shutdown icon is nawawala yung panel.. 
Panu po gagawin ko para mag locked po sya..
Salamat po!

---

### Post by loell on 2008-10-09
paki tingnan mo sa properties nang panel, baka naka autohide?

---

### Post by jerryheavyarms on 2008-10-09
Sige po, iche-check ko po..
....*after a few minutes....*
hindi naman po sya naka autohide eh. Ang natatandaan ko po, may napress akong key tapos ganun na po yung behaviour nya. Everytime na ki-click ko po yung shutdown icon, nawawala po sya..

salamat po sa pag reply

---

### Post by loell on 2008-10-09
mukhang bug yata 'to, :(  na wala pang sulosyon.

[http://ge.ubuntuforums.com/showthread.php?p=5650204](http://ge.ubuntuforums.com/showthread.php?p=5650204)
[http://ubuntuforums.org/showthread.php?t=940213](http://ubuntuforums.org/showthread.php?t=940213)

kung gusto mo attach mo lang yung panel config file mo. baka may makita tayong kakaiba.

```
gconftool --dump /apps/panel > my-panel-settings.xml
```

paki attach na lang sa **my-panel-settings.xml**

---

### Post by jerryheavyarms on 2008-10-09
oo nga po.. katulad sa thread na binigay nyo po yung problem ko.. nakakalungkot naman..
Eh kung i-reinstall ko po yung gnome desktop nya.. uubra kaya?

---

### Post by loell on 2008-10-09
yung previous setting ng gconf pa rin kasi ang gagamitin nya, kaya palagay ko, andun pa rin yun after gnome reinstall.

---

### Post by chr05210084 on 2008-10-15
Try mong i delete ung .gnome2 .gconf .gconfd .metacity na mga folder, tapos restart mo ung pc mo, para mabalik sa default ang settings ng desktop mo.

```

cd /home/username
sudo rm -rf .gnome2 .gconf .gconfd .metacity 
sudo reboot

```

Please visit this link [http://www.cahilig.org/restore-broken-ubuntu-desktop](http://www.cahilig.org/restore-broken-ubuntu-desktop) for more info.

---

### Post by jerryheavyarms on 2008-10-28
Sir Richard,
It works! Thanks a lot po!
Gayundin sa mga nagreply, salamat sa inyo.
Astig!:guitar:

---

