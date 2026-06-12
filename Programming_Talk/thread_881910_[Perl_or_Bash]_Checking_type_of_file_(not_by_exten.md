---
title: "[Perl or Bash] Checking type of file (not by extension)"
date: 2008-08-06
forum: Programming Talk
---

### Post by ConMan318 on 2008-08-06
Is there any way to check the type of file (in Perl or Bash) by looking at contents rather than extension?  For example is there a way to check if a file is an audio file or not?  Since there are so many different types of audio files, I would like to be able to check without having to regex a bunch of different file type extensions, which wouldn't be all-inclusive anyway.

Also, is there a way to check if a file can be opened by a certain program without actually opening it?  I don't know of any file tests that can check something like that, though I think it could be possible since I know Perl can try to determine if a file is text or binary.  Since Perl specializes in text though, I don't know if it can check audio or video file types.  For example having a filename and seeing if it can be opened with Totem.

Thanks in advance.

---

### Post by slavik on 2008-08-06
look at the file command

---

### Post by ConMan318 on 2008-08-06
Cool, thanks for that.  

So that command returns something like this:
```

$ file /stor/music/Muse/Absolution/01.\ Intro.mp3 
/stor/music/Muse/Absolution/01. Intro.mp3: Audio file with ID3 version 24.0 tag, MP3 encoding

```

So if I am testing for an audio file, would the best option be to regex for the word "Audio" after the colon in the output of the 'file' command?

---

### Post by geirha on 2008-08-06
If you only need to know if it's video, audio, text etc. Then try with the --mime option. Should be easier and more safe to parse.

---

