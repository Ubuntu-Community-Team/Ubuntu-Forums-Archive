---
title: "HOWTO: Install Google Earth - The easy way!"
date: 2008-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by iSplicer on 2008-05-02
[B][U][SIZE="5"]HOWTO: Install Google Earth - The easy way!
[/SIZE][/U][/B]
Hey all. I say another guide on this that uses the .bin file downloaded from google's website, but I think using synaptic is way way easier. I will guide you through how to set up and install this excellent program the easy way!

Google Earth does not come in the default Ubuntu repos, so you will have to install the "medibuntu" repositories.
[B]
Step one[/B]

Copy+paste / type this into your terminal:

If you have Hardy:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```

IF you have Gutsy:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

If you have Feisty:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```

**Step two**

Copy+paste / type this into your terminal:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

**Step three**

Copy+paste / type this into your terminal:
```
sudo apt-get install googleearth-4.3
```

You can start it by creating a launcher with command googleearth or you can alt+f2 and type it in.

Enjoy!

---

### Post by danbar on 2008-05-03
Shall I proceed to step 3 even though I continuously get the same reply?

Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz](http://download.tuxfamily.org/syzygy42/dists/gutsy/avant-window-navigator/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ubuntosh on 2008-05-03
Hi there, I followed your instructions, everything went fine until the last step, in terminal I got that the googleearth 4.3 package couldn't be found. What should I do then?
Thanks.
I'm using Gutsy AMD64. Bye

---

