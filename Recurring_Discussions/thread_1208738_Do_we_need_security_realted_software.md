---
title: "Do we need security realted software?"
date: 2009-07-09
forum: Recurring Discussions
---

### Post by mytechguru on 2009-07-09
Hi,
     i am new guy 2 Linux side. Really we need anti virus software @ linux. Or any security related product.

---

### Post by HermanAB on 2009-07-09
Nope - Ubuntu is secure out of the box - you don't need band-aids.

However, there are virus scanners for use on servers to remove Windows crudware and protect client systems.

---

### Post by sasho_zl on 2009-07-09
You can use antivirus software also to scan files which you are going to send to windows users. I had avast antivirus installed a few months ago and it worked great as an on demand scanner. Also ClamAV is a very popular solution and it is open source.
Also having a configured firewall is never a bad thing so take a look at the various tools out there like gufw, shorewall and so on.
Good luck ;)

---

### Post by mytechguru on 2009-07-09
what about firewall?

---

### Post by monsterstack on 2009-07-09
> **mytechguru said:**
> what about firewall?

Linux has a firewall built into the kernel. There are a bunch of command-line and GUI utilities to change the settings, though. In Ubuntu, at least, the default setting is to keep ports closed. You can have as many outgoing ports as you like kept open if you need them (for server stuff), but so long as you disallow incoming connections to them you will probably be fine. And if you *do* allow incoming connections for remote-login and such, there are a number of tools available to you to make sure only you are able to do that. The majority of users, however, are pretty well-defended without changing any of the default settings.

---

### Post by donkyhotay on 2009-07-10
This story pretty much sums it up:


Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

---

### Post by juancarlospaco on 2009-07-10
> **donkyhotay said:**
> “when your house is well constructed, there is no need to add pillars to keep the roof in place.”

[b][size="3"][color="sienna"]
+1[/color][/size][/b]

---

### Post by bodyharvester on 2009-07-11
> **juancarlospaco said:**
> [B][SIZE=3][COLOR=sienna]
+1[/COLOR][/SIZE][/B]

let me add one to that

+1

):P

---

