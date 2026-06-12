---
title: "Edubuntu/Ubuntu + Windows Network"
date: 2008-02-26
forum: Philippine Team
---

### Post by parenghilton on 2008-02-26
Question: Di ako maka connect sa Windows Network na may internet. 

meron namang natatanggap na IP address me kaso wala talaga lumalabas.

naka router kami.

yung windows na laptop namin isang kabit lang sa router ok na agad yung ubuntu ayaw.

help naman

1. Paano mag add ng windows network printer sa ubuntu
2. paano ko connect yung ubuntu sa windows network na may internet..
3. paano ko connect ang ubuntu sa windows network

---

### Post by Nhatz on 2008-02-26
:KS Yo parenghilton..... install mo muna SAMBA para maka-connect ka sa network mo.

```
sudo apt-get install samba
```

then stop mo muna samba daemon...

```
/etc/init.d/samba stop
```

then backup mo samba config file mo...

```
cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
```

then edit mo yung samba config mo...

```
sudo gedit /etc/samba/smb.conf
```

scroll down mo hanggang makita mo yung "WORKGROUP=MSHOME"... change mo yung MSHOME sa name ng windows workgroup mo.

then... Save & Exit mo

restart no SAMBA daemon...

```
/etc/init.d/samba restart
```

then WHALA!!! ok na network mo.... hehehehe :)

:KS about nman sa network printing mo...

punta ka sa System -> Administration -> Printing

then... New Printer -> Windows Printer Via Samba

then browse mo yung network mo kung saan nakakabit yung printer (make sure na naka [COLOR="Red"]"SHARE"[/COLOR] yung printer.)

then.. Select Printer Form Database, hanapin mo yung model nung printer kung saan gusto mo mag-connect then click Apply.... tapos ang problema. heheheh.

Ganyan lang setup ko dito sa office... sana makatulong ito. hehehe :)

Astig! :guitar:

---

### Post by parenghilton on 2008-02-26
thank you po sir nhat.. galing mo talaga. wait mo ako dyan sa ACLC. ok thanks

---

### Post by Nhatz on 2008-02-27
Gumana ba? sana gumana syo kasi ganyan lang setup ko gumagana nman sakin. hehehe :)

Astig! :guitar:

---

### Post by glenn45 on 2008-02-29
galing ah... asteeg.
siguro  ubuntu guru kaw? :)

---

### Post by Nhatz on 2008-02-29
yo glen45 gumana ba syo setup ko? hehehehe. inaral ko lang (kailangan kasi sa work eh) ok nman at nakakatulong ako sa ibang tao,
Astig! :guitar:

---

### Post by glenn45 on 2008-02-29
eh ta try ko yung steps mo. actually, sa opis automatic namang nakita nung kubuntu ko yung samba network ng rhel  pati na rin yung printer. ang di ko mapagana pa ay yung email server sa laboratory namin. hehehe. 

tenks.:guitar:

---

