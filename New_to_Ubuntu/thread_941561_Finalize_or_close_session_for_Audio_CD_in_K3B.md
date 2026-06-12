---
title: "Finalize or close session for Audio CD in K3B"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by stot on 2008-10-08
Last week I tried to make an audio CD using K3B in Kubuntu on my Shuttle XPC DVD writer.  After the computer wrote the files to the disc, it did not finalize.  So I tried it again, and I got another CD that will not play.  When I view the disc, I see 17 .cda files (i.e. Track02.cda) as if it was an audio CD.  However, neither Kubuntu nor Windows XP nor my car CD player will play the CD.  Is there any way to finalize the disc or close the session using K3B?

---

### Post by indytim on 2008-10-08
Are you certain that you have the k3bmp3 library installed (I'm Windows bound at the moment so I can't give you the exact library name)?

IndyTim

---

### Post by stot on 2008-10-09
IndyTim,

Thanks for your response.  The audio files I used to make the CD are .wav files.  Should I still need the k3bmp3 library?

---

### Post by indytim on 2008-10-09
I am reasonably sure that k3b will not be able to handle .wav files to create audio CD.  I have not had an occasion to do any work in .wav files.  One thought, you might want to checkout soundconverter (it's in the repro's). I know it can convert from ogg->mp3.  Might also be able to convert from wav -> mp3.  

Good Luck,

IndyTim

---

### Post by SuperSonic4 on 2008-10-09
> **indytim said:**
> I am reasonably sure that k3b will not be able to handle .wav files to create audio CD.  I have not had an occasion to do any work in .wav files.  One thought, you might want to checkout soundconverter (it's in the repro's). I know it can convert from ogg->mp3.  Might also be able to convert from wav -> mp3.  

Good Luck,

IndyTim

It can do anything if you have all the codecs installed.

---

### Post by stot on 2008-10-09
Should I need to add codecs to default Kubuntu K3B to simply burn an audio CD from .wav files?

It seemed to add the files just fine.  However, it didn't close the session.

Why didn't it give me any errors?  Instead, it just poppped the CD out of the computer.

---

### Post by SuperSonic4 on 2008-10-09
Have you checked the cd to see if it worked? I'm currently testing on an mp3 audio CD in mandriva

edit: no problem at all. K3B didn't give a pop up notice but it did say success in the window. I'm just testing by reimporting and now I have another coaster xD

---

### Post by indytim on 2008-10-09
As was suggested earlier, looks like you're missing codec(s).  I just downloaded a .wav file and used soundconverter to convert it to a mp3.  I also created a new audio cd project in k3b and it allowed me to import the .wav file directly into k3b for an audio cd.

For codec install help, suggest you meander over to the multimedia board and check out the stickies for specifics on installing the necessary codecs to get the av stuff running properly.

IndyTim

---

### Post by weegreenblobbie on 2012-02-21
Please read the original post.  An audio CD is a disc format that contains PCM WAV data.  No codecs necessary.

CDs that contain mp3s or ogg files are DATA CDs, not Audio CDs.

OP wants to know how to close or finalize the session so it is playable by CD players.

---

### Post by oldos2er on 2012-02-21
Closed, necromancy.

---

