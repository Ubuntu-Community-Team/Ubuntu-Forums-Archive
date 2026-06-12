---
title: "mp3gain query"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by gedzilla on 2008-10-01
I've been using mp3gain and easy mp3gain very successfully and after playing about with it thought i'd normalize the gain on my entire music directory using

find . -name *mp3 -exec mp3gain -a -k {} \;

Of course this worked great, but I was just wondering if anyone could tell me how to set my entire music directory to a different level (the default is 89db and i'd like it a bit higher - like 91.5 to 92.5db)

---

### Post by vanadium on 2008-10-01
The best thing you do first is to "undo" the changes you did (option -u). You choose -a to apply album gain, which is a good choice. However, the way you used the find command will have adjusted each file individually. Tracks from a same album will now have a different volume.

To adjust and really apply album gain, files of the same directory must be processed in the same run of mp3gain. The command you want looks like

```

find . -iname '*.mp3' -execdir mp3gain -a -k "{}" + 

```

Note the + rather than \; at the end: this command will make find to append all filenames of the current directory to the mp3gain command, such that all files of the same directory are processed by a single mp3gain command.

If these mp3s are intended for computer playback, you are better with the tag based approach, i.e. aaplying replaygain tags rather than changing the actual audio data. This is less intrusive, allows for more flexibility and is the way it works for other formats like ogg and flac as well. If it is to be used on devices that do not understand replaygain tags, your choice is the best.

I guess you can change the reference level with the -m or -d options. Check the manual (man mp3gain) and do a little test before proceeding.

---

### Post by gedzilla on 2008-10-02
That's great! I'll look into into that and let you know how I get on.
thanks!
:)

---

### Post by vanadium on 2008-10-02
I see that easymp3gain, like its Windows counterpart, has an mp3 target volume option.

---

### Post by evencoil on 2009-02-12
I tried using
```

find . -iname '*.mp3' -execdir mp3gain -a -k "{}" +

```

on a machine with find version 4.2.32 and it worked perfectly. However when I try to run the same command on a machine with find version 4.4.0, it just processes each file individually. (My file structure is the same on both machines.) Does anyone know what changed with the syntax? Thanks!

---

### Post by evencoil on 2009-02-12
hard to follow the bug reports for findutils, but it seems that they have had problems with the -execdir {} + functionality and have disabled it at times in the past, so this might be the case on the latest version as well.

---

