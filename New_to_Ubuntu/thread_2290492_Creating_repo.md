---
title: "Creating repo"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by waghanza on 2015-08-12
Hi,

I have created a repo (for **ubuntu:vivid**) with [http://www.aptly.info](http://www.aptly.info)
I'm try to install on my ubutu client (server is a debian jessie).

```
curl [http://apt.tech4team.fr/key.asc](http://apt.tech4team.fr/key.asc) | sudo apt-key add - 
sudo add-apt-repository 'deb [http://apt.tech4team.fr/](http://apt.tech4team.fr/) vivid main'
```

When I am trying to update my package list with ```
sudo apt-get update
``` I have ```
W: Impossible de récupérer [http://apt.tech4team.fr/dists/vivid/InRelease](http://apt.tech4team.fr/dists/vivid/InRelease)  Impossible de trouver l'entrée « main/binary-i386/Packages » attendue dans le fichier « Release » : ligne non valable dans sources.list ou fichier corrompu

E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
``` (**french **distribution)

I don't understand why **apt-get** is trying to reach an URL for **i386 **but I'm on a **amd64 **platform 
> uname -p```
x86_64
```

---

