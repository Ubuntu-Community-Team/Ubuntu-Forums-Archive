---
title: "[SOLVED] Converting alot of songs .m4p --&amp;gt; .mp3"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by saj0577 on 2008-10-27
I got alot of songs in .m4p format (unencrypted & playable on my computer) they are all in folders and subfolders(they need to stay this way)

and what i want to do is convert them all to .mp3 using this as my gstreamer pipeline:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=4 ! id3v2mux


Is there a script to do this with that i can set away and it will convert them all and when i come back and check the computer they will be done?


Saj

---

### Post by vanadium on 2008-10-27
There is no script, but you have your powerful bash shell that allows you to automate almost anything you want. This is the idea:

```

find <top_of_directorytree> -iname "*.m4p" -execdir <command> "{}" \;

```

If you could post the command line needed to convert a single file, we might help to think how this might be incorporated in the find command.

---

### Post by saj0577 on 2008-10-27
> **vanadium said:**
> There is no script, but you have your powerful bash shell that allows you to automate almost anything you want. This is the idea:

```

find <top_of_directorytree> -iname "*.m4p" -execdir <command> "{}" \;

```

If you could post the command line needed to convert a single file, we might help to think how this might be incorporated in the find command.


I normally use sound-juicer so i dont know the command.ANyone able to help?

Saj

---

### Post by saj0577 on 2008-11-04
I just ended up using the sound converter application and adding the folder I wanted to be converted.

If anyone finds a terminal way please let me know so I can run it without a GUI.

Saj

---

