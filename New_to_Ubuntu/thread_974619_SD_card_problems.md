---
title: "SD card problems"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by freelancelote on 2008-11-07
Hi,
my new SD card is not recognised when using my external card reader but it is when using the internal one.
I know is not a problem with the external card reader because it works fine when using my old SD card.

Any ideas on how to fix that?

thanks

---

### Post by B34ST1Y on 2008-11-07
see if you can see the partition in "gparted" . Run the program by typing into terminal ```
sudo gparted
```

if its not installed, try installing it```
sudo apt-get install gparted
```

---

### Post by freelancelote on 2008-11-07
> **B34ST1Y said:**
> see if you can see the partition in "gparted" . Run the program by typing into terminal ```
sudo gparted
```

if its not installed, try installing it```
sudo apt-get install gparted
```

I'm afraid I can't see the partition with gparted.

---

### Post by B34ST1Y on 2008-11-07
you may be missing / incorrect / out of date   usb drivers. make sure you have all available updates for your current setup

---

### Post by freelancelote on 2008-11-07
Is that done with the Synaptic Package Manager? if it is... the system is up to date.

---

### Post by edgaruy1980 on 2008-11-07
I just installed Kubuntu in an lenovo, and I had to look for my card reader drivers separately, just you need to know your hardware then you google your device, like mine it was a ricoh 5-1 card reader.

---

### Post by freelancelote on 2008-11-07
> **edgaruy1980 said:**
> I just installed Kubuntu in an lenovo, and I had to look for my card reader drivers separately, just you need to know your hardware then you google your device, like mine it was a ricoh 5-1 card reader.

Mhhh. But still, the card reader works with the old SD Card.

---

