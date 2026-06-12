---
title: "Mencoder: .ogg to .mp3"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Edd11111 on 2008-07-01
How do I use mencoder to convert .ogg vorbis files to .mp3 files?

---

### Post by Thanoulis on 2008-07-01
I do not know about mencoder, but there is a handy nautilus script i use:
```
sudo apt-get nautilus-script-audio-convert
ln -s /usr/share/nautilus-scripts/ConvertAudioFile ~/.gnome2/nautilus-scripts/ConvertAudioFile
```

---

### Post by ChameleonDave on 2008-07-01
> **Edd11111 said:**
> How do I use mencoder to convert .ogg vorbis files to .mp3 files?

I generally use sox to convert audio files.  Mencoder is normally for videos.

If you have a file called "Beethoven.ogg" on your desktop, then this will decode it from OGG Vorbis and then re-encode it to MP3
```

sudo apt-get install sox lame
cd ~/Desktop
sox Beethoven.ogg  Beethoven.wav
lame Beethoven.wav

```

Type "lame --help" to see the options for changing the quality level.

---

### Post by TenPlus1 on 2008-07-01
In Add/Remove their is a program called SoundConverter that lets you simply drag & drop files/folders to be converted from one format to another,..

---

### Post by billgoldberg on 2008-07-01
I use ffmpeg to convert files (the version from the medibuntu repo).

Well, I actually use the winff gui for ffmpeg to convert files.

Besides audio, it also does video.

Winff isn't in the repos (google for it, it's a .deb), you'll need the ffmpeg version from the medibuntu repo.

---

### Post by LookTJ on 2008-07-01
You could try using ffmpeg:

**Install FFMPEG: **```
sudo aptitude install ffmpeg
```

**Convert OGG to MP3: **```
ffmpeg -i inputoggfile.ogg -ab  128 outputmp3file.mp3
```

:D Hopes this helps!

---

### Post by msrinath80 on 2008-07-01
Well, someone had to mention it: Not a good idea to go from lossy (OGG) to lossy (MP3) formats.

On the other hand, if you are a free software zealot like me, you might want to convert all your LOSSY & patented (MP3) formats to LOSSLESS & free (flac) formats instead. The only advantage is that you now have an audio file that is free software compatible (not patent encumbered). Doing so of course gives no improvement in audio quality when compared to the original MP3 encoding. A significant disadvantage that I can think of is the increase in file size by converting MP3 to FLAC. But that seems to be quite moot given the monstrous hard drives of today.

---

### Post by ChameleonDave on 2008-07-01
> **msrinath80 said:**
> Well, someone had to mention it: Not a good idea to go from lossy (OGG) to lossy (MP3) formats.

I'm sure he's doing it for compatibility with an MP3 player.

---

