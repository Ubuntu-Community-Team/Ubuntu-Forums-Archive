---
title: "Let me tell you about my mother"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by cray5656 on 2012-05-23
My mum loves Ubuntu ( 11.04?, the previous version) because it has that uplifting music on start up :-)

I am sure that music isnt there on 12.04 so is there a way that we can upgrade her and retain the start up music?

ALso I had a bit of a ***** of a time setting up her Cannon printer to run on the previous version, does that mean if we upgrade that we will have to set all that up again?
Thanks

---

### Post by fantab on 2012-05-24
> **cray5656 said:**
> My mum loves Ubuntu ( 11.04?, the previous version) because it has that uplifting music on start up :-)

I am sure that music isnt there on 12.04 so is there a way that we can upgrade her and retain the start up music?

ALso I had a bit of a ***** of a time setting up her Cannon printer to run on the previous version, does that mean if we upgrade that we will have to set all that up again?
Thanks

Upgrades from Update Manager, as opposed to Clean Upgrade from CD/DVD/USB, are known to be messy. It may mess up your configurations. Personally, I would recommend a Clean Upgrade. Since you have configured the Printer before, you can do it again... ;)  On the brighter side Ubuntu 12.04 is an LTS with 5 years support, so once properly configured you don't have to worry about it for next five years.

As far as login sound is concerned, its simple: In 12.04 open STARTUP APPLICATIONS and scroll down to GNOME Login Sound, select it and EDIT. In the Edit dialog box paste the following _as it is_ in Command box replacing whatever there is already:

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```and SAVE it.
That is all and it will be uplifting again. :guitar:

---

### Post by cray5656 on 2012-05-24
I am a little waery of a clean instal only because my mother has so much stuff on her computer.

I guess its working fine so I will leave it.

My 2 sons have the latest version so I will see if I can put the uplifting music on there :-)

Thanks!

---

### Post by Lord Burghley on 2012-05-24
Thanks for that, fantab. Works like a charm! :)

---

