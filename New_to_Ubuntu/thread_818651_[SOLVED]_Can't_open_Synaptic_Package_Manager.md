---
title: "[SOLVED] Can't open Synaptic Package Manager"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Creasey on 2008-06-04
Tried to install adobe pdf reader.  Followed instructions on [www.ubuntugeek.com](www.ubuntugeek.com), I think! Can't open Synaptic Package Manager
Following message:
E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report
Can anybody help.  I'm on day 3 with ubuntu a real newbee!

---

### Post by JoshuaRL on 2008-06-04
Try these three commands from the terminal (Applications->Accesssories->Terminal)
```

sudo dpkg --configure -a
sudo apt-get install -f
gksu synaptic

```

The first will try to fix any broken packages and dependencies through dpkg.  The second will try to do the same through APT.  The third will try to launch Synaptic.  See if that helps.

---

### Post by Rocket2DMn on 2008-06-04
Sounds like the repository may just be down or just needs to be refreshed.  Can you please run in Terminal (Applications->Accessories->Terminal)
```
sudo apt-get update
sudo apt-get upgrade
```
Post the output here, please.

---

### Post by Creasey on 2008-06-04
Thanks for such a promt response but alas neither suggestion has worked!
Is there anything else I can try?

---

### Post by Rocket2DMn on 2008-06-04
Sure, can you please post these two files for us?
```
cat /etc/apt/sources.list.d/medibuntu.list
cat /etc/apt/sources.list
```

---

### Post by drs305 on 2008-06-04
I worked a similar problem a week or so ago.

For Hardy, this should be the entire contents of the medibuntu.list file. If you have anything else, delete it all and replace it with:
Code:

```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```

After you replace it, reload synaptic. You might also want to run:
```
sudo apt-get update

```

---

### Post by Oldsoldier2003 on 2008-06-04
> **Creasey said:**
> Tried to install adobe pdf reader.  Followed instructions on [www.ubuntugeek.com](www.ubuntugeek.com), I think! Can't open Synaptic Package Manager
Following message:
E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report
Can anybody help.  I'm on day 3 with ubuntu a real newbee!

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get upgrade
```
Apparently you used an old out of date tutorial for installing the medibuntu repos. what has happened is that you have a html page for the list instead of a properly formatted source list.

---

### Post by Oldsoldier2003 on 2008-06-04
> **drs305 said:**
> I worked a similar problem a week or so ago.

For Hardy, this should be the entire contents of the medibuntu.list file. If you have anything else, delete it all and replace it with:
Code:

```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```

After you replace it, reload synaptic. You might also want to run:
```
sudo apt-get update

```

indeed. There are quite a few old tutorials out there that still hit high on google. unfortunately these tutorials are wrong since they have the user wget the wrong url which results in a bad sources list

---

### Post by Creasey on 2008-06-05
Many thanks Old Soldier problem soved! Magic

---

