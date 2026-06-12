---
title: "C#/Mono MP3?"
date: 2009-10-12
forum: Programming Talk
---

### Post by dchurch24 on 2009-10-12
Hi,

I've been writing a media player for some time now using C#.

For the most part it's working, it looks good (well, I think so), it scrolls through Artist/Song/Year etc.... it can take requests from any source on my network blah, blah....

...But...for some reason, every Mp3 it plays sounds like it's been recorded from a vinyl record that's been used as a brake disk for a mini-metro - i.e. very, very crackly.

This is the code used to play the file (the reader object returns the path to the file and is converted using 'Replace' to a Windows path which is mapped to the same drive holding the music files) - I am developing on both Windows and Ubuntu, and the final 'product' is intended for deployment on my Xubuntu box.

It uses the SDLDOTNET Music library.

```

MusicPlayer.EnableMusicFinishedCallback();
Music techno = new Music(Reader.GetValue(1).ToString().Replace("/home/dave/Music/", "m:\\"));
techno.Play();  

```

If I play the same file using say, Rhythmbox or VLC, then it sounds fine.  This leads me to think that perhaps the decryption in the SDL.Net library is not complete and/or working properly.

Is there another library I can use to play Mp3 files using Mono/C#?

---

### Post by directhex on 2009-10-12
> **dchurch24 said:**
> Hi,

I've been writing a media player for some time now using C#.

For the most part it's working, it looks good (well, I think so), it scrolls through Artist/Song/Year etc.... it can take requests from any source on my network blah, blah....

...But...for some reason, every Mp3 it plays sounds like it's been recorded from a vinyl record that's been used as a brake disk for a mini-metro - i.e. very, very crackly.

This is the code used to play the file (the reader object returns the path to the file and is converted using 'Replace' to a Windows path which is mapped to the same drive holding the music files) - I am developing on both Windows and Ubuntu, and the final 'product' is intended for deployment on my Xubuntu box.

It uses the SDLDOTNET Music library.

```

MusicPlayer.EnableMusicFinishedCallback();
Music techno = new Music(Reader.GetValue(1).ToString().Replace("/home/dave/Music/", "m:\\"));
techno.Play();  

```

If I play the same file using say, Rhythmbox or VLC, then it sounds fine.  This leads me to think that perhaps the decryption in the SDL.Net library is not complete and/or working properly.

Is there another library I can use to play Mp3 files using Mono/C#?

[http://gstreamer.freedesktop.org/src/gstreamer-sharp/](http://gstreamer.freedesktop.org/src/gstreamer-sharp/)

---

### Post by dchurch24 on 2009-10-12
Excellent - thank you.

I'll have a play ;-)

---

