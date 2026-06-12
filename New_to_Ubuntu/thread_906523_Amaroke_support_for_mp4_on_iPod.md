---
title: "Amaroke support for mp4 on iPod"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Ralph L on 2008-08-31
I am trying to switch my iPod support from Windows XP/Vista to Amarok under Kubuntu Hardy.  All my Windows files and all my iPod files (on the iPod) are in mp4 (aac) format. I would like to stick with that format if possible.  Is there any way to do that with Amarok (or any other kubuntu/ubuntu program)?  I need to be able to add albums (CDs) to the iPod in mp4 format as well as maintain and play my music collection on hard disk.

In addition, I can't even get to first base with Amarok.  How do I create a music collection on my hard disk from CDs?  I tried copying to an image file with k3b (took only a couple minutes), but Amarok didn't recognize it as part of the collection.  (I used the Collection>Configure Amarok (button) to set the folders where Amarok looks for the collection.)   I then used Dolphin to just copy the cd to the Music folder.  This copy took at least an hour, and although Amarok recognized it as part of the Collection, when I tried to transfer it to the iPod I got a message saying "12 tracks not playable on media device"

Any help appreciated.

Ralph

---

### Post by lbriner on 2008-08-31
I can't promise that Amarok will work with the ipod (someone else know?) and I did have some problems synching it with my Archos MP4 player even though it appears as a hard disk! I can however help you with the ripping bit.
Use KAudioCreator to rip your CDs onto your hard disk. I have a guide about ripping to m4a on [http://lukieb.blogspot.com/2007/12/ripping-m4a-in-kaudiocreator.html](http://lukieb.blogspot.com/2007/12/ripping-m4a-in-kaudiocreator.html)

Once you have ripped the music you have two choices in Amarok. The first is to set it up so that it monitors certain folders. Settings - COnfigure Amarok - Collection  Tick the folders you need and choose if you want it to constantly check the folders or not. The other way is to play the music from the hard disk and I think it automatically adds it to your collection. If at any point you change your music, you can choose Tools - Update Collection (or rescan, not sure what they do but I think one deletes the info and re-reads it, the other just checks it).

Last time I looked, although KAudioCreator can add track info to the m4a file, Amarok can not edit this info like it can with wmas and mp3s for reasons I do not know. Make sure you rip correctly and you won't need to edit it.

Good luck synching with the ipod, I'm sure if you search the web you'll find something useful!

---

