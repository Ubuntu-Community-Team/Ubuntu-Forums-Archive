---
title: "Problems updating"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by Moonigan on 2012-04-20
Update manager throws me this message at the moment:


Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

app-install-data
gcc-4.2-base
gcc-4.3-base
libavc1394-0
libdb4.6
libraw1394-8
libt1-5
mailx


It would seem my settings are inadequate but unclear exactly what to change or how.

thx

---

### Post by audiomick on 2012-04-20
Have you given it some time to sort itself out?

It says in the error message "this may be a transient network problem". This means you should give it some hours or even a day or so. Maybe the server you are getting the packages from is having a problem or something like that.

---

### Post by Moonigan on 2012-04-20
yea its been like that for weeks, same packages

---

### Post by cortman on 2012-04-20
Is it not saying it's missing GPG keys? Just "unauthenticated packages"?

---

### Post by audiomick on 2012-04-20
> **cortman said:**
> Is it not saying it's missing GPG keys? Just "unauthenticated packages"?

Amounts to the same thing, doesn't it? Isn't there a way to tell it to install anyway?

---

### Post by cortman on 2012-04-20
OP doesn't mention if it's giving GPG errors. If so, it's an easy fix- instructions [here.]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/")
If not, it's something strange and possibly a bug.

---

### Post by QIII on 2012-04-20
Could you attempt to do your updates in the terminal and post back the entire error message(s)?

---

### Post by Moonigan on 2012-04-21
I've attached a screenshot showing what happened in the terminal as well as the message i get before attempting to update through update manager, and another one that i get upon opening update manager. im mostly concerned that it won't make any updates, not just the ones it claims to have issues with, but i dont understand what most of the updates are anyway

---

### Post by raja.genupula on 2012-04-21
Dont go for partial upgrades , they are not recommended . They can make your system as unstable.

open update manager -> settings -> other software  TAB , select the all sources .

at 1st TAB change the server to main server or best server to your main location . 

then try again .  :)

---

### Post by Moonigan on 2012-04-21
thanks raja, i realise it was still on a china server too though i've come back to blighty. most of them are installed now, whatever's left doesn't seem too crucial(?)

---

### Post by raja.genupula on 2012-04-21
whats left tell us , we will try .

---

