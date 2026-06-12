---
title: "Shotwell has mixed up my photos."
date: 2014-06-05
forum: New to Ubuntu
---

### Post by RayArdia on 2014-06-05
Haven't used Shotwell for a while but now I've got back to it I find that:-
1. Have lost the vast majority of my Tags.
2. Photos are filed under the wrong dates, eg photos taken in 2014 are filed in 2007.
Is there a way to make Shotwell re-sort according to exif data?

---

### Post by RayArdia on 2014-06-07
> **RayArdia said:**
> Haven't used Shotwell for a while but now I've got back to it I find that:-
1. Have lost the vast majority of my Tags.
2. Photos are filed under the wrong dates, eg photos taken in 2014 are filed in 2007.
Is there a way to make Shotwell re-sort according to exif data?

Further to my post above, I have tried (via Software Centre) removing and re-installing Shotwell with no improvement at all.

As I understand things, each photo carries its own exif data and its tags. All my photos are filed in folder Pictures. Surely, if I am able to fully uninstall Shotwell and then install it anew, it will start 'with a clean sheet' and do what it is supposed to do - organise my photos.

I've never had any problem with the application before but I'm now rapidly losing confidence in it and thinking of how I can better achieve the desired resut!

---

### Post by vanadium on 2014-06-08
Removing/installing does not help, because that does not remove your user data, which probably is where the problem lies.

The Shotwel database is stored under ~/.local/share/shotwell/data.

- A first thing you could try: in that folder, there will be a photo.db.bak database. Perhaps first check the sizes of photo.db.bak and photo.db. If the sizes are largely different, and especially if the size of photo.db is less than photo.db.bak, this may be a result of corruption.
You may now try to reuse the backup copy of the database: Rename photo.db to something like photo.db.corrupt, and rename photo.db.bak to photo.db. Start Shotwell to check whether all is OK again. Shotwell will automatically be updating your library and depending on your settings, reimport pictures that were not yet in the old database.

- If that does not work, you may need to restart from scratch. Rename .local/share/shotwell to something like  .local/share/shotwell_corrupt. Start shotwell: now, it will be as when you started shotwell for the very first time.

I am afraid tags will be lost with the latter approach. Certainly, any edits will be lost.

---

### Post by RayArdia on 2014-06-08
Re: Perhaps first check the sizes of photo.db.bak and photo.db. If the sizes are largely different, and especially if the size of photo.db is less than photo.db.bak, this may be a result of corruption.
What command to show sizes? Am confused by many options!

---

### Post by vanadium on 2014-06-09
File operations are done with your file browser. Load your file browser, find the files and from right-clik / properties you will learn about the file size.

.local is a hidden directory in your home folder: you can tell that because the name begins with a dot. By default, you will not see it in your file manager. Select "View - Show Hidden Files" (or simply press Ctrl+H) to toggle the display of these hidden files on or off.

There is indeed something risky about using Shotwell. I am now also starting to use Shotwell because it allows much easier access to the pictures. However, I will simultaniously maintain my file-system based organisation as before, so not all is lost when suddenly Shotwell breaks or is not further developped. To that aim, I continue to "manually" import photos, i.e., by naming the pictures myself (using renrot files are renamed to date-time.jpg) and putting them manually in a folder (e.g. "2014/2014-06-01 Travel to London"). In Shotwell, you can set it to automatically add files upon startup. This way, Shotwell reads my newly imported files upon startup, and I can continue to organize and tag them in Shotwell.

Shotwell can write tags to the image files. Perhaps at some time, I will allow Shotwell to do so. Thus, also tags would also be preserved outside of Shotwell (probably not the hierarchy).

---

### Post by RayArdia on 2014-06-09
> **vanadium said:**
> File operations are done with your file browser. Load your file browser, find the files and from right-clik / properties you will learn about the file size.

.local is a hidden directory in your home folder: you can tell that because the name begins with a dot. By default, you will not see it in your file manager. Select "View - Show Hidden Files" (or simply press Ctrl+H) to toggle the display of these hidden files on or off.

There is indeed something risky about using Shotwell. I am now also starting to use Shotwell because it allows much easier access to the pictures. However, I will simultaniously maintain my file-system based organisation as before, so not all is lost when suddenly Shotwell breaks or is not further developped. To that aim, I continue to "manually" import photos, i.e., by naming the pictures myself (using renrot files are renamed to date-time.jpg) and putting them manually in a folder (e.g. "2014/2014-06-01 Travel to London"). In Shotwell, you can set it to automatically add files upon startup. This way, Shotwell reads my newly imported files upon startup, and I can continue to organize and tag them in Shotwell.

Shotwell can write tags to the image files. Perhaps at some time, I will allow Shotwell to do so. Thus, also tags would also be preserved outside of Shotwell (probably not the hierarchy).

