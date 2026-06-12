---
title: "[SOLVED] remove embedded album art..."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-20
when I was using windows a virus I managed to download added embedded album art to all my mp3 files and so every time I play them I can some random album cover, is there a way to remove it in ubuntu?

---

### Post by falcon61102 on 2008-08-20
If the album art is on your windows system, then yeah, it should be a snap to remove it.  If you navigate to your music folder in Ubuntu, you should see a folder named Album Art.  In that folder should be all the files used for your album art collection.  

If you don't have one of those folders, it may be that the art is stored in the individual albums.  If that be the case, then check a couple of the folders to comfirm that and see what type of file is being used.  Then run a search on your Music folder looking for that file type.  Once the list is generated you should be able to delete all the pic files without a problem.

If the music is on your Ubuntu side, you can go about that in the same way, but you may also have to check the settings on you music player.  If your music player is set to automatically download the album art, then you deleting it is only going to cause your player to download it again.

Btw... your signature is funny.

---

### Post by kamitsukai on 2008-08-20
> **falcon61102 said:**
> 
Btw... your signature is funny.

LOl thanks:)

---

### Post by Esthellin on 2009-09-29
What about for those people who actualy have EMBEDDED album art in their music files? They should change the thread name...misleading....
I have quite alot of music, and going through each individually to remove album art is a pain.

I need a batch method - to delete all album art from a selection of files if they have embedded album art.

EasyTag can remove album art but only one at a time. Gtkpod somehow didn't even delete the album art. (I clicked the button marked "Add folder", put in my music, selectin all the files, clicked the checkbox marked "apply to all tracks simultaneously", then pressed the button "Remove album art", applied the changes, then saved the changes in the main screen toolbar.)
Surely this would have done it, but loading the music into vlc adds the so-called "deleted" album art into its cache again.

---

### Post by psychoelf on 2010-09-10
I know this is an old thread, but I agree with the above, the Title is misleading.

This SOLVED the embedded image problem for me.

I had a lot of messed up album art from years of itunes, windows and other media players.

I finally found out how to get rid of all the album artwork.  Now I've started all over doing it right.

eyeD3 is in synaptics.  
Install, navigate to your music folder in the terminal and run```
eyeD3 --remove-images * *.mp3
```

This removed all the images.  Yay!

P.S.  I also used did a search for *.jpg in my music folder and *.ini just in case and deleted all.

---

### Post by krivine on 2010-09-15
> **psychoelf said:**
> I know this is an old thread, but I agree with the above, the Title is misleading.

This SOLVED the embedded image problem for me.

I had a lot of messed up album art from years of itunes, windows and other media players.

I finally found out how to get rid of all the album artwork.  Now I've started all over doing it right.

eyeD3 is in synaptics.  
Install, navigate to your music folder in the terminal and run```
eyeD3 --remove-images * *.mp3
```

This removed all the images.  Yay!

P.S.  I also used did a search for *.jpg in my music folder and *.ini just in case and deleted all.
Thank you! I will give that a try this evening.

---

### Post by Jack Brown on 2010-11-10
> **psychoelf said:**
> I know this is an old thread, but I agree with the above, the Title is misleading.

This SOLVED the embedded image problem for me.

I had a lot of messed up album art from years of itunes, windows and other media players.

I finally found out how to get rid of all the album artwork.  Now I've started all over doing it right.

eyeD3 is in synaptics.  
Install, navigate to your music folder in the terminal and run```
eyeD3 --remove-images * *.mp3
```This removed all the images.  Yay!

P.S.  I also used did a search for *.jpg in my music folder and *.ini just in case and deleted all.

Nice solution psychoelf simple and worked as promised.  did leave jpg album art behind, but removed embedded ones not visible in the folder.

---

### Post by clockworktri on 2011-01-01
Thanks for this suggestion! I want to delete all my embedded album art, and this got a lot of it. But it doesn't seem to search in every folder in a directory. Is there a way to make sure it scans every file in every folder in my music directory, or do I have to go through every sub folder manually?

---

### Post by psychoelf on 2011-01-07
I'd have to check the manual for eyeD3 but I believe the first "*" is for all sub directories within a main directory.  I just went to my "Music" folder in terminal and ran it and it covered all sub dirs.

---

### Post by tom957 on 2011-03-19
eyeD3 does the job right. Thanks for the heads-up!

---

### Post by FerroPower on 2012-02-16
Superb even works in arch

---

### Post by psychoelf on 2012-02-16
Glad it works still!

---

