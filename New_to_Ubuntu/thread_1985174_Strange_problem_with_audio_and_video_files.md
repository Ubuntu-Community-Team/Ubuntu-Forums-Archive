---
title: "Strange problem with audio and video files"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by asensio on 2012-05-23
This is such a strange thing that i don't even know where to post it...

Well, I have a music colection in a folder. I have videos in other folders.

Today I was going to listen to some music. When I opened the files, I noticed that some of the songs where blended, mixed, glued with short video clips (not even the full vídeo, just a clip) from files that I have in other folders... The name of the file didn't change, the extention of the file didn't change, still .mp3

I used gloobus-preview well..., to preview. And the result is: when I hit space key I start to watch seconds of some vídeo and then some other song starts playing...

Audacious and Rhythmbox can't play the file...

It's not in every song of an album/folder, not even in every album of my music collection, but I already deleted 3 or 4 albuns before I dig in to the problem. I don't want to delete anymore.

I don't know how to explain this in a better way, so I made a screencast and upload it to my dropbox [**[COLOR="Red"]here[/COLOR]**]("http://dl.dropbox.com/u/1384316/vid/strange.mp4")...

I don't even believe that there's a solucion to this...

WHAT THE HELL HAPPENED? :mad: ](*,)
**ASENSIO**

---

### Post by asensio on 2012-05-23
Some more details about this: just before I noticed this error I installed the Ubuntu Kernel 3.4.0 from the quantal PPA, just like [**this**]("http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html"), Banshee, where I had to specify my video and audio files, and cover-thumbailer...

Could this be a kernel error? Could one of this apps/software have messed with my music colection?
Cheers
**ASENSIO**

---

### Post by choppyfireballs on 2012-05-23
> **asensio said:**
> Some more details about this: just before I noticed this error I installed the Ubuntu Kernel 3.4.0 from the quantal PPA, just like [**this**]("http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html"), Banshee, where I had to specify my video and audio files, and cover-thumbailer...

Could this be a kernel error? Could one of this apps/software have messed with my music colection?
Cheers
**ASENSIO**

I almost wonder if installing or updating the kernel would have messed with some of the bits, how or if this is even possible I don't know. But if the kernel had been doing anything with partitions i guess it could theoretically make sense.

---

### Post by asensio on 2012-05-23
Thanks for your reply choppyfireballs...

About the kernel I just updated it, and rebooted. I think it didn't touch any partitions.
 
I was thinking that maybe when I was configuring Banshee, pointing the location of my media files, somehow it messed up my files. I didn't sync the entire colection just some albums and videos, Banshee freezed so I killed it...

I have no idea...
Well, seems I need to rip some CD... again

---

### Post by juustahiker on 2012-05-23
I have never encountered anything like this but could it be that some how placed pointers in your audio and video files to other files? do you have the program back in time if you do just roll back your system until before you reconfigured banshee. if you don't I strongly recommend it, it saved me countless times.

---

### Post by asensio on 2012-05-23
thanks juustahiker

I don't have a clue, really. There's not a real damage here, but I think this is just too weird, so I posted it.

I'm going to check Back In Time, never used it... but it seems handy.

Cheers and thanks

---

### Post by choppyfireballs on 2012-05-29
> **juustahiker said:**
> I have never encountered anything like this but could it be that some how placed pointers in your audio and video files to other files? do you have the program back in time if you do just roll back your system until before you reconfigured banshee. if you don't I strongly recommend it, it saved me countless times.

This is what I was thinking happened, logically it makes sense, but as to how it happened i don't know, i've never seen it before.

---