Thanks Vanadium. I'm sorry I misunderstood your instructions - thought you were suggesting I use Terminal. 
When I examine the two files photo.db and photo.db.bak I find they're the same size, each is 8.5MB. I thought this rather small for files which 'look after' some 8500 photos, what do you think.
My Pictures folder appears to hold all the photos but Shotwell seem to have lost whole 'year's worths' of photos and mis-filed most of the others. There are virtually no tags at all.
In addition it has added a lot of .jpeg files which are not photos. Can I somehow select only those .jpeg files which contain exif data and put all the rest in a holding file for later sorting? ( I know I have some photos which are scanned copies of old photographs which have yet to have exif data added, so I really must avoid losing those in any sorting).

Are tags not held in the .jpeg files exif data? I thought they were and USED to be quite happy with the way Shotwell handled things - now I'm not so sure!

I have read your comments starting with "There is indeed something risky about using Shotwell". Is this a general view amongst expert users? As a 76-year old I really want a _risk-free_ means of organising my family's photos and I thought I had it in Shotwell. All the present hassle has ocurred since upgrading to Ubuntu 14.04 and I just wish I could revert to how things were.

Am I alone in experiencing problems a) With Shotwell running under 14.04, and, b) With 14.04 telling me, quite often, that it is 'experiencing problems' and inviting me to send an error report? Will post this latter question again on a more appropriate thread.

---

### Post by open2reason on 2014-06-10
Ray,
would it be possible for you to examine your tags via Digikam (in Ubuntu software centre) as this should then confirm what exactly information is held with your photos? 
You could also search by tag and search by time line to see if dates of your photos are correct.

You do not need to amend / update information but use Digikam to obtain another view of things.

You may then be able to form an opinion as to the fitness of Shotwell to manage your photo collection.

---

### Post by vanadium on 2014-06-10
> **RayArdia said:**
> When I examine the two files photo.db and photo.db.bak I find they're the same size, each is 8.5MB. I thought this rather small for files which 'look after' some 8500 photos, what do you think.

Does look like a normal size to me. The database contains only textual information.

Both files are equal in size, which does not lead me to suspect that one would be corrupt.

First thing I would try, nevertheless, is try the photo.db.bak.
- Close Shotwell
- Rename photo.db to for example photo.db.corrupt
- Rename photo.db.bak to photo.db

Start Shotwell again: it will now use the backup copy. With some luck, this will work again as expected (although I would not hold my breath).

To have all your pictures imported again, you can start from scratch by removing the shotwel user configuration folder. To do that, leave Shotwell, and rename .local/share/shotwell to something like .local/share/shotwell_corrupt. Start Shotwell again: it will be as if you are running it for the first time.

Working this way, you may always revert to the old situation. Delete the newly created .local/share/shotwell and rename .local/share/shotwell_corrupt back to .local/share/shotwell
> 
My Pictures folder appears to hold all the photos but Shotwell seem to have lost whole 'year's worths' of photos and mis-filed most of the others. There are virtually no tags at all.
Shotwell in principle does not touch your photo files, fortunately.
> 
In addition it has added a lot of .jpeg files which are not photos. Can I somehow select only those .jpeg files which contain exif data and put all the rest in a holding file for later sorting? ( I know I have some photos which are scanned copies of old photographs which have yet to have exif data added, so I really must avoid losing those in any sorting).

I am afraid there is no automated way in Shotwell for that. You have to pick the jpegs in Shotwell then drag them to an event, or create a new event for them.

On newly imported pictures, all these without exif time tags will be sorted in "No Event". Those with exif time tags will be automatically sorted in Events.
> 
Are tags not held in the .jpeg files exif data? I thought they were and USED to be quite happy with the way Shotwell handled things - now I'm not so sure!

There is an option in Shotwell to write tags to the jpeg files as well. By default, this is not done. If you enable the setting, only new tags you add in the future will be written to the picture files. I don't think it is possible to have Shotwell write all of its tags to the files.
> 
I have read your comments starting with "There is indeed something risky about using Shotwell". Is this a general view amongst expert users? As a 76-year old I really want a _risk-free_ means of organising my family's photos and I thought I had it in Shotwell. All the present hassle has ocurred since upgrading to Ubuntu 14.04 and I just wish I could revert to how things were.

I am not an expert user: I started using Shotwell actively for a few days only, and I am not sure whether I will continue. The major advantage is that your photo's are more accessible.
The risky thing is not that your valuable pictures are at risk. Fortunately not. It is only that there is something "proprietary" about these photo managers. You import pictures, organize within the programme. If at some point you cannot anymore use the program, for example because it is not anymore maintained, you a lot of your organization.
On the other hand, the program will have sorted the pictures into folders for you, upon importing.

