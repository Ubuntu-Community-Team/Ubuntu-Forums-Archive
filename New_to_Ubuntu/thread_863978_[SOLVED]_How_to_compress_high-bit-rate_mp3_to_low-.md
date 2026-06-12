---
title: "[SOLVED] How to compress high-bit-rate mp3 to low-bit-rate mp3?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by paker on 2008-07-19
Can it be done? I have insane mp3's at 320 kbit. It's too bulky for digital mp3 player. Is there a way to compress 320k CBR mp3 to <200K VBR mp3? Thanks.

---

### Post by cpetercarter on 2008-07-19
You can load each mp3 into an audio recording/editing programme and get the programme to export the file in a new format (lower bit rate etc). Trouble is that you would have to do this for each mp3 one at a time, which could be quite time-consuming if you have a lot of files to convert. Audacity (in the repos) is a common choice of audio recording/editing software, though my favourite is WavePad, a Windows prog which runs well under Wine.

---

### Post by Vivaldi Gloria on 2008-07-19
> **paker said:**
> Can it be done? I have insane mp3's at 320 kbit. It's too bulky for digital mp3 player. Is there a way to compress 320k CBR mp3 to <200K VBR mp3? Thanks.

You can use the command line to do it easily. Install lame using 

```
sudo apt-get install lame
```

in a terminal (or use synaptic) and google a bit for lame command line options.

The big papa of all sound players/converters is foobar2000. Every audiophile in [www.hydrogenaudio.org](www.hydrogenaudio.org) forums uses it. It works nicely with wine. I have been looking for a native linux app that comes close to it for years now - there isn't any.

---

### Post by paker on 2008-07-19
Thanks. Since I have used Audacity before and am dealing with a handful only, I will use it.

---

### Post by pi.boy.travis on 2008-07-19
You could use sound converter (in the repositories, use add/remove) whick will allow you to convert lots of audio files at once.

---

