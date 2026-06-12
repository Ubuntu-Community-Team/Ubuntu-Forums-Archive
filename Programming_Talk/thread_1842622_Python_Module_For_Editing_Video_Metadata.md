---
title: "Python Module For Editing Video Metadata?"
date: 2011-09-11
forum: Programming Talk
---

### Post by dniMretsaM on 2011-09-11
I was wondering if there are any good Python modules for editing video metadata. I know Mutagen is very good for audio files, but I haven't been able to find any information about a module for video metadata. Any suggestions would be greatly appreciated.

---

### Post by dniMretsaM on 2011-09-13
Bump.

---

### Post by dniMretsaM on 2011-09-14
Bump.

---

### Post by dniMretsaM on 2011-09-17
Bump.

---

### Post by dniMretsaM on 2011-09-18
Bump. Anyone?

---

### Post by jerenept on 2011-09-19
> **dniMretsaM said:**
> I was wondering if there are any good Python modules for editing video metadata. I know Mutagen is very good for audio files, but I haven't been able to find any information about a module for video metadata. Any suggestions would be greatly appreciated.

Maybe [pyFFMpeg]("http://code.google.com/p/pyffmpeg/")?

There seems to not be anything else, but I think you already knew that :P

---

### Post by dniMretsaM on 2011-09-19
I'll have a look at that, thank you! And yeah, video metadata editing doesn't seem to have much support.

---

### Post by dniMretsaM on 2011-09-19
As far as I can see, it just supports the normal transcoding ability of FFmpeg, so not what I'm looking for (although I may use it for something else though). I'll continue looking. I may end up use a program I can run as a sub process... Maybe someday (when I'm much more skilled), I'll write my own module for this.

---

### Post by HarrisonNapper on 2011-09-19
PyPI brought up one that lets you get metadata (hachoir-metadata), so maybe that dev has looked at it before. Contacting the dev of that package is probably a good place to start.

---

### Post by dniMretsaM on 2011-09-19
> **HarrisonNapper said:**
> PyPI brought up one that lets you get metadata (hachoir-metadata), so maybe that dev has looked at it before. Contacting the dev of that package is probably a good place to start.

Problem. He's French, I don't speak French. I can't send a message to him on bitbucket (where he hosts his code) since I'm not a member (and I'm not going to join) and I can't find any other type of contact info (like an email address or something). And while searching I found a lot of libraries for viewing metadata (like kaa-metadata), but absolutely nothing for editing. EasyTAG can edit videos, anybody know of a CLI version of EasyTAG (<- stab in the dark)?

---

### Post by zcartist on 2011-11-16
I don't know about python but you can edit metadata in banshee and VLC

banshee

go to edit/preferences

check write metadata to file

import the video and right click edit track info and save

vlc

play video

tools/edit media info 

edit save

---

