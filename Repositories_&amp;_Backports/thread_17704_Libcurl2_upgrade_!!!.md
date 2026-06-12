---
title: "Libcurl2 upgrade !!!"
date: 2005-03-02
forum: Repositories &amp; Backports
---

### Post by Marauder1 on 2005-03-02
I am using warty and did a full upgrade !!!
All my repos are to warty only.
Everything went ok but i'm getting this error
concerning libcurl2.

 Preconfiguring packages ...
(Lecture de la base de données... 80554 fichiers et répertoires déjà installés.)Préparation du remplacement de libcurl2 7.12.0.is.7.11.2-1 (en utilisant .../libcurl2_7.12.0.is.7.11.2-1ubuntu0.1_i386.deb) ...
Dépaquetage de la mise à jour de libcurl2 ...
dpkg : erreur de traitement de /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1ubuntu0.1_i386.deb (--unpack) :
 tentative de remplacement de « /usr/share/curl/curl-ca-bundle.crt », qui appartient aussi au paquet libcurl3
dpkg-deb: sous-processus paste tué par le signal (Relais brisé (pipe))

Échec lors de l'application des changements - Faites défiler la fenêtre pour trouver l'erreur.

So for libcurl2 upgrade is nocando !!!
Any reasons why ?
Is this a bug or a bad deb pack ?

TIA

---

### Post by jeremy on 2005-03-02
I am getting the same, I attach a screenshot of the terminal output (it won't let me copy/paste).

---

