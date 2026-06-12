---
title: "How to use same personal key across multiple computers?"
date: 2012-12-23
forum: Packaging and Compiling Programs
---

### Post by JamesTheAwesomeDude on 2012-12-23
I have an old computer that I fixed up, and I'd like to use it for my coding (right now, I'm working on debianizing the games at stabyourself.net. Don't worry; the liscense allows it!)

I have already built a few on my main computer, and I'd like to sort of migrate my packaging to the old computer. Unfortunately, I would have to generate another key for the second computer, and I'd prefer not to do that. I know that you can import someone else's key, sort of as a "recognized person," but how do I import a key as one of MY keys? (P.S., I *do* have the secret password thingy. That's how I've been signing the packages, after all.)

---

### Post by Bachstelze on 2012-12-23
Any reason why you can't just do [font=monospace]scp -r .gnupg targethost:[/font]?

---

### Post by JamesTheAwesomeDude on 2012-12-29
> **Bachstelze said:**
> Any reason why you can't just do [font=monospace]scp -r .gnupg targethost:[/font]?

Lol, probably because I've never heard of that before.

So... I execute that command on the machine I've already built stuff on? Do I need to export my keyfile first or something like that?

---

### Post by Bachstelze on 2012-12-31
Normally no, copying .gnupg is the only thing that's needed, executing gpg on the other host will pick up the keys as normal.

---

### Post by JamesTheAwesomeDude on 2013-01-07
Okay... where do I find this file?

Also, do I just type scp -r .gnupg targethost, then upload some file to the other computer, or do I need to do
scp -r /home/james/.pgp/pgp.gnupgp 192.168.2.3
...or something like that?

---

