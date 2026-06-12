---
title: "mp3 tag editor"
date: 2009-01-29
forum: Programming Talk
---

### Post by smartygoldenfish on 2009-01-29
hi.
i have organized my music in a weird fashion and now i am getting its aftereffects.

CURRENT SCENARIO:
There are N number of directories, each having variable number of songs. Each and every song is a MP3. No song is having its ALBUM TAG set.
Each directory is a name of a particular movie. Each song in that directory has parent movie's song(s).

AIM:
Change ALBUM attribute [or mp3 tag] of each and every song to its parent directory name. eg. If song1.mp3 is in Titanic, then song1.mp3's Album should be changed to Titanic. 

**It is required to create a Script that can sit in a "root" folder, which has all Parent Movie directories and who in turn have respective songs.**

---

### Post by mike_g on 2009-01-29
Check out: [http://id3lib.sourceforge.net/](http://id3lib.sourceforge.net/)

You can use the library to code somethin to edit mp3 header information, or just grab one of the progs linked on the page and use it.

---

### Post by fubbleskag on 2009-01-29
Audio Tag Tool will let you change id3 tags for batches based on file name and/or structure

```
sudo apt-get install tagtool
```

---

