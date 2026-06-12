---
title: "head-phone"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by rhanex on 2008-08-03
why theres still sound on my speakers even my headphone are plug in?

---

### Post by mgranet on 2008-08-03
What kind of computer are you using?

---

### Post by northern lights on 2008-08-03
> **mgranet said:**
> What kind of computer are you using?
Must be a laptop. If not, redundant question / contact the manufacturer of your amplifier.

@ the OP:
Please post the output of ```
cat /proc/asound/cards
```

---

### Post by mgranet on 2008-08-03
> **northern lights said:**
> Must be a laptop. If not, redundant question / contact the manufacturer of your amplifier.

@ the OP:
Please post the output of ```
cat /proc/asound/cards
```

Yes, I was well aware. But one must start somewhere, given the lack of info by the OP.

---

### Post by rhanex on 2008-08-03
im using a desktop kinda thing
here's the code
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 21

```

---

### Post by Ru$$i@N on 2008-08-03
> **rhanex said:**
> why theres still sound on my speakers even my headphone are plug in?

i have same problem on my averatec laptop.
what i did is i adjusted the *front* volume to 0 in the Volume Control, but every time you want the speakers, you would have to manually adjust the volume control

---

### Post by rhanex on 2008-08-03
> **Ru$$i@N said:**
> i have same problem on my averatec laptop.
what i did is i adjusted the *front* volume to 0 in the Volume Control, but every time you want the speakers, you would have to manually adjust the volume control

Didn't work. I put it to 0 like u said, now both of them have no sound. :confused::confused:

---

### Post by northern lights on 2008-08-03
> **rhanex said:**
> im using a desktop kinda thing
here's the code
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 21

```Wasn't aware of desktop hardware detecting headphone plugs. Still think the question might need rephrasing.

The Intel High Definition Audio chipset is so far badly supported by the linux sound architecture.

Are you certain the speakers should stop working in the first place? Do you have internal speakers?

---

### Post by rhanex on 2008-08-03
> **northern lights said:**
> Wasn't aware of desktop hardware detecting headphone plugs. Still think the question might need rephrasing.

The Intel High Definition Audio chipset is so far badly supported by the linux sound architecture.

Are you certain the speakers should stop working in the first place? Do you have internal speakers?

i didn't get what do u mean to say?:confused:
internal speakers?? whats that??
sorry super noob here:-P:-P

---

