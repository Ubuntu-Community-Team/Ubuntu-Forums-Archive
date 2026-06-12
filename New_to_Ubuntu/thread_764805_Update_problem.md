---
title: "Update problem"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-04-24
I am trying to run the updater in 7.10 and when I click the "check" button I am getting these 2 msgs.

[http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz:) 404 Not Found

and


W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Please help.

---

### Post by kpkeerthi on 2008-04-24
It appears that the **gutsy** repository is no longer available there. I can only see feisty's

See [http://download.tuxfamily.org/syzygy42/dists/](http://download.tuxfamily.org/syzygy42/dists/) on your browser.

---

### Post by DarkSaga70 on 2008-04-24
What do I do with that?

---

### Post by chewearn on 2008-04-24
Probably server falling under pressure from the surge of hardy update?  Try again later, or wait a few days.

---

### Post by zvacet on 2008-04-24
Type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 58403026387EE263
gpg --export --armor 58403026387EE263 | sudo apt-key add -

---

### Post by ptcbus on 2008-04-24
Try torrents. THis is much much faster. I have listed the steps here: [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by kpkeerthi on 2008-04-25
> **DarkSaga70 said:**
> What do I do with that?

Can't do anything. The gutsy repo hosted there has been retired and you will no longer receives updates to the packages you installed from there. 

You may delete the repository from System -> Admin -> Software Sources -> 3rd party repositories, if you want.

---

