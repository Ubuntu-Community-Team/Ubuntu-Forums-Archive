---
title: "hcitools install how to?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by PT.Linn.A on 2008-08-22
I am attempting to setup Bluetooth, and am told that I need **hcitools**.

I cannot seem to find it it Synaptic. Nor am I able to locate it with a sudo apt-get.

Where, and how, do I get this app to install it?

---

### Post by TheMaxzilla on 2008-08-22
Try this:
```
sudo apt-cache search hcitools
```
If there's more than one, pick which one suits your needs.

---

### Post by PT.Linn.A on 2008-08-22
> **TheMaxzilla said:**
> Try this:
```
sudo apt-cache search hcitools
```
If there's more than one, pick which one suits your needs.

I tried that in terminal with no results.

I also searched Syanaptic again for hcitools, and also came up with a blank search.

I cannot seem to locate this app. at all.  :(

---

### Post by cariboo on 2008-08-22
Is **bluez-hcidump** what you are looking for? You may aslo need **btscanner**. They are available in the repositories.

Jim

---

### Post by PT.Linn.A on 2008-08-22
I have both **bluez-hcidump** and **btscanner** installed.

But, I am still told to run hcitools in the terminal, and cannot find it anywhere.

---

