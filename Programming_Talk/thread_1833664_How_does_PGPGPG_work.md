---
title: "How does PGP/GPG work?"
date: 2011-08-26
forum: Programming Talk
---

### Post by ki4jgt on 2011-08-26
I am trying to find an article on the inner workings of GPG/PGP. I want enough information that I could program it. I've looked at wikipedia and it's all so complex that I don't know what to think. If it had a few examples in it, that would also be great. Thanks guys :-)

---

### Post by amauk on 2011-08-26
Encryption is complex

anyway, here's the OpenPGP spec.
[http://www.ietf.org/rfc/rfc4880.txt](http://www.ietf.org/rfc/rfc4880.txt)

---

### Post by ki4jgt on 2011-08-26
> **amauk said:**
> Encryption is complex

anyway, here's the OpenPGP spec.
[http://www.ietf.org/rfc/rfc4880.txt](http://www.ietf.org/rfc/rfc4880.txt)

May I freely use this (in a paid product) without being sued for protocol infringement?

---

### Post by Bachstelze on 2011-08-26
> **ki4jgt said:**
> May I freely use this (in a paid product) without being sued for protocol infringement?

Are you saying you want to develop and sell an OpenPGP implementation? Sure you can but that would be extremely dumb. If you can't understand the Wikipedia pages, there is no way you can do a decently secure product.

---

### Post by ki4jgt on 2011-08-26
> **Bachstelze said:**
> Are you saying you want to develop and sell an OpenPGP implementation? Sure you can but that would be extremely dumb. If you can't understand the Wikipedia pages, there is no way you can do a decently secure product.

I agree, but that is why I'm inquiring as to how it works, to increase my own understanding. Trying to create a product which uses PGP now would be insane. But if you can create a successful PGP system based on what you find on Wikipedia, Good Luck. I didn't mean I couldn't understand them as much as I meant that they were extremely vague. There are examples on the Wikipedia page, but it does not go into detail enough to enable any person the ability to create a fully functional PGP feature in their program.

---

### Post by amauk on 2011-08-27
> **ki4jgt said:**
> But if you can create a successful PGP system based on what you find on Wikipedia, Good Luck. I didn't mean I couldn't understand them as much as I meant that they were extremely vague.That's because it's an encyclopaedia. They are supposed to be "vague". They're a secondary source of information that summarise multiple primary sources

Anyway...

---

### Post by haqking on 2011-08-27
Wikpedia is an opinion (until edited with another opinion) overview information source.

To understand PGP you will need a good foundation in math and cryptography.

See here for PGP specific overview.

[http://www.pgpi.org/doc/pgpintro/](http://www.pgpi.org/doc/pgpintro/)

and here for more indepth

[http://www.pgpi.org/](http://www.pgpi.org/)

---

### Post by ki4jgt on 2011-08-27
Is there a way to use GnuPG (the program) with Python?

NM: just did my own research.

---

### Post by haqking on 2011-08-27
> **ki4jgt said:**
> Is there a way to use GnuPG (the program) with Python?

what do you mean use it with python ?

It is open source so the source is available here [http://www.gnupg.org/download/](http://www.gnupg.org/download/)

what exactly do you mean use it with python ?

---

### Post by ki4jgt on 2011-08-27
> **haqking said:**
> what do you mean use it with python ?

It is open source so the source is available here [http://www.gnupg.org/download/](http://www.gnupg.org/download/)

what exactly do you mean use it with python ?

As in API

---

### Post by Longinus00 on 2011-08-27
> **ki4jgt said:**
> As in API

Like this? [http://code.google.com/p/python-gnupg/](http://code.google.com/p/python-gnupg/)

It's even BSD licensed.

---

### Post by ziekfiguur on 2011-08-28
Actually, the makers of gnupg offer an api for programmers that want to use cryptography. From the gnupg website
> GnuPG Made Easy (GPGME) is a library designed to make access to GnuPG easier for applications. It provides a High-Level Crypto API for encryption, decryption, signing, signature verification and key management. Currently it uses GnuPG as its backend but the API isn't restricted to this engine; in fact we have already developed a backend for CMS (S/MIME).

Because the direct use of GnuPG from an application can be a complicated programming task, it is suggested that all software should try to use GPGME instead. This way bug fixes or improvements can be done at a central place and every application benefits from this.

Especially authors of MUAs should consider to use GPGME. It is even planned to create a set of standard widgets for common key selection tasks.

The ubuntu repositories have a gpgme package as well as a package with python wrappers for this library. They're called libgpgme and python-gpgme

---

### Post by ki4jgt on 2011-08-28
> **ziekfiguur said:**
> Actually, the makers of gnupg offer an api for programmers that want to use cryptography. From the gnupg website


The ubuntu repositories have a gpgme package as well as a package with python wrappers for this library. They're called libgpgme and python-gpgme

Well, I've been wanting to make this program for a while. Everyone kept telling me I needed to move it to C/++ so, I finally started C++ today. :-( :-) but that is still useful to know. I've got a git repository started and everything. *Fingers Crossed* this project is hopefully gonna be worth it.

---

### Post by hakermania on 2011-08-28
> **ki4jgt said:**
> Well, I've been wanting to make this program for a while. Everyone kept telling me I needed to move it to C/++ so, I finally started C++ today. :-( :-) but that is still useful to know. I've got a git repository started and everything. *Fingers Crossed* this project is hopefully gonna be worth it.
let as know !
don't let this thread die!

---

