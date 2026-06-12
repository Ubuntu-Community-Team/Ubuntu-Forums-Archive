---
title: "Unable to start ubuntu from dvd | going directly to grub rescue"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by paul195 on 2015-02-16
Hi guys,

so i bought a hp 355 notebook and wanted to install ubuntu from the dvd. There is just freedos on the notebook so i thought i won't have any problems. I already changed the BIOS settings in the way that it will boot from the dvd, insert the disc and waited to be able to install ubuntu. Unfortunately there is no installing screen or live screen coming up but just "Welcome to GRUB!" and an error: cdrom read error

So i was spending a night with trying to figure out what i did wrong but couldn't find anything. Any help would be much appreciated. Thanks a lot in advance!

---

### Post by fantab on 2015-02-16
> error: cdrom read error

That indicates a bad burn. Reburn the ubuntu.iso to  another DVD. Try using a USB pen drive instead of DVD, it will be easy on your purse.

---

### Post by kc1di on 2015-02-16
Also what video driver is in use please ?

---

### Post by paul195 on 2015-02-16
The DVD should be ok it's from a linux magazin that you can get in Germany/Austria that's why I don't really think that it could be a bad burn. Also my MacBook is giving me a hard time getting in iso on a USB pen drive.

How can i find out the video driver? Sorry if I'm asking silly questions but I'm a bit lost right now.

---

### Post by kc1di on 2015-02-16
if your machine uses Nvidia graphics then you'll need to enter nomodeset to the boot line. but it seems like your not getting even that far.

Even though the disc came from a magazine doesn't mean it was burned correctly. they make mistakes also.
try downloading a new ISO image from[ here]("http://www.ubuntu.com/download/desktop") and burning that to a DVD and try again. 

if your using windows you can burn the iso using information on this[ page: ]("https://help.ubuntu.com/community/BurningIsoHowto")

good luck :)

---

### Post by paul195 on 2015-02-16
yeah guess you're right and the DVD just isn't burned correctly. So i will try with a new ISO image and burning by myself. Hope it works better 

thanks a lot :)

---

### Post by paul195 on 2015-02-16
So i solved my problem by creating a ISO image on a USB pen drive ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)). Took me some time and nerves but now everything looks nice and fine.

---

### Post by kc1di on 2015-02-16
Glad it's working for you, enjoy.

---

