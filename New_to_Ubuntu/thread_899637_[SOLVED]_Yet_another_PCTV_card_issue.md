---
title: "[SOLVED] Yet another PCTV card issue"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-08-24
I have a PCTV Stereo card (supported saa7134 card=26 tuner=33) that was working fine on Windows and I can't make it work properly on Ubuntu.

After following the tutorials, the card is recognized and loaded during initialization, I have image and sound if Composite input is selected, but I can't make TVTime properly tune the cable channel using the RF antena input.

When running the command "tvtime-scanner" a lot of channels are recognized and added to the "stations.xml" file, but they all display only static. It should only display 1 functioning channel, which is exactly at 61.25MHz. I have configured the channel entry, adding this frequency, but still see only static.

I need to fix this, but I think my TV card has Poltergeist.

---

### Post by billgoldberg on 2008-08-24
I suggest you pose this question in the correct forum.

You won't get much help in the absolute beginners forum.

---

### Post by lovinglinux on 2008-08-24
> **billgoldberg said:**
> I suggest you pose this question in the correct forum.

You won't get much help in the absolute beginners forum.

Thanks. Already added a new thread in the Multimedia & Video.

---

### Post by lovinglinux on 2008-08-30
I finally managed to configure it properly with image and sound.

Here is what I did. I don't know if all steps are necessary, but it is working so I will not change it.

```
sudo gedit /etc/modprobe.d/options
```

then added this at the end of the file and saved

```
options saa7134 card=26 tuner=33 alsa=1
```

then 

```
sudo modprobe saa7134 card=26 tuner=33
```

then opened TVTime and did a channel scan using PAL-M

---

