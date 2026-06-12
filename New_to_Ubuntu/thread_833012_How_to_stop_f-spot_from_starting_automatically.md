---
title: "How to stop f-spot from starting automatically?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by silkstone on 2008-06-18
I'm using Ubuntu Hardy. Whenever I slot a CF card with image files into the card reader, f-spot starts up and wants to import the photos. I don't want it to - I just want to copy the files manually to the folder of my choice, using Nautilus or whatever.

I have unchecked the digital camera import option in Tools > Preferences > Removable Drives & Media, but it doesn't make any difference - f-spot still starts up.

Could someone please suggest a remedy? Thanks!

---

### Post by billgoldberg on 2008-06-18
Link:

[http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/](http://linuxowns.wordpress.com/2008/05/31/changing-default-applications/)

---

### Post by silkstone on 2008-06-18
Thanks.

I opened defaults.list and found two references to f-spot...

```
x-content/image-dcf=f-spot-import.desktop
x-content/image-picturecd=f-spot-import.desktop
```

So I put a # and a space in front of each...

```
# x-content/image-dcf=f-spot-import.desktop
# x-content/image-picturecd=f-spot-import.desktop
```

Then I restarted the machine, and when I inserted a CF card, f-spot still started up!

Now I'm totally baffled.

---

### Post by Tom--d on 2008-06-18
Thats an easy one :D

System > Pref > Removable drives .... 

Delete all which says f-spot :D!

---

### Post by silkstone on 2008-06-18
I did that first, Tom. Unchecked the box - f-spot still loaded. Then checked the box, deleted f-spot-import and tried again. Still loaded... :confused:

---

### Post by senewag on 2008-06-18
Hi,
Start up F-spot and "edit"  "preferences"  and tick "allow other programs to manipulate F-spot"

---

### Post by timcredible on 2008-06-18
> **senewag said:**
> Hi,
Start up F-spot and "edit"  "preferences"  and tick "allow other programs to manipulate F-spot"

that didn't do anything.  i've been looking for a way to have digikam start instead of f-spot since 8.04 came out, haven't found anything yet.

---

### Post by MasterSander on 2008-06-18
You can try to uninstall it :P Then it won't launch anymore.

---

### Post by philinux on 2008-06-18
Instead of hashes in the config file why not choose your preferred app.

---

### Post by silkstone on 2008-06-18
Well I don't really want anything to happen apart from the card to be mounted. It would be fine if the file browser launched.

Would it be OK to change the defaults.list entry to...

x-content/image-dcf=nautilus

instead of =f-spot-import.desktop

?

---

### Post by mc4man on 2008-06-18
On my system the card (sd) is treated as a drive not a camera, to turn off f-spot i went to preferences -> file management -> media -> photos and set it to open folder

---

### Post by silkstone on 2008-06-18
Unfortunately on mine there is no File Management option under Preferences.

---

### Post by philinux on 2008-06-18
Use places>home folder.

Then Edit Prefs> click the media tab.

Look down the list for photo's. In the drop down menu are you options.

---

### Post by mc4man on 2008-06-18
either go to edit menus (r. click on applications) click (highlight) preferences on left and then on right side ck (enable) file management or go places -> home -> edit -> preferences

---

### Post by silkstone on 2008-06-18
That's it! :) Thanks mc4man, philinux and everyone else who has offered suggestions.

It does seem a little buried there, doesn't it? Maybe they could have all that under Tools > Preferences. I'm sure it was easier on Feisty, but sorted now anyway.

---

### Post by Dafydd on 2009-10-21
> **silkstone said:**
> That's it! :) Thanks mc4man, philinux and everyone else who has offered suggestions.

It does seem a little buried there, doesn't it? Maybe they could have all that under Tools > Preferences. I'm sure it was easier on Feisty, but sorted now anyway.

I've had this hassle for a while and could not find options in "tools > preferences > media " to stop f-spot opening.

But now I've just opened nautilus and went to > tools > preferences.

There you can stop it.

Dafydd

---

