---
title: "Music?"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Haioko on 2008-07-28
Why can't I listen to music?

I've copied music from my windows OS computer onto my pen drive then onto my Ubuntu OS and it won't let me listen to them :@

They are all .mp3 files.

---

### Post by t0p on 2008-07-28
> **Haioko said:**
> Why can't I listen to music?

I've copied music from my windows OS computer onto my pen drive then onto my Ubuntu OS and it won't let me listen to them :@

They are all .mp3 files.

To listen to mp3s, you need to install the package **ubuntu-restricted extras**.  Do this in Synaptic (**System > Administration > Synaptic Package Manager**), or in a Terminal type

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Haioko on 2008-07-28
scott@scott-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for scott:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

Aparently thats not gonna happen.

---

### Post by halitech on 2008-07-28
do this first
```
sudo apt-get update
```
then
```
sudo apt-get install ubuntu-restricted-extras
``` and see if that works

---

### Post by Haioko on 2008-07-28
First one worked but the second one came up the same thing. My Ubuntu really hates me lol.

---

### Post by t0p on 2008-07-28
Ok, you probably need to enable the restricted repositories.  Do this through **System > Administration > Software Sources**.  Then you'll be able to install ubuntu-restricted-extras

---

### Post by Haioko on 2008-07-28
What do I check?

---

### Post by koji042 on 2008-07-28
You should check "non-free (multiverse)" or something along those lines. Then just install ubuntu-restricted extras via Terminal or Synaptic Package Manager.

Hope the helps.

---

### Post by Haioko on 2008-07-28
Cheers guys. It's downloading as we speak =]

---

### Post by Haioko on 2008-07-28
This just came up as I was installing.

E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1

What does that mean?

---

### Post by t0p on 2008-07-28
> **Haioko said:**
> This just came up as I was installing.

E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1

What does that mean?

*Uhhh...* I dunno, man!!  :(

---

### Post by sandeepy on 2008-07-28
> **Haioko said:**
> Why can't I listen to music?

I've copied music from my windows OS computer onto my pen drive then onto my Ubuntu OS and it won't let me listen to them :@

They are all .mp3 files.


Q1. Are you able to mount the USB ?

Q2. What is the err mesg that you get ? What player are u using to open it with ?

---

### Post by cariboo on 2008-07-28
Open up a Application-->Accessories-->Terminal and type:

```
sudo apt-get -f install
```

This will download any missing files and finish installing the restricted extras.

Jim

---

