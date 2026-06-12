---
title: "AmaroK help?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by CorwinShiu on 2008-04-22
I can't seem to get my music to play on amaroK. When I click play, it just runs through all the files and says 'playlist finished' when it runs through all of them. I know the files work, it works when I open them with VLC. Thanks.

---

### Post by Xiong Chiamiov on 2008-04-22
Ah yes, I've had the problem many a time.  Now, if I can just remember what it was...

Are you dragging the files in directly from the file manager, or adding them from your collection?  If the latter, try tools -> update collection.

---

### Post by dmub82 on 2008-04-22
Sounds like it could be a codec problem; doesn't VLC use its own set of codecs, so they might work there but not in Amarok?

---

### Post by Xiong Chiamiov on 2008-04-22
> **dmub82 said:**
> Sounds like it could be a codec problem; doesn't VLC use its own set of codecs, so they might work there but not in Amarok?
Yessir, that's true.  Still, amaroK doesn't skip files if it can't play them, but rather gives you an error about the media not being loadable or some such.  I'm pretty sure that it's when the files don't exist that that happens.

Oh, and to check that, you can also go to tools -> playlist -> remove dead and duplicate entries, or something like that ([not on my normal box right now]("http://ubuntuforums.org/showthread.php?t=763265")).

---

### Post by CorwinShiu on 2008-04-22
I can't seem to find the 'update collections'. I selected my music file from the set-up window and all my music is there but doesn't play. What other things can I try? I also can't seem to access the help box.

---

### Post by ace007 on 2008-04-22
If when you add the songs to the queue they are greyed out, it means the file has been moved.  Under one of the menus up top there is a rescan collection option

---

### Post by CorwinShiu on 2008-04-22
No, the files are dark and reloading the files doesn't seem to do anything...  The files just skip when I press play. Arg, this is frustrating. I'm not sure if this would change anything, but I use Ubuntu 6.06. 


Does anyone have an alternative player they would suggest that is similar to amaroK?

---

### Post by redbob on 2008-04-22
Several reasons make Amarok pass by your files without playing them. See:
1) if your default sound driver isn't Alsa, it may conflict with anyelse app that makes sound;
2) Even if your drive may be Alsa, sometimes Firefox, even Virtualbox may mute Amarok sound, today morning my Amarok turned like you described. When I was resolut to reset my computer, I resolved to shutdowm my Firefox and - voila- Amarok worked!
3) To determine if your files isn't broken, just execute the option Playlist>Remove Duplicate & Dead entries.

---

### Post by Xiong Chiamiov on 2008-04-22
Ah yes, that's right.  I used to have terrible problems with ALSA, and ended up building it from source.  For some reason I could only get one app to output sound at a time, so if I paused amarok and played something in VLC, amarok would skip like that until I restarted it.  Are you using the latest version of ALSA?

---

### Post by redbob on 2008-04-22
I'm using 1.4.7. Amarok's default drive is Alsa.
My default sound drive is Autodetected in Sound Preferences. 
Verify if in your sound preferences the option Enable ESD Software Mix is checked. It is the guy that allows you use more than one app to make sound, besides Audacity doesn't share sound. With Helix, Totem or MPlayer I can hear Amarok very well.:guitar:

---

### Post by Xiong Chiamiov on 2008-04-22
> **redbob said:**
> I'm using 1.4.7. Amarok's default drive is Alsa.
My default sound drive is Autodetected in Sound Preferences. 
Verify if in your sound preferences the option Enable ESD Software Mix is checked. It is the guy that allows you use more than one app to make sound, besides Audacity doesn't share sound. With Helix, Totem or MPlayer I can hear Amarok very well.:guitar:
Sorry, that question was aimed towards the OP; I should've been more clear.

Thankfully, my sound works great now.  Besides, I'm using Kubuntu (well, trying to fix it atm), so I can never follow GUI instructions from anyone, which can be a pain sometimes.

---

### Post by CorwinShiu on 2008-04-23
I'm using 1.0.10 for Alsa, but I'm not sure if it is my default sound driver.
The files seem fine...

---

### Post by redbob on 2008-04-23
Xiong, I just realized that the question came from you after have posting my answer... but don't worry, it was suitable. :)

---

