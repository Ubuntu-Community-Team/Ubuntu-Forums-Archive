---
title: "Another question from the eager question asker here at forum :)"
date: 2020-03-20
forum: New to Ubuntu
---

### Post by xcfstarflight1 on 2020-03-20
[B]Hi guys!
Hope you are not tired of me yet.. Stil working up the system


[/B]I was using rythmbox to play MP3. I do have one user with the KODI.
I want to be using mpg123 and i cannot remember the name of the wav to MP3/FLAC and how to use it to convert to FLAC and also put in Copyright on my music
etc.. Any good ideas? It was a terminal application.
Thanks guys! You are so supportive and I wish I will be one day too.,, And offcourse I do read manuals ;-)

---

### Post by xcfstarflight1 on 2020-03-20
Just an add. I want to convert my music from .wav to FLAC with best possible quality and add ID3 tags to it :)

---

### Post by mörgæs on 2020-03-21
If you ask giving your questions a clear and informative title there is a better chance that people are going to read them.

---

### Post by Holger_Gehrke on 2020-03-21
For converting .wav to .mp3 (and back) 'lame' is the CLI-tool of choice. For .flac the same can be done with 'flac'. Metadata in .flac-files is stored according to the vorbis comment specification. Tags can be set during conversion both for .mp3 and for .flac. Changing, adding or removing metadata from flac-files can be done with 'metaflac'. All mentioned programs are in the repos, the package names are identical to the program names. All programs come with documentation in the form of man-pages.

Holger

---

