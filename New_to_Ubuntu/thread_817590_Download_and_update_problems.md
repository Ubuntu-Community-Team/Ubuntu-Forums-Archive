---
title: "Download and update problems"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by vfrankli on 2008-06-03
The Download Manager is sticking.  The little activation wheel is spinning, and the options are faded/shaded, but the selections are not downloading.  Has anyone had this problem?  BTW, the Update manager is doing the same thing.:(

---

### Post by Joeb454 on 2008-06-03
What happens if you try from a terminal? ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by b0lha on 2008-06-03
Hi there! Got the same problem...

Two weeks ago I achieved in surpassing the problem by calling System/Adminstration/Synaptic, so that the system asked for a pass and everything was OK. Now even that doesn't work, lauching synaptic or even firestarter from the system is a no go.

However,If I try through a console both work fine:synaptic and firestarter, all but the apt-get...while the apt-get update just checks the repositories, the apt-get ugrade is strange...

I'm trying to do these last kernel upgrades for 2.6.24-18 and the computer just says it won't install them... why? don't know....!

Cheers, 

David

---

### Post by Joeb454 on 2008-06-03
What's the output from the terminal?

Please enclose it in ```

``` tags :)

---

### Post by b0lha on 2008-06-04
It is the most regular output I've ever seen....don't know if you will understand because it's in Portuguese...

> A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Lendo informação de estado... Pronto
Os seguintes pacotes serão mantidos em suas versões actuais:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 4 não actualizados.


It basically says the packages will be maintained in their present version...

---

### Post by b0lha on 2008-06-04
Tell me if  you need a translation for this output, sorry....

David

---

### Post by Inxsible on 2008-06-04
Guys I have the same problem in my Xubuntu install. Not only update manager/synaptic but even when I start firefox, my system just hangs there...and i finally have to restart X or manually power down.


See the [thread]("http://ubuntuforums.org/showthread.php?t=818936") that I started about the same issue a little while ago....No solutions yet though :(

---

