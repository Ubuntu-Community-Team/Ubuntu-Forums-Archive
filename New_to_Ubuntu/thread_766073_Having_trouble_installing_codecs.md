---
title: "Having trouble installing codecs"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Inbo on 2008-04-25
Hi

I've already tried installing the codecs via the medibuntu repositories but it's not working. It shows up as 'unable to find x repository'. I've also been having trouble connecting to some of the official ubuntu repositories as well.

---

### Post by rouge568 on 2008-04-25
Try the whole medibutnu process again.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras
```

Of course, it may just be the slow ubuntu severs.

---

### Post by Paqman on 2008-04-25
Yep, the poor old repos are getting thrashed right now. Patience is the solution for that.

---

### Post by SunnyRabbiera on 2008-04-25
Yeh there will be some time, with hardy's release comes much anticipation.

---

### Post by Inbo on 2008-04-25
Yeah, I thought it was just my patience getting to me. Thanks.

---

### Post by PCTux on 2008-04-25
> **rouge568 said:**
> Try the whole medibutnu process again.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras
```

Of course, it may just be the slow ubuntu severs.

I get this:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Helios38 on 2008-04-25
```
sudo apt-get install ubuntu-restricted-extras
```


should have every codec you need. although ubuntu servers are very very slow around release times.

---

### Post by zvacet on 2008-04-25
@ **PCTux**

In terminal type

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

---

### Post by Ub1476 on 2008-04-25
> **PCTux said:**
> I get this:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

According to Medibuntu, just:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring

```

---

### Post by PCTux on 2008-04-26
Tnx to zvacet and Ub1476

---