> 
Am I alone in experiencing problems a) With Shotwell running under 14.04, and, b) With 14.04 telling me, quite often, that it is 'experiencing problems' and inviting me to send an error report? Will post this latter question again on a more appropriate thread.

a) Up to now, I have no problems running Shotwell. It took a very long time importing my pictures and would crash doing so. However, starting it again, it would resume where it left, and now, all my pictures are imported.
b) That will be the error reporting system that is turned on. Here is how you can turn it off: [http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport](http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport)

---

### Post by RayArdia on 2014-06-12
Thanks for your replies. First to Vanadium:- I did as you sugges, but 'swapping' the photo.db for the .bak files made no difference at all when Shotwell was restartedt. Guess if I'm to continue to use Shotwell I'll just have to accept the fact that I'll have to 'retag' all my photos - and there are a lot! BTW the events shown (ie dates) only run from 2004 to 2014, so there's a whole lot missing - I suppose that when I do the full monty restart that MAY correct itself. I'm not holding my breath as advised!

Re comments from open2reason:- I'm still trying to get Digikam to import. It gives me a list of all the dates pertinent to my Pictures folder on the left hand side, and they do seem to be correctly shown from 1949-2014, but I can't seem to get any thumbnails. Screen 'greys-out' while it's importing and I have to Force Quit. Any suggestions?

---

### Post by RayArdia on 2014-06-12
Re comments from open2reason:- I'm still trying to get Digikam to import.
Have now got the files imported, and ALL the photos are there! What I need to do now is to sort out all the 'spurious' .jpeg files. Some, perhaps all, of these seem to have assigned themselves a place in the heirarchy and seem to have tags - how this happened I have no idea.
Not too clear how to search.

---

### Post by RayArdia on 2014-06-12
Re comments from open2reason:- I'm still trying to get Digikam to import.
Have now got the files imported, and ALL the photos are there! What I need to do now is to sort out all the 'spurious' .jpeg files. Some, perhaps all, of these seem to have assigned themselves a place in the heirarchy and seem to have tags - how this happened I have no idea.
Not too clear how to search.

---

### Post by Derek Karpinski on 2014-06-12
I've had this issue before and if I remember correctly, I found a folder in ~/.cache/shotwell (not sure I'm not in front of my pc)  and deleted everything in there. I then opened shotwell and it rebuilt all the thumbnails with the correct date.

---

### Post by open2reason on 2014-06-13
> **RayArdia said:**
> Re comments from open2reason:- I'm still trying to get Digikam to import.
Have now got the files imported, and ALL the photos are there! What I need to do now is to sort out all the 'spurious' .jpeg files. Some, perhaps all, of these seem to have assigned themselves a place in the heirarchy and seem to have tags - how this happened I have no idea.
Not too clear how to search.

Good, things are indeed looking up for you.

You have noticed that tabs and other meta data associated with your images that have been previously written by Shotwell has now been correctly interpreted by DigiKam and you can now form an opinion about the state of your photo collection. If you so wish you can use Digikam to edit and amend the meta data connected with your images. The Digikam documentation might be slightly out of date but never the less well worth a read, try not to get too bogged down in detail.

I'm only too happy to help you if I can:)


Perhaps a browse followed by a SaveAs of  [http://docs.kde.org/development/en/extragear-graphics/digikam/digikam.pdf](http://docs.kde.org/development/en/extragear-graphics/digikam/digikam.pdf) may help.

---

### Post by open2reason on 2014-06-13
Just found more documentation but this time in the form of screen shots at [http://www.digikam.org/node/323](http://www.digikam.org/node/323)  and thought it may be of use to you.

---

### Post by vanadium on 2014-06-14
Digikam is the by far more powerfull counterpart for Shotwell. You may prefer to use it if you don't mind its added complexity, and perhaps the fact that it is a program for the KDE desktop: it thus feels less integrated than Shotwell in a gnome or Unity or other gtk based desktop.

Do not quit to fast when Digikam or OpenShot for the matter greys out. Operations can be lengthy if many pictures are involved. Graying out only means the system feels that the graphical interface is not responsive. In the background, however, the command line tools launched by either Digikam or Shotwell continue to do their work, and eventually, the applications will return to an active state.

I now have decided to let Shotwell write any info to my picture files. This indeed safeguards tags, dates etc. that lso can be used by other programs.

---

### Post by open2reason on 2014-06-14
vanadium,
I suggested it be used as a way by which to check / audit and perhaps amend meta data associated with the OP's photo collection.
One collection of photographs and a selection of tools by which to examine and amend sounds and looks good to me.

---

### Post by open2reason on 2014-06-21
Ray, how are things going with your photo collection?

---

