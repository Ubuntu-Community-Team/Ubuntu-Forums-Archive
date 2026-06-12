---
title: "broken package problem"
date: 2006-04-22
forum: Repositories &amp; Backports
---

### Post by annaraps on 2006-04-22
Hi

I tried installing the linuxdcpp client using a debian package 
that i found.It complained about dependencies with some 
libraries like libcairo , libpango , libglib , libgtk etc and i installed those 
too.

the client works well, though i get a broken package error of all
those libraries that i installed 

whn i tried fixing the broken packages apt complains saying
try running sudo apt-get install -f

when i try that , it tries to uninstall virtually every package i 
have installed.

can some one help me out please ?

---

### Post by jazzmuzik on 2006-04-22
I see a dcpp package in Synaptic but I've got the extra repositories enabled plus Automatix. I'd install something made for Ubuntu first before looking at a Debian package. While Ubuntu is a Debian based distro your best bet is to first look for something made for Ubuntu.

---

### Post by annaraps on 2006-04-22
I couldn't find it using my 
repository list.But thanks 
for the advice.I 'll remember
next time to do so

It would be helpful if I could get rid of the
error by some means for now

---

### Post by stevensheehy on 2006-04-22
I don't know what cvs version the package is, but I'd highly recommend compiling from source. It is still very much beta software and it is constantly changing, so you can update it easily by just getting the updated source and recompiling.

---

### Post by fdoving on 2006-04-22
try:
```

sudo dpkg -P packagename

```

That would purge the debian package. 
And hopefully solve your broken package problems.

- Frode

---

### Post by annaraps on 2006-04-23
I purged the debian package for
dcpp but the libraries that I mentioned,
like libacairo1 , libpango and
libgcc1 ,remain broken.When
I try to upgrade/remove/purge
them comes the trouble of 
having to uninstall all my other
packages.

Everything seems to be dependent on 
these libraries

p.s sorry about the delay in the reply.

---

### Post by fdoving on 2006-04-23
Why do you want to remove the libraries? They are probably used for other packages too.
To fix your apt try:
```

sudo apt-get -f install

```

Does it still want to remove everything? 

- Frode

---

