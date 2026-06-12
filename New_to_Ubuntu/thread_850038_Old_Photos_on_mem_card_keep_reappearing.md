---
title: "Old Photos on mem card keep reappearing"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by MarkX on 2008-07-05
Hello, semi-noob here!
I installed 7.10 on a friends computer. 
Main problem: 
Whenever my friend inserts the memory card from his camera into the card reader, the icons that show  are of much older pictures which have long been deleted. (The camera btw keeps the old numbering system of pics, the labels are the old numbers)) Once he clicks on the icons the new pics are maximised as they should. What's the fix please?



Also: Should I upgrade him to 8.04? 
I'm scared to do that because once I fixed the numerous bugs in 7.10 I don't want to "upgrade" to a whole new batch of problems.

---

### Post by sayakb on 2008-07-05
Do you move the pics to trash or delete them permanently? Try deleting them (Shift + Del) the pics and see if they come back.
Also, regarding the upgrade, there are some chances that the upgrade to 8.04 doesn't work successfully (well, it seems to have worked for quite many people, Im not in the list though). You may have a clean installation of Hardy 8.04.1. 8.04.1 has numerous bug-fixes from 8.04.
Link: [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by nikgare on 2008-07-05
they might be in a trash folder on the disk.
Using Nautilous, you can select "show hidden files" from the menu, and then look for folders labels ".trash" - note this name has a full stop infront of it so it's hidden.

---

### Post by lisati on 2008-07-05
There might be a file e.g. thumbs.db somewher which contains the old & incorrect image for the newer photos.

---

### Post by sayakb on 2008-07-05
Isn't thumbs.db a Windows generated file? If it does exist, then Windows me be the culprit of not being able to delete the file.

@OP
Also, check if the memory card has any physical write lock activated. If possible, backup all data on it. **Delete **the memory card's partition via gparted and create it again. I assume it has a vFAT or FAT16 fs.

---

### Post by CyberCowboy on 2008-07-05
Another thing is to make sure you unmount the card.  I had the exact same problem in 7.10 and then noticed that I wasn't unmounting it, when I did a right click / unmount it then said it was writing on the card, and then that it was ok the remove, at that point it did the actual write.

---

### Post by ixus_123 on 2008-07-05
Never format or delete pictures from a memory card (for photo use) in PC software.  It doesn't matter if it's Linux, Windows or OS X.

Always format the card in the camera it is to be used in with new session

The camera will store the file number system for future uses.

Camera flash uses the FAT filesystem and the file allocation table is extremely fragile. While it will likely hold up for general use, there is nothing like losing a bunch of holiday pictures.

The way you can minimise this is to help the filesystem keep things ordered by not deleting pictures in camera (so that all picures are stored squebtially, and formatting the card in the camera it is to be used in with each new useage session.

---

### Post by MarkX on 2008-07-05
OK:

Erased all pictures from card in-camera as per camera instructions.
(It's vfat btw.)
Deleted all files in trash.
No sign of hidden files on card, with "view hidden files" enabled.
Unmounted card before extracting from reader.

Took some  pics, inserted card into card reader and the problem remained:
The card icon appears and inside are a bunch of icons of long erased pictures.
When clicking on the old pics the new pics are maximised.
Same happens if I move the file with the photos from the card onnto the desktop, old pics display in icons, new pics seen when when maximised.

Now I think I SOLVED IT ?!
I deleted all photos from the card via the computer. The old icons are gone and the new pictures are displayed.

It seems that for some reason it is actually better to delete the photos on the computer than in the camera, the opposite of how it should be! Another Linux quirk....

---

### Post by steveneddy on 2008-07-05
> **MarkX said:**
> 

Now I think I SOLVED IT ?!
I deleted all photos from the card via the computer. The old icons are gone and the new pictures are displayed.

It seems that for some reason it is actually better to delete the photos on the computer than in the camera, the opposite of how it should be! Another Linux quirk....

I was going to suggest this. I always edit the pics (delete what we don't want) on the laptop. We don't run Windows, so we've always done it on the computer.

Just remember to empty the trash when deleting pics and remember to unmount the card before you remove it.

Easy Peasy.

---

