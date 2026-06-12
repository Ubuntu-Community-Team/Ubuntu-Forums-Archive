---
title: "Mysteries"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by bustard on 2011-11-21
Like a lot of people running xubuntu, it seems, I get the:
```

ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-28]
ecryptfs_writepage: Error encrypting page (upper index [0x000000000212c485])
```messages, at least in the kern.log. I do not see them as popups so I have been ignoring them - everything seems to work ok.

But I notice that over the last several nights, or early mornings, at about 2am, the kern.log has a dozen or of such messages within 2 seconds, and then there is no more logging.

I have checked kern.log and syslog, and the logging stops after the flurry of ecryptfs messages.

I have a script running netstat once a minute, and at the time of the ecryptfs messages, it writes out a slew of garbage - looks like binary stuff, and it no longer works. - the script continues to try to run nestat, but the output file is 0 length.

Same thing with a test email that I send once an hour - after the ecryptfs stuff, it no longer works.

I guess my PC is locked up in some way, but when I come down in the morning and type in the password to unlock the screensaver, everything seems normal, and if I look at the kern.log, I can see messages beginning again from that point.

Any comments?

While I am at it, I noticed today that there was a program installed called 'popularity-contest' that apparently sends out emails to ubuntu about what programs I use the most. I don't remember telling anybody to install that one. I removed it, but it does not give me a warm and fuzzy feeling about ubuntu or xubuntu.

---

### Post by Larkspur on 2011-11-21
I can't help you with your main question, but about this one:

> **bustard said:**
> While I am at it, I noticed today that there was a program installed called 'popularity-contest' that apparently sends out emails to ubuntu about what programs I use the most. I don't remember telling anybody to install that one. I removed it, but it does not give me a warm and fuzzy feeling about ubuntu or xubuntu.

Popularity-contest is installed by default, but it is opt-in; you have to tick a box in Software Sources in before it starts doing its thing.

---

### Post by bustard on 2011-11-21
> **Larkspur said:**
> I can't help you with your main question, but about this one:



Popularity-contest is installed by default, but it is opt-in; you have to tick a box in Software Sources in before it starts doing its thing.Thanks

---

### Post by matt_symes on 2011-11-21
Hi

See what you make of this. I am unsure if it's related but i thought i would post it...

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014)

Kind regards

---

### Post by bustard on 2011-11-22
> **matt_symes said:**
> Hi

See what you make of this. I am unsure if it's related but i thought i would post it...

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014)

Kind regardsThanks, it looks like ecryptfs has some long-standing problems (since 2009, from that list).

---

