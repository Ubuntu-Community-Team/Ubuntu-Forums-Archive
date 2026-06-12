---
title: "Running Ubuntu 12.10 from an iso image on a DVD"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by Jonalt on 2013-04-26
I am trying to run Ubuntu 12.10 from a DVD iso image as a trial. When I try to boot from the disc it gets to the screen that asks if I want to install or just try it out. I select 'try out' and the screen then changes to the Ubuntu pattern on it, but no icons. [ie a blank desktop.] I left it like this for 5 or 10 minutes but nothing changed. Can anyone help re this? My PC has Windows XP. [I didn't use the 'checksum' because it looks complicated.]

Jonalt

---

### Post by slickymaster on 2013-04-26
Most probably your ISO image is corrupted, but the only way you have to confirm it is using the MD5 checksum. See [MD5SUM on Windows]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows") on how to do it, it's not that complicated.

So, now you have two options: confirm your iso using MD5 checksum or download a new iso image.

---

### Post by Jonalt on 2013-04-26
Thank you Slickymaster. 

I just used the winMD5Sum.exe and the MD5 Checksums are the same. What is the problem do you think?

Jonalt

---

### Post by slickymaster on 2013-04-26
There use to be a ***'Check CD for Defects'*** option available while booting from the CD/DVD, I can't say if it still exists as it has been a long time since I've use it.
Anyway if it's still there you can try it and wait until the process is complete and it will let you know if all of the files are 100% intact.
Other than that, I'll advise to read [Burning Iso Howto]("https://help.ubuntu.com/community/BurningIsoHowto") and follow the steps there.

---

### Post by Kopkins on 2013-04-26
When you boot press F6 when the first purple screen appears, it will bring you to a menu where you can select to check the disk for defects. I had and ISO that was otherwise fine, except for the partitioner. It would ruin partitions, now I always check to make sure the disk is okay before I try to install it. 

Good luck

Kopkins

---

### Post by holycow131415 on 2013-04-26
When you burn dvds slow burn it, 4x or 8x.

---

