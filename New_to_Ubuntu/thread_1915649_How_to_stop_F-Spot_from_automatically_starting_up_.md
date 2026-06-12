---
title: "How to stop F-Spot from automatically starting up when I insert a flash card"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by rocksockdoc on 2012-01-26
It used to be that nothing happened when I inserted a camera flash card into my Lenovo X61 laptop flash card slot - but now F-Spot comes up and tries to import pictures.

I manage my own pictures with my own script (orient, shrink, annotate, rename by exif data, etc.) so I don't want to have to kill F-Spot every time I insert the flash card:
- [Stringing commands together to manage typical digital photo operations]("http://ubuntuforums.org/showthread.php?t=1839153")

But I can't figure out HOW F-Spot knows to come up when a flash card is inserted. (It's not in F-Spot "Edit->Preferences".)

Do you know?

What is the setting (where is the setting?) that tells F-spot to STOP opening when a flash card is inserted? 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211470&stc=1&d=1327611425[/IMG]

---

### Post by rocksockdoc on 2012-01-26
I looked at the right-click properties of the flash card itself, but there was nothing there either.

What is it that tells Gnome to open up the flash card in F-Spot when I insert that flash card into the computer slot?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211471&stc=1&d=1327611726[/IMG]

---

### Post by rocksockdoc on 2012-01-30
Anyone?

---

### Post by rocksockdoc on 2012-02-03
Still no suggestions?

What I'll try, in desperation, is to uninstall F-Spot.

Then it can't pop up. :)

---

### Post by rocksockdoc on 2012-02-03
Drat!

Now Shotwell Photo Manager automatically comes up!

I'm going to have to remove it too!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211946&stc=1&d=1328296240[/IMG]

---

### Post by rocksockdoc on 2012-02-03
OK. That worked. 

With both F-Spot and Shotwell removed, inserting a flash card simply mounts that flash card (which is what it used to do until F-Spot mysteriously started popping up).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211947&stc=1&d=1328296690[/IMG]

---

### Post by eric-yorba on 2012-02-03
In Oneiric, it's just System Settings -> Removable Media.  All the options are there.

In previous versions, I believe it was in the Nautilus preferences.

---

### Post by rocksockdoc on 2012-02-04
> **eric-yorba said:**
> In Oneiric, it's just System Settings -> Removable Media

I'm using 10.04 Lucid Lynx and it's not in System->Preferences nor in System->Administration.

Where else would I find Nautilus settings?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211975&stc=1&d=1328331723[/IMG]

---

### Post by yetiman64 on 2012-02-04
Open any nautilus window (eg. your home folder), go to Edit > Preferences > Removable Media tab. Select "do nothing" for photos. 

If you re-install shotwell or f-spot remember to repeat the above. 

You can have both of those applications installed and still have nothing happen when photos are on the media by using the settings here.

---

### Post by rocksockdoc on 2012-02-04
> **yetiman64 said:**
> Open any nautilus window (eg. your home folder), go to Edit > Preferences > Removable Media tab. Select "do nothing" for photos.

That makes sense. 

Nautilus won't give me the option anymore (since there are no programs installed) but I'm sure it would have worked had I not deleted all the photo organization software in an apparently misguided attempt to fix this problem on my own.

I wonder why nobody suggested that though?

Maybe it's a new feature people don't know about yet?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212013&stc=1&d=1328376747[/IMG]

---

### Post by eric-yorba on 2012-02-06
> **rocksockdoc said:**
> Maybe it's a new feature people don't know about yet?
New feature? You're running a version of Ubuntu that's a *year* old! :)

---

