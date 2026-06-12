---
title: "ubuntu 12 with google earth"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-07-01
Hi all, 
I have up-graded from ver 10.10 Mavrick to ver 12 ?lts of Ubuntu, 
The last bit I need to install "if that is the right wording" would be the Place Marks I have to use in google earth, these are from Ireland, South Wales, South Spain, Portugal, Tampa USA, and Canda

I have copied the "MyPlace.kml" or some thing like that from version 10 to a stick, found "How To, but its win / mac only" [http://support.google.com/earth/bin/answer.py?hl=en&answer=166438](http://support.google.com/earth/bin/answer.py?hl=en&answer=166438)

It has to be some what the same as win/mac but I just can't find where ubuntu installs these files to?

Some help please to get this thing finnally sorted, just noted, No spell checker on ubuntu 12 ?? How come

Dave

---

### Post by DeathByDenim on 2013-07-01
It should be in ~/.googleearth . It's an hidden directory in your home-directory.
As to the spell checking. Do you mean in your browser? If so, which browser?

---

### Post by DaveMcC on 2013-07-01
> **DeathByDenim said:**
> It should be in ~/.googleearth . It's an hidden directory in your home-directory.
As to the spell checking. Do you mean in your browser? If so, which browser?

Can't find my way into /.googlearth ???

Ya the spell checker here in firefox, on ver 10.10 Mavrick it seemed as if it was built into the whole OS

Also, on lubuntu when I installed gimp, I got ver 2.8, here 2.6

Strange wee things like that are back-ward facing

Dave

---

### Post by DeathByDenim on 2013-07-01
Yeah, it's a hidden directory. In the Dolphin filemanager you can either type the destination directly, or press Alt + .
I'm not sure how it is done in Nautilus though. I assume you also have a "go to folder"-thingy there?
Google Earth should automatically create that directory when you start it for the first time.
Alternatively, you can use the terminal and type:
```
cd ~/.googleearth
cp /media/usb/myplaces.kml .
```
where you should replace /media/usb/myplaces.kml with wherever you put the myplaces.xml file.

Does this link help for your spell checking needs: [https://support.mozilla.org/en-US/questions/952836](https://support.mozilla.org/en-US/questions/952836) ?

I think gimp is still on version 2.6 in Ubuntu 12.04. Only in Ubuntu 12.10 they moved up to gimp 2.8, I believe. Your Lubuntu is also 12.04?

---

### Post by DaveMcC on 2013-07-01
> **DeathByDenim said:**
> Yeah, it's a hidden directory. In the Dolphin filemanager you can either type the destination directly, or press Alt + .
I'm not sure how it is done in Nautilus though. I assume you also have a "go to folder"-thingy there?
Google Earth should automatically create that directory when you start it for the first time.
Alternatively, you can use the terminal and type:
```
cd ~/.googleearth
cp /media/usb/myplaces.kml .
```
where you should replace /media/usb/myplaces.kml with wherever you put the myplaces.xml file.

Does this link help for your spell checking needs: [https://support.mozilla.org/en-US/questions/952836](https://support.mozilla.org/en-US/questions/952836) ?

I think gimp is still on version 2.6 in Ubuntu 12.04. Only in Ubuntu 12.10 they moved up to gimp 2.8, I believe. Your Lubuntu is also 12.04?

OK, in reverse, Ubuntu is 12.04 here, that should explain gimp, thanks
Installed spell checker UK version cuz I live in Northern Ireland, or North of Ireland, or as we say Ulster

As for the top bit, sorry I am lost with that part, Dolphin is a mammal that swims in water, Nautilus is the coffee shop down at the harbour,.... I don't have a "go to folder" got a home folder with other folders in them
Desktop, Doc's Downloads, Video etc

Useless at this stuff, I am really I am

Dave

PS it's near 1am, better go to bed or the wife will err, frying pan time again

---

### Post by DeathByDenim on 2013-07-01
Ha, sorry. The file manager in KDE is called Dolphin and the one in Gnome is called Nautilus. I didn't name those things. :)
If you go through the menus, is there anything that says something like "Show hidden files"?

If not, then your best bet is to use the terminal commands I gave you.

PS No rush. I wouldn't want you involved in a frying pan incident. :)

---

