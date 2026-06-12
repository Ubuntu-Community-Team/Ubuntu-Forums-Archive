---
title: "TomTom appearing as Wired Connection 2"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coco_loco on 2011-09-20
Hi everybody

I'm running oneiric exclusively, have some bugs but can live with it.

I just bought a brand new Tomtom start 25 - wanted to update it and most of all, put french language on it using jTomtom.

So I plugged it with the USB-cable, but jTomtom is telling me that there's no GPS connected.
lsusb is telling me that there's a TomTom device.

While plugging it in / out and over again, I doscovered that each time I plug it in, there's a new Wired Connection (2) appearing... 

I was googling and searching in the forums with no luck - am I alone with this issue?

Thanks for any suggestions
coco-loco

P.S.: Avoid suggesting dual boot - this is no option for me!

---

### Post by BbUiDgZ on 2011-09-20
same happens to me when I tether my android phone - only it's supposed to happen.

is there anyway to turn off network connections and/or GPS on your tomtom?

I know nothing about tomtoms

---

### Post by ronacc on 2011-09-20
try running jtomtom from a terminal , that may tell you something , also it may not like the java you have installed .

---

### Post by coco_loco on 2011-09-20
Actually it does not complain about the Java-Version - it just tells that there's no GPS connected.

However I don't think that it is due to jTomTom, it seems that the TomTom itself is not correctly detected since it definitively is no Wired Connection at all - at least for my understanding.

Following the documentation:
    - it shall be mounted as a drive, not as a network connection - if I understand that correctly.
    - one has just to plug the usb-cable in and start the tomtom, then mount the device manually (which is refused since it is already in use)

btw. : I can't find any settings that allow changing the connection mode

EDIT: I tried on a friend's 11.04 - same trouble ;o( perhaps it's meant to be like that but jTomTom does not recognize it?

---

### Post by ronacc on 2011-09-20
sorry to say but a lot of companies don't play nice with linux , I gave up trying to update my garmin maps on my ubuntu box and used my Mac .I thought just maybe it was the java because I have run into troubles with that before .

---

### Post by coco_loco on 2011-09-20
I've googled for quite a while now... it seeems that you're right (I might have known, I've had a Genious tablet and for a few years I was struggling with the x-config files at each dist-upgrade).

The Start xx series for TomTom may be updated with a browser based (this is probably the reason why it appears as a network connection) interface called MyTomTom . And guess... there are only win and os x versions of the plugin! 

I might have checked that out more precisely before! And the song remains the same...

---

