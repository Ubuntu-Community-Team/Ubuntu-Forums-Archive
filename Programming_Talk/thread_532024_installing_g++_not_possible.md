---
title: "installing g++ not possible"
date: 2007-08-22
forum: Programming Talk
---

### Post by Althippie on 2007-08-22
Hello Community,

I need g++ to compile my c++ programmtext and I obviously haven't got it on my Ubuntu 7.04 system. By searching it by using the adding/removing software function I could not find it even if I search for all accessible software.
Can anybody help me?

Thank you in advance,
Althippie

---

### Post by Soybean on 2007-08-22
You want to install the "build-essential" package. So search for that in Synaptic, or
```
sudo aptitude install build-essential
```
from a command-line. :)

---

### Post by Althippie on 2007-08-22
Thank you very much. The package is installed and there is no missing g++ compiler anymore.
But now there is a new problem :) and I will open a new thread.
Thanks a lot!

---

### Post by Althippie on 2007-08-22
Footnote:

It was not possible to install built-essentials with the packet-manager. Maybe this is a generell problem on my system because it is not possiblle too to install some quodlibet-plugins. 
Does anyone know an answer?

Greetings, 
Althippie

---

### Post by fct on 2007-08-23
The packet-manager doesn't display a detailed view of the available packages, so some of them aren't directly visible. Synaptic is another GUI package management application that displays all the available packages.

---

