---
title: "Files from Android phone lost when using Ubuntu"
date: 2016-01-28
forum: New to Ubuntu
---

### Post by renegadomota on 2016-01-28
[COLOR=#111111][FONT=Ubuntu]I had my phone connected to the pc, installed with Ubuntu, with a usb cable. Moved 400+ photos from the photos directory of my phone to a new folder i created inside that main folder - this was just so i could have photos separate by the location they were taken. After Ubuntu finished moving the files, with no errors, i unplugged my phone from the pc and all photos, music, videos were gone - not just the photos i moved. Can anyone help? BTW, i'm an IT guy but don't really know nothing about Ubuntu or other Linux distros. This was my 1st day using Ubuntu and can't say it was a pleasant experience at all.[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-01-28
> [COLOR=#111111][FONT=Ubuntu]to a new folder i created inside that main folder [/FONT][/COLOR]

What main folder? We can create folders on the Desktop. We can create folders inside the 5 default folders (including Pictures & Videos). We can copy & paste or cut & paste files into and out of folders. If we use cut, then the original files will be deleted from their original locations.

These folders and files will show up in File Manager. We can also create folders under what in Linux is called the root directory. Folders and files in the root directory will not show up in File Manager unless we open the location. In some versions of File Manager we click on File System. On other versions we click on Computer. In the next version of Ubuntu to be released we will need to click on Other Locations.

Not knowing which version of Ubuntu you are using I can only speak in general terms.

---

### Post by Bucky Ball on 2016-01-28
If you mean you moved them to a different location on the phone, are you sure you moved them to a location the phone recognises as a storage area for pics?

---

### Post by renegadomota on 2016-01-28
I was using Ubuntu 14.04.3.
By "main folder" i'm referring to the photo's main folder on my android phone - DCIM\Camera.
I created a new folder there - so: DCIM\Camera\NewFolder and changed those photos from DCIM\Camera to DCIM\Camera\NewFolder.
All within the phone. I didn't save anything to Ubuntu; but i did all that while using Ubuntu.

> **Bucky Ball said:**
> If you mean you moved them to a different location on the phone, are you sure you moved them to a location the phone recognises as a storage area for pics?

It should still recognize the photos since the files were still within the folder. But even if it didn't, i can no longer see the files. Not even connecting it again to Ubuntu.

---

### Post by Melnik_Hoogland on 2016-01-29
Did your folder begin with a dot? If so, try pressing Control+H in the file manager, then, on the same file manager window, looking in DCIM\Camera.  Folders beginning with dots are hidden folders in Linux (control+H reveals hidden folders in the file manager). If this reveals your folder, you should move the files out or rename it, since (although I'm not an android expert) I don't think android will show you your pictures as long as the folder starts with a dot.

---

### Post by mastablasta on 2016-01-29
moving files on same media is usually done in an instant.

---

### Post by renegadomota on 2016-01-29
No, no folders had dots in them. At this point i lost all hope on getting the files back. But thanks for the tip, it's worth trying it out.

> **mastablasta said:**
> moving files on same media is usually done in an instant.

Yes, but not when you're moving +400 files with +/- 5MB each.

---

### Post by tea for one on 2016-01-29
Out of curiosity, why did you not use your phone's file manager to move files from one area to another within your phone?

Secondly, you do have a back up of 400+ files?

---

### Post by howefield on 2016-01-29
> **renegadomota said:**
> Yes, but not when you're moving +400 files with +/- 5MB each.

Suppose you have checked the data storage settings on the phone, that amount of space is fairly significant on a phone ? Might give you an idea of whether the pictures are in fact, still there.

---

### Post by renegadomota on 2016-01-29
> **tea for one said:**
> Out of curiosity, why did you not use your phone's file manager to move files from one area to another within your phone?

Secondly, you do have a back up of 400+ files?

Fair question. And the answer is because i was testing out Ubuntu for the 1st time and since the laptop was in from of me and the phone was already charging trough it, i decided to do it using the pc.
Unfortunately i didn't had any backup of the files because all those photos were taken during a vacation.

I did check storage data. According to it, they're not there. Unless they are stored somewhere else in a different format/coding.

---

### Post by mastablasta on 2016-01-29
> **renegadomota said:**
> 
Yes, but not when you're moving +400 files with +/- 5MB each.

moving, not copying would still be almost instant. as nothing actually get's moved on the media (i.e. no bits move arround hard disk hard disk) it just get's a different address.

if it took quite a while for the task to complete you actually moved them somewhere else (to another media).

---

### Post by renegadomota on 2016-01-29
Moving files is a simple task. I'm not saying i didn't do anything wrong, but if i did i don't know what it was. I opened the file explorer on Ubuntu, went to my phone drive, photo's folder and inside that folder i created a new one and moved the files there.
Even after finishing moving the files, i could see them on the new folder. However, i wasn't able to open them on Ubuntu so i tried on the phone itself (i could see the files on the phone after unplugging it from the pc). Also couldn't open. Once i connected the phone to the pc again, the files were gone.

---

### Post by Bucky Ball on 2016-01-29
When you unplug the phone from Ubuntu, can you see the files on the phone? Forget about trying to see them with Ubuntu for the moment. You just want to know they are still on the phone so that is a distraction. Ubuntu's telling you the files aren't there but what's the phone showing???

---

### Post by Melnik_Hoogland on 2016-01-29
That is odd. Did the move take longer than a few seconds? If so, you probably moved the pictures to another drive. The only other thing I can think of that could cause this would be that your SD card is corrupted.

---

### Post by renegadomota on 2016-01-29
> **Bucky Ball said:**
> When you unplug the phone from Ubuntu, can you see the files on the phone? Forget about trying to see them with Ubuntu for the moment. You just want to know they are still on the phone so that is a distraction. Ubuntu's telling you the files aren't there but what's the phone showing???
At first  yes, i could see the files on the phone. But i couldn't open any of them. So plugged it back to the pc to try to understand why i couldn't open them on the phone. After that all the files were gone and i couldn't see them neither on Ubuntu or on the phone.

> **Melnik_Hoogland said:**
> That is odd. Did the move take longer than a few seconds? If so, you probably moved the pictures to another drive. The only other thing I can think of that could cause this would be that your SD card is corrupted.
It did take more than 5min. But because there were a lot of files, i didn't thought much of it.
My phone only has internal storage; no sd card slot.

---

### Post by Bucky Ball on 2016-01-29
Do you remember any of the file names? If so, do a file search on the computer with Catfish or your app of choice and see if it pops up. Also check the trash on both devices. 

Shot in the dark.

---

### Post by renegadomota on 2016-01-29
The file names are the standard "IMG_date***" I did check the trash on both devices: both were empty.
Is catfish already installed on Ubuntu?

---

### Post by Bucky Ball on 2016-01-29
There may be something else installed for file searches on Ubuntu. Catfish is what I use, though. It's in the repos.

---

### Post by renegadomota on 2016-01-29
Oh ok. I'll do a search later today. Thanks for the help.

Tanks for the tips but none of them solved it. Couldn't find anything using the file explorer or looking into the hidden folders.
Unfortunately i guess all the photos are really gone.

---

### Post by philinux on 2016-02-01
> **renegadomota said:**
> Tanks for the tips but none of them solved it. Couldn't find anything using the file explorer or looking into the hidden folders.
Unfortunately i guess all the photos are really gone.

Sorry to hear that. For the future I would use Onedrive or similar. Every time I take a photo on my G3 phone it gets backed up to Onedrive automatically.

---

### Post by leunam12 on 2016-02-01
I don't know how the files can be lost like that, unless you tried to cut and paste a opposes to drag and drop.

---

### Post by renegadomota on 2016-02-01
> **philinux said:**
> Sorry to hear that. For the future I would use Onedrive or similar. Every time I take a photo on my G3 phone it gets backed up to Onedrive automatically.
I don't like using cloud services for my personal pics. Next time i just wont change directories until i backup my photos to an external hd. That's where i store all my pics.

> **leunam12 said:**
> I don't know how the files can be lost like that, unless you tried to cut and paste a opposes to drag and drop.
That's what i did. Ctlr+X, Ctlr+V.
Lesson learned.

---

### Post by mastablasta on 2016-02-01
nothing is gone until you overwrite it. even delete function basically only says - "hey, this disk/media area is free to use".

formatting can overwrite portions, but generally and unless you format into different file system, things can still be recovered. even if you format into different file system, the files can sometimes be recovered I think. but it take a bit more skill and patience.

so at this point it might be wise to stop using the phone and record new data (if files are really deleted) and search for some file recovery app. 

this is still a very strange and unusual issue. and if it all checks out it should definitely be reported on Launchpad.

---

### Post by renegadomota on 2016-02-01
> **mastablasta said:**
> nothing is gone until you overwrite it. even delete function basically only says - "hey, this disk/media area is free to use".

formatting can overwrite portions, but generally and unless you format into different file system, things can still be recovered. even if you format into different file system, the files can sometimes be recovered I think. but it take a bit more skill and patience.

so at this point it might be wise to stop using the phone and record new data (if files are really deleted) and search for some file recovery app. 

this is still a very strange and unusual issue. and if it all checks out it should definitely be reported on Launchpad.
I was thinking the same, that's why i opened this thread. But i already tried to recover the files using several apps. They do find loads of pics files but none of them are the 400 ones i moved.
I've been trying not to create new user data on the phone just in case i manage to recover the files, but at this point it seems that it's not going to happen.

---

### Post by philinux on 2016-02-01
> **renegadomota said:**
> I was thinking the same, that's why i opened this thread. But i already tried to recover the files using several apps. They do find loads of pics files but none of them are the 400 ones i moved.
I've been trying not to create new user data on the phone just in case i manage to recover the files, but at this point it seems that it's not going to happen.

Have you tried photorec which is part of the Testdisk suite?

---

### Post by renegadomota on 2016-02-01
> **philinux said:**
> Have you tried photorec which is part of the Testdisk suite?
That's an Ubuntu app, correct? On Ubuntu i only did a search by file name and looked up hidden folders.
Since i moved the files from the phone to the phone directly, if the files still exist they should be on the phone somewhere.

---

