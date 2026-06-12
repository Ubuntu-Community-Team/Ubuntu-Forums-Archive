---
title: "F-spot export to cd help"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2008-06-15
**[SIZE="3"][COLOR="DimGray"]HI, when I open F-spot then go to "Edit" and choose select all, then go to "Photo" and choose export to .. CD   I always get an error.   he is a screenshot   , what have I done wrong here? [/COLOR][/SIZE]**

---

### Post by Daveth on 2008-06-15
having just replicated your instructions, my copy takes me all the way to the "burn cd" option, so if you are using Hardy and are up to date, then we have the same version. I do not think it is you, but the program.
How many times have you tried it, and does it persist over re-boots etc?

---

### Post by MeTylerDurden on 2008-06-15
My bad,  last thing I go to is Create CD with options to cancel or export  also gives boxes to check  (write only these photos to cd) and (autorate)      what I did here was just push export.. I also tried to check boxes,but get same error.

---

### Post by MeTylerDurden on 2008-06-15
[B][SIZE="3"][COLOR="DarkOrange"]Any way of getting my pictures to a cd are welcome now..    would me editing some photos be the problem because I did alot of cropping and red eye removal..     



[COLOR="DimGray"]or am I just the all singing all dancing crap of the world[/COLOR][/COLOR][/SIZE][/B]

---

### Post by MeTylerDurden on 2008-06-16
**[SIZE="3"][COLOR="SlateGray"]Is any1 using F-spot  , if so how do I get my pictures to disc or transfer to another program that will copy to disk[/COLOR][/SIZE]**

---

### Post by senewag on 2008-06-16
Hi Tyler,
I am not an expert but since no-one else has jumped in here goes..

Since you have done cropping etc to some of your photos you could have 2 versions of the same photo on your computer,  so it is important to know which photos to send to the cd/dvd.
When you import photos, if you tick the "copy files to xxx folder" then your photos will be copied to that folder (the one you have set up in "preferences".  The photos will still be in the original folder but any red-eye editing etc you make will be done to the photos in the destination folder.  
But beware, if you didn't consistently have "copy files to xxx folder" ticked, then some of your photos will be in the source folder only and they will miss out on going to the cd/dvd.

You can sort out which imports are not in the destination folder by "find" "by import roll"  "selected import rolls" then do "edit" "copy location" and look at the clipboard on one of those photos to see if that batch is in the destination folder.

Also for each photo you modify, there will be 2 copied  i.e. photo.jpg and photo(modified).jpg.

You can copy the photos to a cd/dvd using nautilus or brasero or whatever.
  
Hope this is of some help,  F-spot is a great program.

---

### Post by tashmooclam on 2008-07-03
F-Spot gives me fits also. It works very badly for me. No slideshow, no burn to CD, imports photos and nests them in countless folders, leaving full screen mode quits the program. Otherwise, it's OK, and for free I guess that's what I can expect.

---

### Post by sdegrace on 2008-07-06
I'm really mad about Hardy and F-Spot. Actually, no release of Ubuntu has ever managed to make me mad in so many ways like Hardy does - I *used* to love getting new releases of Ubuntu. Managing digital photos is such an important part of what the average person uses their computer for, and for some reason, *for a long term service release*, Ubuntu thought it was a good idea to replace the simple and robust gthumb with the complicated and buggy F-Spot as the default app that gets launched. I'm far from computer illiterate, but the experience of having F-Spot pop up and suddenly have to grapple with a more complicated interface is disconcerting to say the least. The little suite of tools is nice, but the versioning and lack of undo is a really strange and uncomfortable system. But I could get over the change to F-Spot and maybe learn to love it if it worked - but it's fundamentally crippled.

So, I avoided F-Spot until yesterday I decided to give it a try. Now today I want to make a photo CD and guess what, I can't, same problem as you. Apparently this piece-of-cr4p software made it into Hardy with this gross, totally deal-killing bug, which didn't get fixed upstream apparently until May, and if supposedly fixed certainly hasn't made it back to Hardy (my system is fully updated). Uninstalling and reinstalling F-Spot did not help.

I can offer you one bit of actual helpful advice, though. My advice is to not use F-Spot. You might remember the program that handled photo import in older versions of Ubuntu - that was gthumb. gthumb did and still does work great. If you want to tell F-Spot to F-Off and go back to gthumb, do the following:

[LIST=1]
[*]Go to System -> Preferences -> Removable Drives and Media
[*]On the Cameras tab leave "Import digital photographs when connected" checked if you still want that behaviour
[*]For "Command:" enter the following:
gthumb --import-photos
[/LIST]

My further advice to to remember the command that was in there for F-Spot (f-spot-import) and think about trying F-Spot again in October when Intrepid comes out. F-Spot actually holds real promise as a nice way to manage and edit your photos, it's just very much Not Ready For Prime Time. Yet (hopefully).

---

