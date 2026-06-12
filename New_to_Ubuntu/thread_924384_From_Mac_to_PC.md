---
title: "From Mac to PC"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by greg@medialounge.tv on 2008-09-19
So, I'm thinking that I could download Ubuntu to my Mac, burn it to CD, then use it to start my down and out Dell laptop, install it as the system on the Dell so I can use it again.

Am I thinking straight?

Thanks in advance for any and all help.

---

### Post by Delirium_Trigger on 2008-09-19
I believe I understand what you're asking.
You want to download the .iso of Ubuntu on your Mac and make the CD there.
Then you want to take said CD and run/install it on your Dell PC.
If that's correct then yes, that will work.

---

### Post by greg@medialounge.tv on 2008-09-19
Thanks, I'll give it go.

---

### Post by greg@medialounge.tv on 2008-09-19
So after I download it, I drag it to the cd, obviously without opening it because it wold then install on my Mac, then insert it into the Dell, turn on the Dell and ?

---

### Post by purplepaint on 2008-09-19
You have to burn the .iso file as a CD image ([how-to](https://help.ubuntu.com/community/BurningIsoHowto#In%20Mac%20OS%20X)).  "Opening" it with your file browser shouldn't do anything, but when you've burned the image, you put the CD in the Dell's CD ROM drive and restart it with the CD in it.  It should boot from the CD.  ([how-to](https://help.ubuntu.com/community/GraphicalInstall))

---

### Post by greg@medialounge.tv on 2008-09-19
I've dragged the Ubuntu alias icon to a cd, I'm burnin it now....the Dell...Pressed F12, waited for the cd load, chose the cd drive, 'loading...' flashes by then the screen goes black, up comes the Windows XP start screen, tehn...ye olde "KERNEL32.dll was not found,"   yeah, I know.  Back where I started.

Now what to do?

---

### Post by zvacet on 2008-09-19
Using link **purplepaint** posted to you see hot to** check md5sum** and **Cd integrity**.

---

### Post by Cypher on 2008-09-19
You don't want to burn the ISO image as a data file, that isn't bootable. You want to burn it to the CD as a CD-image. No clue how you do that in Mac, but look for that specifically..

---

### Post by madsmeg on 2008-09-19
[http://www.macosxhints.com/article.php?story=20060619181010389](http://www.macosxhints.com/article.php?story=20060619181010389) try here to find out how to burn an iso

---

### Post by greg@medialounge.tv on 2008-09-20
Thanks, but Disk Utilities sits still when I choose, the "open" button remains grayed out.

---

### Post by issih on 2008-09-20
On the mac, mount the iso (just double click on it) then open disk utility which will now have the iso in the list on the left. select that iso and click burn.

The iso is an image of the disc, dragging it into the cd just creates a data cd containing the iso file, not a bootable cd.

Do as stated above, and ensure that the dell's bios is set to boot from the cd prior to trying the hard drive and you should be all set.

Hope that helps

---

