---
title: "Do I need Snort"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Troy McClure on 2012-02-04
So I finally got suspend working on my old HP laptop.  But then whenever it woke up from suspend the CPU was pegging at 100%.  I found the culprit was a program called snort.  I removed snort in Synaptic and now it wakes up fine.  Question is, did I need snort?  If it's required for security, should I put it back?

---

### Post by stoneage on 2012-02-04
It isn't part of the default installation.

Are you running a network ?

---

### Post by Dangertux on 2012-02-04
> **Troy McClure said:**
> So I finally got suspend working on my old HP laptop.  But then whenever it woke up from suspend the CPU was pegging at 100%.  I found the culprit was a program called snort.  I removed snort in Synaptic and now it wakes up fine.  Question is, did I need snort?  If it's required for security, should I put it back?

Snort is a network based intrusion detection system, if you weren't actively auditing its logs (or running it in inline mode) it wasn't doing anything for you in terms of security anyway.

IDS / IPS is no substitute for decent security settings and I would not say you NEED it for security.

Hopefully this helps.

---

### Post by Troy McClure on 2012-02-04
yeah I use a wireless router with 2 laptops.  If it's not there by default, I wonder how it got there.  I need to keep better track of what I install.  Thanks for the free consulting.

---

