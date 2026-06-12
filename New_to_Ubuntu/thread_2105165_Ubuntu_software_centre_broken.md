---
title: "Ubuntu software centre broken"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by henry006 on 2013-01-14
Hi everybody,
like most of french people my english could be better but I'll try to do my best, SO:

I recently had a prob with my software center which didn't want to open no more and send me back a message like: [B]E:Encountered a section with no Package: header, E:Problem with MergeList
i found help on this forum doing what follows:
[/B]
Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

maybe it will help you...
The point is that at the end I still receive a message like:
W: Impossible de récupérer [http://orniere-du-globe.net/debian/./Release.gpg](http://orniere-du-globe.net/debian/./Release.gpg)  Mauvaise ligne d'en-tête

W: Impossible de récupérer [http://orniere-du-globe.net/debian/./Sources](http://orniere-du-globe.net/debian/./Sources)  Mauvaise ligne d'en-tête

W: Impossible de récupérer [http://orniere-du-globe.net/debian/./Packages](http://orniere-du-globe.net/debian/./Packages)  0  Requested Range Not Satisfiable

W: Impossible de récupérer [http://orniere-du-globe.net/debian/./en](http://orniere-du-globe.net/debian/./en)  Mauvaise ligne d'en-tête

E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
 is it a big prob or should I leave it like it is ?????...
By advance thanks to all for any reply

---

