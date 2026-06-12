---
title: "Error with libc6 during installation on ps3"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by lucky74 on 2008-05-03
Hi, I'm installing ubuntu 8.04 alternate CD on my PS3, I'm following how to guide but the installation process stopped showing this error message during libc6 installation :

[!!] Installare il sistema base
Avviso di debootstrap
Attenzione: Failure while configuring required packages.
<Indietro>    <Continuare>

Sorry for italian.

---

### Post by lucky74 on 2008-05-03
Any suggestion, I don't know what I must do ... press continue on back ?

---

### Post by lucky74 on 2008-05-03
No suggestion ? Any other area for support to PS3 ?

---

### Post by zvacet on 2008-05-04
Press continue and if you end up with errors try 

```
sudo dpkg --cofigure -a
```

or

```
sudo apt-get -f install
```

or you can post errors output (if any) here.

---

### Post by lucky74 on 2008-05-04
Thank you zvacet for your reply ! ):P [-o<

Now I have stopped the installation process because it still to be on 75%, installation of language, for a lot of time. I'm on kboot, I must type the line command from kboot ?

:):):):):)

---

### Post by lucky74 on 2008-05-04
After 1/2 hour the step is finished, but now I'm stopped to 1% of configurating language-pack-en-base, is passed more than 2 hours and I have decided to reset PS3.

I have discovered this discussion about the SAME problem of mine.

[https://bugs.launchpad.net/ubuntu-ps3-port/+bug/197728](https://bugs.launchpad.net/ubuntu-ps3-port/+bug/197728)

What can I do to install (a fresh installing) Hardy on my PS3 ?

---

