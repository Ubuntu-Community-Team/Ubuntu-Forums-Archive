---
title: "xD card"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by iLona on 2008-06-04
I have an Olympus camera with an xD card, and I would like to upload the pictures directly from the card onto my computer. However Ubuntu does not recognise that I inserted the card into the slot. Are xD cards compatible with Ubuntu? If so, how would I get it to work?
Thanks,
iLona

---

### Post by Cypher on 2008-06-04
You have a reader I presume? If the reader is a USB one, the xD card should show up when plugged in..

---

### Post by kamitsukai on 2008-06-04
> **iLona said:**
> I have an Olympus camera with an xD card, and I would like to upload the pictures directly from the card onto my computer. However Ubuntu does not recognise that I inserted the card into the slot. Are xD cards compatible with Ubuntu? If so, how would I get it to work?
Thanks,
iLona

the XD card wouldn't be the problem it's your card reader you need to find drivers for it! what make is it? is it a built in one?

if you don't know run

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

in the terminal and upload the html file it creates in you home directory:)

---

### Post by stchman on 2008-06-04
> **iLona said:**
> I have an Olympus camera with an xD card, and I would like to upload the pictures directly from the card onto my computer. However Ubuntu does not recognise that I inserted the card into the slot. Are xD cards compatible with Ubuntu? If so, how would I get it to work?
Thanks,
iLona

My Toshiba has the Ti 5 in 1 reader.  That reader works with SD cards OOB but not xD.  I have an xD to USB adapter that works for that.

---

