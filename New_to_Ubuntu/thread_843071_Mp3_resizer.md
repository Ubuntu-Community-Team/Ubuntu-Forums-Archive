---
title: "Mp3 resizer"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by monolux on 2008-06-27
Does anyone know of a resizer program for mp3 in linux?

---

### Post by ChameleonDave on 2008-06-27
> **monolux said:**
> Does anyone know of a resizer program for mp3 in linux?

One doesn't normally talk of resizing MP3s.  Are you talking about an audio editing program, allowing you to cut short the length of the recording, amongst other tasks?  Then you need Audacity.  It is available in the software repositories.  Just search for it in Synaptic.  Alternatively, type "sudo apt-get install audacity" on the command line.  You may have the program already.

Do you mean re-encoding an MP3 at a lower quality level in order to make the filesize smaller but keep the length of the recording the same?  You can do that in Audacity too, or there are simpler tools that will also do the job.

Let's assume you have a music file called GreatMusic-bigfile.mp3 on your desktop.  
Go to the command line:

```

cd ~/Desktop
sudo apt-get install lame sox
sox GreatMusic-bigfile.mp3 GreatMusic-hugefile.wav
lame -V7 GreatMusic-hugefile.wav GreatMusic-smallfile.mp3
ls -lh GreatMusic*

```

Enter each command on its own line.

---

### Post by monolux on 2008-06-27
> **ChameleonDave said:**
> One doesn't normally talk of resizing MP3s.  Are you talking about an audio editing program, allowing you to cut short the length of the recording, amongst other tasks?  Then you need Audacity.  It is available in the software repositories.  Just search for it in Synaptic.  Alternatively, type "sudo apt-get install audacity" on the command line.  You may have the program already.

Do you mean re-encoding an MP3 at a lower quality level in order to make the filesize smaller but keep the length of the recording the same?  You can do that in Audacity too, or there are simpler tools that will also do the job.

The second option....I need smaller files but something simpler then audacity. Please help!!

---

### Post by Sinkingships7 on 2008-06-27
```
sudo aptitude install soundconverter
```
Find it in Applications->Sound & Video

---

### Post by ChameleonDave on 2008-06-27
OK, before I saw your response, I edited my previous one to have more information.  I can explain each of the commands if you like.

---

### Post by Niloc on 2008-07-03
My problem is I have downloaded some books which I listen to on my MP3 player.
My player does not have a proper 'pause' function so if I want to stop a replay today and continue tomorrow, I have to 'fast forward' to where I finished which takes ages and sometimes drops out.

I want to split my MP3 files into (say) half hour chunks, I tried Audacity but end up with dozens of 1K files, can I do this with Sound Convertor and if so how?

Any help appreciated,

Colin from Melbourne

---

### Post by AnarkistNZ on 2008-07-03
> **Niloc said:**
> My problem is I have downloaded some books which I listen to on my MP3 player.
My player does not have a proper 'pause' function so if I want to stop a replay today and continue tomorrow, I have to 'fast forward' to where I finished which takes ages and sometimes drops out.

I want to split my MP3 files into (say) half hour chunks, I tried Audacity but end up with dozens of 1K files, can I do this with Sound Convertor and if so how?

Any help appreciated,

Colin from Melbourne

Audacity is easy.

Set your start time, set your finish time, and export that selection as mp3. Set LAME to encode in 32kbs (considering it's voice only) and you'll have a tiny file that is cut up into half hour (or however long your choose) chunks.

---

### Post by Niloc on 2008-07-03
AnarkistNZ I did exactly as you said, it said 'exporting the selected audio as MP3'. I ended up with a new folder called 'data' which contains 7002 1 MB files all .au extension but no MP3 files at all!

I cannot comprehend the LAME parameters, how do I set LAME to encode to 32kbps, I suspect this is the problem....

Thanks for your help...

Colin

---

### Post by ChameleonDave on 2008-07-03
> **Niloc said:**
> AnarkistNZ I did exactly as you said, it said 'exporting the selected audio as MP3'. I ended up with a new folder called 'data' which contains 7002 1 MB files all .au extension but no MP3 files at all!



I suspect that you are for some reason looking inside the project folder for Audacity rather than at the files you exported.

---

### Post by monolux on 2008-07-12
> **Sinkingships7 said:**
> ```
sudo aptitude install soundconverter
```
Find it in Applications->Sound & Video

txs a lot man really helpfull!!!

---

