---
title: "ROOT terminal ayaw mag-open"
date: 2009-05-17
forum: Philippine Team
---

### Post by guitar_man on 2009-05-17
mga sir ayaw mag-open ng root terminal ko...
nakalagay lag sa windows list na starting Root terminal,,,pero ayaw din gumana

---

### Post by loell on 2009-05-17
anong output?

---

### Post by guitar_man on 2009-05-17
wala nga sir loell e...ayaw mag-open......

---

### Post by loell on 2009-05-17
anong output sa

```
gksu gnome-terminal
```

---

### Post by guitar_man on 2009-05-18
Failed to contact the GConf daemon; exiting.

---

### Post by loell on 2009-05-18
parang, restart lang daw ang kailangan.

may ininstall or ginawa ka ba lately?

---

### Post by dsdeiz on 2009-05-18
pwd pala un? akala ko lock ung root acct? :confused: panu bah magstart ng root terminal, ser?  :?:

OT: naglalaro ka rin pala ng frets on fire.. :guitar:

---

### Post by guitar_man on 2009-05-18
> **loell said:**
> parang, restart lang daw ang kailangan.

may ininstall or ginawa ka ba lately?

parang nmap ata huli ko intall...hindi ko maalala

---

### Post by Script Warlock on 2009-05-18
or hanapin mo bka may mga pending na updates or installation pwede naman cguro puntahan sa recovery mode tapos dpkg-reconfigure -a ba yun? or install -f? di ko matandaan.

---

### Post by guitar_man on 2009-05-18
pwede po ba try nyo yung root terminal nyo...


Applicatiom>>System Tools>>Root Terminal

---

### Post by Script Warlock on 2009-05-18
oi walang lumabas na root terminal? wat hapen?... terminal lang sa accessories ok lang pero sa root nga wala.:?:

---

### Post by guitar_man on 2009-05-18
right click mo sir boyet sa menu then click edit menu tthen lalabas to....


tapos nun check mo yung root terminal under System Tools

---

### Post by Script Warlock on 2009-05-18
> **guitar_man said:**
> right click mo sir boyet sa menu then click edit menu tthen lalabas to....


tapos nun check mo yung root terminal under System Tools

oo nga sa akin ayaw din...hehe sa akin ok lang server ng inet to di pa cguro kailangan gamitin but was confused bakit ayaw din sa akin....pero marami naman paraan to run sa root previledge like sudo su, sudo -i etc..pero eto sa 9.04 ayaw maopen yung icon link bkit kaya..

---

### Post by zeroseven0183 on 2009-05-20
> **boyet said:**
> oo nga sa akin ayaw din...hehe sa akin ok lang server ng inet to di pa cguro kailangan gamitin but was confused bakit ayaw din sa akin....pero marami naman paraan to run sa root previledge like sudo su, sudo -i etc..pero eto sa 9.04 ayaw maopen yung icon link bkit kaya..

Root Terminal did not open also on my machine. But no worries, there are still other ways just like he mentioned. Another one is

```
sudo -s
```

---

