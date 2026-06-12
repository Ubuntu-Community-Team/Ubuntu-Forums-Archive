---
title: "HowTo install aMule"
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by illmonkey on 2005-03-28
Hello,

I try the method on the guide but thex don't work..

I try this :

 $ sudo apt-get install amule

[PHP]root@ubuntu:/home/illmonkey # apt-get install amule
Reading package lists... Fait
Building dependency tree... Fait
E: Impossible de trouver le paquet amule[/PHP]

How can i do? 

Thank you

---

### Post by boma on 2005-03-28
Hi,

amule is part of the universe packages...

edit 

> /etc/apt/source.list

and uncomment the universe source-line.

> apt-get update

> apt-get install amule 

..will do... \\:D/ 

good luck
boma

---

### Post by illmonkey on 2005-03-28
Thank you it works!!   :D 

What is the difference between universe packages and main-restricted packages?

---

### Post by mig_l on 2005-05-09
I can´t do it...

The following packages have unmet dependencies:
  amule: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages


????

Need some help please!!!

---

