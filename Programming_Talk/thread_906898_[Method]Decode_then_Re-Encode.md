---
title: "[Method]Decode then Re-Encode"
date: 2008-08-31
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-31
Hello,

It turns out that VLC does not possess all codec's (of course not) and the few that it doesn't have are mp3 files i have an entire album of. Would it make sence to Decode the song, and then Re-Encode it with another encoder? It would be best if i could use builtin linux programs (or ones i could get with synaptic). I put this in the programming section becasue my hopes would be to make a batch or shell program that could do all the files in a directory (including sub directories).

Thanks
~Cody Woolaver

---

### Post by Bachstelze on 2008-09-01
VLC cannot play MP3 files? Maybe Ubuntu's one was compiled without MP3 support, but that would be weird since VLC is suposed to be a more or less universal player... Anyway, ffmpeg sounds like what you need, it will convert your MP3s with one command, so it will be easy to integrate into e.g. a shell script.

For example, to convert a mp3 into Vorbis :

```
ffmpeg -i myfile.mp3 -acodec vorbis -aq 60 myfile.ogg
```

More information about ffmpeg usage [here](http://howto-pages.org/ffmpeg/#basicaudio).

---

### Post by Pyro.699 on 2008-09-01
It can play mp3 files ^^: there are some music files that are encoded differently and i need to re-encode them

---

### Post by Bachstelze on 2008-09-01
> **Pyro.699 said:**
> It can play mp3 files ^^: there are some music files that are encoded differently and i need to re-encode them

That's weird. MP3 is MP3, there aren't many different ways to encode it... Anyway, try ffmpeg and see if it does the trick.

---

### Post by Pyro.699 on 2008-09-01
Would there be a way to do this while keeping the mp3 format?

Heres the link on the VLC Forums

[http://forum.videolan.org/viewtopic.php?f=14&t=34657&start=0&st=0&sk=t&sd=a](http://forum.videolan.org/viewtopic.php?f=14&t=34657&start=0&st=0&sk=t&sd=a)

---

### Post by Bachstelze on 2008-09-01
I'm not sure whether or not the ffmpeg build that ships with Ubuntu has MP3 encoding support compiled in. Assuming it has, the command is :

```
ffmpeg -i myfile.mp3 -acodec libmp3lame -abr 160k mynewfile.mp3
```

(You can of course change the bitrade as desired)

---

### Post by Pyro.699 on 2008-09-01
> **HymnToLife said:**
> I'm not sure whether or not the ffmpeg build that ships with Ubuntu has MP3 encoding support compiled in. Assuming it has, the command is :

```
ffmpeg -i myfile.mp3 -acodec libmp3lame -abr 160k mynewfile.mp3
```

(You can of course change the bitrade as desired)
Thank you, this did work. Now i want to make a batch program with this but also include all the tags that go with the file if they had any. such as author, track number, title and other information. I also remember there being something like 2 versions of the id information.

Another thing that i couldn't find was that the -abr option didn't work. I looked in the docs and it said that -b was the option to set the bitrate (but it didnt really work (tried 320k)

Also, how would i go about getting all audio typed (mp3, ogg, flac, and other types) listed in a directory and also sub directory. (batch or shell)

Thanks
~Cody Woolaver

---

