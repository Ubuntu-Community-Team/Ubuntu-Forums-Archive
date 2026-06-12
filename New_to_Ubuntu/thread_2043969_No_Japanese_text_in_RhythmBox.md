---
title: "No Japanese text in RhythmBox"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by StardustLuna on 2012-08-17
Like the title says. I have some Japanese music on here, and the titles are all gobbledy-gook.  I searched this issue and have done all the solutions I found, installing several packages that support the Japanese language. 

However, from what I've seen, I think my problem is the tag coding? Or something. I saw a lot of talk about UTC-8 or something like that and using EasyTag. Though I have absolutely no idea what that is or what the people were referring to.

---

### Post by Jakin on 2012-08-17
If the tags are coded correctly (unicode tags) then there ought be no issue.

Unfortunatly is sounds like thats the issue, some players will look up the tags for you. Amarok and Banshee come to mind..

If you want to go the easy-tag/ kid3 route- once you have browsed to the audio file, there will be options to look tags up online, or it will scan and apply tags based on the folder name and filename, and auto apply unicode tags.

Give any of those a shot :)

---

### Post by ageofsteam on 2012-08-17
I have a lot of Japanese music in my library, and I'm not having that problem...  Is it possible that the metadata was messed up somehow?  I've seen webpages, etc. where intended-to-be-Japanese text becomes a lot of squares and apostrophes, etc...  And even the source coding got messed-up.  I'm not sure why it happens...

I think my Rhythmbox supported unicode characters right out of the box.  I'm typing on a new comp now, and I just loaded my library a few days ago...  The titles- many loaded with kanji- immediately displayed just fine.

It seems like the problem might be with the songs themselves...

Oh!  Sometimes there are several id3 tags, and Rhythmbox will sometimes show the wrong one.  If you can download Mozilla Songbird, it can edit the tags.  (It can run from the folder you dump it in- it's not hard to install.  Just unzip and go.  It's one of the few programs I've found that can fix weird id3s.)  It might not be able to *recover* the lost tags, but it can at least fix the file info for the future.

BTW are Japanese websites showing the right characters for you?

---

### Post by StardustLuna on 2012-08-29
I'll definitely mess around with easy-tag or songbird when I have the time. 

Anyway, I put some new music on my comp, and the kanji comes up correctly, so I'm guessing that it's the songs individual tags that are screwy.

And yes, Japanese texts online show up correctly. 

I'll give you both an update if I finally fix it!

---

