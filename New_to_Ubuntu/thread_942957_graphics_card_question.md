---
title: "graphics card question"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by metzy85 on 2008-10-09
I have two graphics cards in two of my 3 pci slots in my computer. I have two moniters I have a lcd on my better card and a crt to the right of it on the other card. Ubuntu only shows up on the crt how do i get it to she the main desktop on the lcd (on the other card)??

---

### Post by Pro-reason on 2008-10-10
Please open a terminal and type these two commands:

```

sudo lshw > ~/lshw.txt
gedit ~/lshw.txt

```

Paste the output here.  Use the **#** button to put [noparse]```
...
```[/noparse] tags around it for legibility.

---

