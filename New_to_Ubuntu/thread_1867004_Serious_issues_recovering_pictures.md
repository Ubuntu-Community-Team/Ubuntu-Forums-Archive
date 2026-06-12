---
title: "Serious issues recovering pictures?"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by P-rench on 2011-10-22
I used scalpel and photorec to try and recover A LOT of photo's that somehow made their way to the trash can and got deleted by accident. After I used the two programs I came up with thousands more photo's then expected. Now heres my problem, I've been looking through these photo's and none of them are photo's I took, their all like these little internet picture thumbnails. For example, there was like 100 thumbnails of different vitamin and herbal supplements, all of which I have looked at, at one time or another on a supplement website I order from. All the filenames start with "f" followed by numbers, example "f308332.jpg" Can someone please explain to me whats going on here? Can I not recover pictures that have been deleted in the trash can or something?

---

### Post by coffeecat on 2011-10-22
Yes, you can recover deleted jpegs, but the problem is that photorec has no way of distinguishing your jpegs from cached and then deleted thumbnails. It simply recovers each and every jpeg (and other types of file) that it can find. Have another look through the recovered jpegs. Are you sure yours are not among them? They will all have seemingly random filenames, so it's a good idea to look at the largest first so as not to be distracted with all the recovered thumbnails. If your photos are not among the recovered jpegs, then it means either that they were not actually deleted or have been overwritten.

If you do manage to find them, you can batch rename them to something more meaningful by using the EXIF metadata. I find gthumb useful for this.

---

### Post by P-rench on 2011-10-22
Thank you for the reply. Currently I have found like 3 photo's...haha. Yea this is gonna be awhile. Is there a way that I can view the pictures and have a setting to only show me pics that are lets say 40kb or higher in size to help avoid the thumbnails like you said?

---

### Post by coffeecat on 2011-10-22
This is what works in Oneiric. I think it will be the same/similar in Natty.

Open a folder with all the jpegs in Nautilus. Keep nautilus to Icon view. I was hoping you could sort by size in list view, but you can't. (:frown:) From the Nautilus menu, View -> Arrange items. Tick both the "By Size" and "Reverse order" lines. That will show the largest files first but not the filesizes which was why I was hoping you could use list view. Anyway, from the Nautilus menu, Edit -> Preferences -> Display tab. Under Icon captions choose "size" from the first drop-down. Now all your photos will be in reverse size order (largest first) with sizes showing. Of course, filesizes will show for every file in every nautilus window now, so you will probably want to reset that last setting when you're finished..

Good luck with that!

---

### Post by P-rench on 2011-10-23
I don't get this, I'm looking through photo's that were recovered right? Well I'm finding a TON of photo's that I never deleted that are showing up as recovered? Now I have doubles of these pictures. Why would it recover photo's that I never deleted?

---

### Post by coffeecat on 2011-10-23
Could it be that you used some software on the photos before you deleted them that created backup copies and then deleted the backup copies? Perhaps a photo-management app?

---

### Post by P-rench on 2011-10-23
That could be a possibility.

---

### Post by P-rench on 2011-10-25
I was able to recover my pictures thankfully. I tried recovering a bunch of other photo's I had deleted about 8 months ago but none of them turned up as far as I can tell. Why is this? I was under the impression that I could recover most data? I also have two other issues I'm facing. 1.) You will see a picture in this post, these literally hundreds of jpg files that look like this that I keep getting in recovery. When I click on them they all have different error's example "Error interpreting JPEG image file (Bogus Huffman table definition)" or "Error interpreting JPEG image file (Bogus marker length)" or "Error interpreting JPEG image file (Unsupported marker type 0x65)" I have no idea what any of these errors mean. Any ideas? 2.) The files I have recovered can't be deleted or moved? I tried deleting everything I recovered that I didn't want and it said I don't have permission, basically I'm guessing this has something to do with root. I also tried moving the recovered files I wanted to keep to a different location and it said I don't have permission to read it? Another root thing? I'm not sure but any help would be greatly appreciated. 

[IMG]http://i167.photobucket.com/albums/u149/spiralnebula42o/jpg_not_working.png[/IMG]

---

### Post by HermanAB on 2011-10-25
$ sudo nautilus
password

Don't worry, be happy...

---

### Post by P-rench on 2011-10-25
Thanks for the reply. That command helped a little. I can move the pictures around to other locations and I was able to delete the unwanted folders of recovered pictures to the trash but when I clicked on trash well in the root mode it wouldn't let me access the trash bin. When I checked the trash bin normally none of what I deleted was there, so yea, I dunno where those deleted folders with pics in them went. Any ideas where they went and how I can delete them if they are in trash? 

