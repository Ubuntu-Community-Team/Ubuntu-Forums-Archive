---
title: "FLV video file thumbnail preview"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by jmlaniel on 2008-11-08
I am currently running a fresh install of hardy heron and I just noticed that Nautilus is generating thumbnails preview for all my video files except my flash file (*.flv).

I tried to find a solution, but I got nothing that worked. Anybody knows how to fix that? It's very annoying...

Thanks.

---

### Post by Zzl1xndd on 2008-11-08
Not sure why or if its even the same problem, but on my machine it will only show thumb nails after I have played the .flv

---

### Post by jmlaniel on 2008-11-08
In my case, there is no thumbnail whether I play or not...

---

### Post by jmlaniel on 2008-11-09
Nobody else has any suggestions?

---

### Post by jmlaniel on 2008-11-15
I am suprised to see that I am the only one with the problem...

Maybe the problem is that I don't have all the necessary codecs installed. Any suggestions concerning this?

---

### Post by InfectedWithDrew on 2008-11-15
Well, do the files play?

---

### Post by jmlaniel on 2008-11-15
Yes, they all play. The only problem is that I have to open them to see what is inside. It is really frustrating especially with flv downloaded from youtube where the files don't have names that identify them very well.

I also notice that for some files, I get a thumbnail for a flv and for others, I don't. The problem doesn't seem to be entirely reproductible.

---

### Post by SamNSane on 2008-11-15
> **jmlaniel said:**
> Yes, they all play. The only problem is that I have to open them to see what is inside. It is really frustrating especially with flv downloaded from youtube where the files don't have names that identify them very well.

I also notice that for some files, I get a thumbnail for a flv and for others, I don't. The problem doesn't seem to be entirely reproductible.

Now that's beginning to sound a little different. Take a look at the folder where you have these files in List mode. Are the ones that aren't getting thumbnails generated the larger files? Say files larger than 10 MB?

IIRC, the default setting for thumbnail generation in nautilus is to NOT generate a thumbnail for files > 10 MB. You can open nautilus, go to the Edit menu, choose Preferences, then select the Preview tab on the Preferences dialog. There's a setting there that will let you increase the default upper size limit for thumbnail generation for "other previewable files". If the files that aren't thumbnailed are bigger than the limit that's set there, you can increase the limit.

Bear in mind that this limit is set to prevent the system from burning resources to preview really big files. If you had a large folder filled with 4 gigabyte files (possible in this day and age) the act of previewing or thumbnailing those files might make the system pretty busy for a while.

---

### Post by jmlaniel on 2008-11-17
Thanks for the suggestion, but I already checked the file size option for generating the thumbnail. It doesn't make any difference. I have for example two 60 Mb flv file: one with a thumbnail and the other without one. I still have no idea why Nautilus treats the files differently...

It's why I am now suspecting the codecs... or maybe the installed video player ? (I am using VLC, SMPLayer, Totem and mplayer).

---

### Post by spiderbatdad on 2008-11-17
You are not using "compact view" under the "views" "default view" menu...are you? You should have "icon view" for the effect you want.

---

### Post by jmlaniel on 2008-11-17
No, I'm using the "View as icon" (but it makes no difference since you can see small thumbnails in "View as a list").

---

### Post by spiderbatdad on 2008-11-17
hmmm. I have thumbnails set at 10mb, yet I have .avi vids over 1.5GB each, and they have thumbnails.

---

### Post by SamNSane on 2008-11-17
> **jmlaniel said:**
> Thanks for the suggestion, but I already checked the file size option for generating the thumbnail. It doesn't make any difference. I have for example two 60 Mb flv file: one with a thumbnail and the other without one. I still have no idea why Nautilus treats the files differently...

It's why I am now suspecting the codecs... or maybe the installed video player ? (I am using VLC, SMPLayer, Totem and mplayer).

Shucks. That is perplexing. I'm going to play around with nautilus to see if I can find a way to get this to happen. It does seem like a defect in a codec, or perhaps in a player. Might be worthy of a bug report.

---

### Post by jmlaniel on 2008-11-18
I just found the solution: it seems that the package totem-gstreamer was not installed. It is now installed and I am getting all my thumbnails. Thanks for all the suggestions.

I found the solution here:

[http://linuxmint.com/forum/viewtopic.php?f=90&t=16361&p=99756&hilit=flv#p99756]("http://linuxmint.com/forum/viewtopic.php?f=90&t=16361&p=99756&hilit=flv#p99756")

---

### Post by Joe_Bishop on 2008-11-30
> **jmlaniel said:**
> I just found the solution: it seems that the package totem-gstreamer was not installed. It is now installed and I am getting all my thumbnails. Thanks for all the suggestions.

I found the solution here:

[http://linuxmint.com/forum/viewtopic.php?f=90&t=16361&p=99756&hilit=flv#p99756]("http://linuxmint.com/forum/viewtopic.php?f=90&t=16361&p=99756&hilit=flv#p99756")
This solution didn't work for me (totem-gstreamer had been installed already), but solution from 
[http://forums.fedoraforum.org/showthread.php?t=204321](http://forums.fedoraforum.org/showthread.php?t=204321) worked OK.

Just remove ~/.thumbnails/fail/ content: rm -r ~/.thumbnails/fail/*

---

