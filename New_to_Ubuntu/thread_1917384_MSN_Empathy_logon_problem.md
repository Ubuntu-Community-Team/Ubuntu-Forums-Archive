---
title: "MSN Empathy logon problem"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by sanscents on 2012-01-29
For some reason, my main MSN address will not connect.  I have two other MSN accounts that connect, and my gmail account as well.

Because that one address wont connect, I use Pidgin.  The new Pidgin update is as great as the Firefox one, with support to be logged on from two different clients using the same address, and email alerts for MSN accounts.

Anyone else have a problem MSN account in Empathy?  Any fixes?  If it is going to continue to be the default Ubuntu IM client, I'd like to get it working properly.

Thanks!

---

### Post by sanscents on 2012-01-30
Anyone?

---

### Post by sanscents on 2012-01-30
I've been advised to "uninstall telepathy-butterfly and try to re-create your MSN account in empathy" at #empathy.  Has anyone heard of this?  I'm just always tentative I'm going to break something.  That's why I'm in Absolute Beginner Talk :confused: - :D

---

### Post by sanscents on 2012-01-30
Well, it worked!  They are switching their backend from butterfly to haze.  Hmm...haze uses libpurple.

---

### Post by d3ngar on 2012-02-03
> **sanscents said:**
> Well, it worked!  They are switching their backend from butterfly to haze.  Hmm...haze uses libpurple.
I'm not sure if sanscents just removed the telepathy-butterfly package 
> ~$ sudo apt-get remove telepathy-butterfly
 but I also upgraded through the empathy PPA (unstable)
to install the PPA and the latest version:
> sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get upgrade

---