I still can't see any of those pics, only difference now in root is that the pic doesn't have the padlock next to it and looks like this ---> [IMG]http://i167.photobucket.com/albums/u149/spiralnebula42o/no_padlock.png[/IMG] When I click on the pic's (and theres hundreds of them like this) it opens and I get an error like this (the errors vary from each photo as I mentioned in my last post above) ---> [IMG]http://i167.photobucket.com/albums/u149/spiralnebula42o/picerror.png[/IMG]  Any ideas?

---

### Post by cryptotheslow on 2011-10-25
> **P-rench said:**
> I don't get this, I'm looking through photo's that were recovered right?  Well I'm finding a TON of photo's that I never deleted that are showing  up as recovered? Now I have doubles of these pictures. Why would it  recover photo's that I never deleted?     

Photorec recovers jpeg (and other) files by looking for what appear to be jpeg file headers so it will find both non-deleted and deleted files (as long as they have not physically been overwritten on the disk).


> **P-rench said:**
> I was able to recover my pictures thankfully. I tried recovering a bunch  of other photo's I had deleted about 8 months ago but none of them  turned up as far as I can tell. Why is this?

If it really has been 8 months since you deleted them it is likely the physical location on the disk where they were has since been overwritten, hence obliterating them.



> **P-rench said:**
> 1.) You will see a picture in this post, these literally hundreds of jpg  files that look like this that I keep getting in recovery. When I click  on them they all have different error's example "Error interpreting  JPEG image file (Bogus Huffman table definition)" or "Error interpreting  JPEG image file (Bogus marker length)" or "Error interpreting JPEG  image file (Unsupported marker type 0x65)" I have no idea what any of  these errors mean. Any ideas?

As above - Photorec does what it can by looking for file headers then recovers subsequent data until it hits an end of file marker. Well it's no doubt a lot more complex than that - but that's the gist of it. If say a section of the disk has been written too in the middle of the deleted file it is recovering it doesn't really know so it blindly recovers it complete with the overwritten bits. Hence you end up with corrupt files. I've never heard of any such thing, but there are probably jpeg repair tools knocking around that you could try.

 > **P-rench said:**
> When I checked the trash bin normally none of what I deleted was there,  so yea, I dunno where those deleted folders with pics in them went. Any  ideas where they went and how I can delete them if they are in trash?

Because you started Nautilus with sudo the deleted files will be in the root accounts recycle bin. Have a look in the /root directory for a .RECYCLER or .TRASH directory (can't remember the name offhand as on my work XP laptop right now!).

Do not use sudo to start graphical applications! Use:
```
gksudo nautilus
``` or
```
gksu nautilus
```
Rather than using a gksudo nautilus you would probably be better off taking ownership of the files.

In this example let's presume your username is "prench" and you have all the recovered jpegs in a directory called "recoveredjpegs" in your home directory.

From a Terminal you would do:
```
sudo chown prench:prench /home/prench/recoveredjpegs/*
```That would change user and group ownership of all files in that directory to be yours.

Be very very very careful using chown - especially with sudo - get it wrong and you can _**seriously**_ hose your system. If in doubt about a chown you are about to commit - _**ask here first.**_ The danger cannot be overstated - it is relatively simple to put your system into a state where it needs a clean re-install with just one wrong chown command.

There... I typed enough now :D

---

### Post by P-rench on 2011-10-25
Awesome reply crypto! Thank you! Answered pretty much all my questions. The only question I have at the moment is, where in the root directory is .recycle or .trash? I'm looking but I don't seem to see it. I will continue to look and update this if I find out before someone posts.

---

### Post by coffeecat on 2011-10-25
> **P-rench said:**
> Awesome reply crypto! Thank you! Answered pretty much all my questions. The only question I have at the moment is, where in the root directory is .recycle or .trash?

An excellent post from cryptotheslow. Thanks cryptotheslow!

The root trash is in /root/.local/share/Trash/. Don't forget that .local is a hidden folder and you will have to ctrl-H to reveal it if you are using a gksu nautilus window.

Tip - if you use a gksu nautilus window to delete root-owned files and you use the delete key, they are simply sent to root's trash. You need to use shift-delete to do an immediate hard delete.

---

### Post by cryptotheslow on 2011-10-25
No worries. Lord knows I've received my fair share of help from these forums so good to help out in some small way.

And thanks for the extra info on the root trash location, I couldn't remember off-hand so took my best guess :D

---

### Post by ArgusVision on 2011-10-25
@ P-wrench
 Just a reminder, if cryptotheslow resolved everything for you please mark the thread [solved]

---

### Post by P-rench on 2011-10-26
Everything looks good but I have one last question. When I go to /root/.local/share/Trash/ I can see all the deleted files and folders now, but, I can't seem to figure out how to delete them permanently?

---

### Post by coffeecat on 2011-10-26
If you use a gksu nautilus file browser window, you *should* be able to delete everything in /root/.local/share/Trash/ with shift+delete. Let us know if that doesn't work.

---

### Post by P-rench on 2011-10-26
Awesome! That did it! Thanks coffeecat and thanks so much for everyones help! I learned A LOT! :D

---

