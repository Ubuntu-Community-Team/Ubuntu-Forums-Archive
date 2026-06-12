---
title: "Consolidating/Renaming mp3 files...help"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by mitchc3 on 2012-11-02
Hello all,

After ripping all the music off my ipod onto my laptop, I am left with a corpus of mp3 files. They all have names like AKWS.mp3, and I would like to change this. The information of the song is correctly labelled when I open it with Banshee, I would like to organize my file directory. 

Does anyone know any programs or commands that I could use to efficiently organize my music collection? Preferably something other than me renaming each individual file :D.

I am using ubuntu 12.04.

Thank you and Rock on:guitar:

---

### Post by papibe on 2012-11-02
Hi mitchc3. Welcome to the forums ):P

If the music is organized correctly on Banshee, it means that the id3 tags are OK (internal fields with song's metadata).

There are several programs that allow you to rename files from the internal id3 tags. I've  used Kid3 successfully for that in the past. For other alternatives look for 'id3 editor' in the Software Center.

The only problem with that approach is that most editors assumed that you have your media organized in one folder per album, so it may require some tricks to rename one file at a time and not make changes in other files (basically you create a directory per file and you would be OK).

Another alternative is to do some scripting. There are several command line tools like id3v2, id3ed, mp3info that would allow you to obtain the name of the artist and song, thus allowing you to rename the file properly. This approach may need some scripting skills.

I hope that helps. Let us know how it goes.
Regards.

---

