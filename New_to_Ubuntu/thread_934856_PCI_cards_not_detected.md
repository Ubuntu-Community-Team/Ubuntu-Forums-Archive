---
title: "PCI cards not detected"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by sakid on 2008-10-01
I've just install ubuntu hardy onto a pc i had laying around. my problem is it will not detect any pci cards in any slots.

I have no idea what the problem could be but Im hoping someone here I might.

Cheers

---

### Post by iaculallad on 2008-10-01
Does it display the card(s) when you issue the terminal command below?

```
lspci
```

---

### Post by sakid on 2008-10-01
No sign of any card in any slot..

---

### Post by wolfen69 on 2008-10-01
sounds like a bad motherboard. poke around in the bios settings for anything amiss.

---

### Post by sakid on 2008-10-01
Yeh Ive had a look in the bios and cant see anything obvious. Is there a way i can see if the slots are "installed"?

---

### Post by iaculallad on 2008-10-01
If it doesn't display in lspci, try:

```
sudo lshw
```

*But I doubt if lswh will display it if lspci does not show it as installed*

---

