---
title: "Batch Edit files with No Extension"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by decrepitneophyte on 2011-09-22
I have been using Ubuntu for a long time, and still have only a superficial understanding of its uses. I just switched to 11.04, on my satellite x205, and in the 5 years with this machine I have never taken the time to get the nvidia graphics or the sd card reader to work.

Ok, all that said, I just got Google Music and I am excited to upload my music library and use it on my thunderbolt.  When I used Google Music Manager, it only found about 20 of my 6000 some files.  

After some confusion I noticed that none of the music files had extensions.  Opening the properties of a given file it offers the type, "MPEG-4 audio (audio/mp4)" Some are mp3's. 

a file might look like...
/media/STORAGE/Music/Elliott Smith/Live at EJ's 5-15-97/14-Say Yes

if I rename the file and add ".m4a" to it everything is great!

So how do I add .m4a to all of these files, and in doing so how do I differentiate from mp3's and m4a's?

How does Ubuntu know that this is an mpeg 4 without the extension?

---

### Post by TeoBigusGeekus on 2011-09-22
Extensions in linux are useless.

If all files where mp3s or m4as, it would be easy to add an extension to them with a script, but if you want to differentiate the formats, then I'm afraid you have to do it by hand...

---

### Post by papibe on 2011-09-22
There are tricks you can use to automate the recognition of different formats.

Do you have just mp4s or also other formats?

Regards.

---

### Post by SecretCode on 2011-09-22
Linux does a lot of examination of file contents (for [magic numbers]("http://en.wikipedia.org/wiki/Magic_number_%28programming%29") etc) rather than blindly relying on extensions.

Try the _file_ command - at the command line - e.g.
```
$ file Various\ Artists\ -\ 99\ Luftballons.mp3 
Various Artists - 99 Luftballons.mp3: Audio file with ID3 version 2.3.0, contains: MPEG ADTS, layer III, v2,  64 kbps, 22.05 kHz, JntStereo
```
This output doesn't say "MP3" as such but it does say "MPEG" and "layer III", so you could test for this in a script.

---

### Post by Paddy Landau on 2011-09-22
The program [pyRenamer]("apt:pyrenamer") is a flexible GUI that allows you to mass-rename files. It has a Preview button to check what you're doing before you do it, and a special tab for music files.

However, it's not intelligent enough to tell the difference between MP3 and M4A. If you have some simple way of telling (e.g. MP3 and M4A files are in different directories), that would make it easier for you.

It would be possible to write a script to fully automate the process. You would have to use *file* (as suggested) with the mime-type option as follows:
```
file --brief --mime-type *filename*
```As I don't have any M4A files, I can't suggest a script.

---

