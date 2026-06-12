---
title: "Grip mp3 encoding problem"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by paker on 2008-05-18
I installed ubuntu-restricted-extras. But I still have Grip mp3 conversion problem. It rips CD but doesn't do mp3 conversion. Here is the encoder setup:

encoder: lame
encoder executable: /usr/bin/lame
encoder command line: -V 6
encoder file extension: mp3
encoder file format: ~/mp3/%A%d%n.%x

When CD ripping is complete, I see WAV files and MP3 files in /mp3 folder. Each WAV file is about 100 MB, but MP3 file is only about 100 KB. Conversion is attempted but not completed?

---

### Post by HotShotDJ on 2008-05-18
> **paker said:**
> I installed ubuntu-restricted-extras. But I still have Grip mp3 conversion problem. It rips CD but doesn't do mp3 conversion You need to install lame.  It doesn't get installed with ubuntu-restricted-extras.  Grip drove me out of my mind until I discovered this.

---

### Post by paker on 2008-05-18
LAME is installed. It is in  /usr/bin/lame. In Synaptic Package Manger  lame is marked green (installed).

If anyone uses Grip, will he kindly check the encoder page and tell me how his is different from mine? Thanks.

---

### Post by ramjet_1953 on 2008-05-18
Here's mine:

encoder: lame
encoder executable: /usr/bin/lame
encoder command line: -h -b %b %w %m
encoder file extension: mp3
encoder file format: ~/mp3/%A/%d/%n.mp3

I have fiddled with this in the past, so it may not be the default settings. but it does seem to work OK with me, even though I use ogg mostly.

Regards,
Roger :cool:

---

### Post by HotShotDJ on 2008-05-18
> **paker said:**
> If anyone uses Grip, will he kindly check the encoder page and tell me how his is different from mine? Thanks.And mine:

Encoder: lame
Encoder executable:  /usr/bin/lame
Encoder command-line:  -h -b %b %w %m
Encoder file extension:  mp3
Encode file format:  ~/Music/%A/%d/%n.%x

---

### Post by paker on 2008-05-18
Thanks my friends. YOU SOLVED MY PROBLEM. My command line didn't have the file names! I added %w (name of the wav file to be converted) and %m (name of mp3 file), and it's now working! Thank you so much.

OLD command line: -V 4
NEW command line: -V 4 %w %m

By the way, I read somewhere that "-h" is an old lame command that is no longer needed. I don't know if it will harm (slow down) though. "-b" is constant bit rate encoding? Why not use variable bit rate? It gives better sound for same file size. Even my old car CD (about 5-6 years old) handles vbr well. "-V 4" gives about 165-170 kbit rate. "-V 5" gives about 125-130 kbit rate.

---

