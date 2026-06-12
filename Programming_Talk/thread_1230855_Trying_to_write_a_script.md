---
title: "Trying to write a script"
date: 2009-08-03
forum: Programming Talk
---

### Post by BufordPants on 2009-08-03
I am trying to develop a bash procedure called sortMP3Files() that "sorts" and moves MP3 files located in the source directory SOURCE given as the first argument into the destination directory DEST given as the second argument.

  I want to create a subdirectory in DEST for each new album name seen among the MP3 files of SOURCE. 
   I want to move an MP3 file with an album tag of AlbumX of SOURCE into DEST/AlbumX directory unless a file with that name already exists.  If so, I want the MP3 file to remain in SOURCE.
  Also, I want to rename the MP3 files of album directories of DEST so that they are now of the form nn-Album-Artist.mp3.  If an MP3 file has no track number tag, I want to to give it a default tag number.

Your help would be appreciated!

---

### Post by Tek-E on 2009-08-08
Have you at least given it a try yet?

---

### Post by BufordPants on 2009-08-15
Yeah, I figured it out!

---

