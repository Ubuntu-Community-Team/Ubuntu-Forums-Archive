---
title: "How to install kicad on ubuntu 9.04"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by abhi1989 on 2012-07-27
How to install kicad on ubuntu 9.04

---

### Post by jonnyboysmithy on 2012-07-27
If you googled it you would have come accross this: [http://www.kicad-pcb.org/display/KICAD/Download+Kicad](http://www.kicad-pcb.org/display/KICAD/Download+Kicad)

```
sudo add-apt-repository ppa:adamwolf/kicad-testing-daily
sudo apt-get update
sudo apt-get install kicad kicad-doc-en
```
Have you tried that?

---

### Post by albandy on 2012-07-27
> **abhi1989 said:**
> How to install kicad on ubuntu 9.04

You should not use unsupported ubuntu versions. 9.04 support ended in october 2010.

I recommend you to upgrade, at least, to ubuntu 10.04.

---

### Post by oldos2er on 2012-07-27
> **jonnyboysmithy said:**
> If you googled it you would have come accross this: [http://www.kicad-pcb.org/display/KICAD/Download+Kicad](http://www.kicad-pcb.org/display/KICAD/Download+Kicad)

```
sudo add-apt-repository ppa:adamwolf/kicad-testing-daily
sudo apt-get update
sudo apt-get install kicad kicad-doc-en
```
Have you tried that?

I don't think the add-apt-repository command existed in 9.04. At any rate, abhi1989 should update to a supported version of Ubuntu as was recommended.

---

