---
title: "[SOLVED] Combine mp3's?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-10-17
Is there a way to combine multiple mp3's?

---

### Post by nothingspecial on 2008-10-17
You can put them together with audacity

[http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

---

### Post by OutOfReach on 2008-10-17
You would need another program to combine MP3s.

EDIT: nothingspecial beat me to it, Audacity is a very nice program (pretty easy to use too). I think it is also available in the repositories.

---

### Post by cariboo on 2008-10-17
Have a look at mp3wrap, it is available in the repositories.

Make sure you have the universe repositories checked in System-->Administration-->Software Sources.

Mp3wrap is a command  line utility so you will have to open a terminal to use it.

Jim

---

### Post by benerivo on 2008-10-17
From the terminal i can do```
cat 'fileone.mp3' 'filetwo.mp3' > mynewcombinedfile.mp3
```which is almost instantaneous.

---

### Post by ajgreeny on 2008-10-17
I would go with mp3wrap, and also mp3splt (that's not a typo, there is no i in mp3splt) if you want to separate them again.  Both work without decoding/recoding so there is no loss of audio quality, which audacity will give you.  You can, however, combine your mp3s in much more controllable ways, eg with overlaps etc etc, with audacity, so it all depends on how you need to combine them.

---

### Post by slughappy1 on 2008-10-17
Well those all seem like viable options. I suppose I should have said why I want to combine them. I listen to a lot of audiobooks at work. I wanted to combine multiple tracks and organize all of my audiobooks into chapters. Instead of having multiple tracks for one chapter. Which one of those methods do you think would best suite my purpose?

---

### Post by FranMichaels on 2008-10-17
Well, I would go with the user that recommended cat.

For example lets say your audio book is on the desktop in a folder called audiobook

Fire up a terminal

cd Desktop/audiobook
cat * > book.mp3

That's it.
You can use tab completion to help you with file names (try typing cd Des then hit tab, sometimes twice if there are multiple stuff.) It will make it a breeze.

If it's too tedious, one could make a very simple nautilus script to let you just right click or what not.

I say give it a go, using terminal apps are usually #1 when it comes to repetitive and non-interactive tasks. Imagemagick comes to mind as an awesome example. :D

---

### Post by slughappy1 on 2008-10-17
Ok then, I have a couple of questions for the cat method. First, it can combine more than just two at once right? Second, will it just create a new mp3? Will the original files be changed at all? will there be pauses or loss of quality?

---

### Post by benerivo on 2008-10-18
> **slughappy1 said:**
> Ok then, I have a couple of questions for the cat method. First, it can combine more than just two at once right? Second, will it just create a new mp3? Will the original files be changed at all? will there be pauses or loss of quality?

When i used it, it allowed more than two files concatenated. It does not replace or alter the originals, but instead just makes a brand new mp3. There is no pause between tracks other than any silence at the start and end, that each track may already have. This is not transcoding, so there is no change to the mp3 quality/bitrate.

Just make a copy of three of your mp3's and do some testing.

---

### Post by slughappy1 on 2008-10-30
So I found ( what I think is ) a problem. When I used the cat method it used the ID3 tags from the first mp3. That wouldn't be a problem, except that it says that the mp3 is the wrong length. The mp3's say they are the length of the first mp3. Even if the mp3 is actually 20 minutes long. Any way to fix this?

---

### Post by jimmy the saint on 2009-02-20
I had the same problem with cat and mp3wrap.  I tried to delete the id3 information altogether, but that didn't seem to work.  I just gave up and used audacity.  If someone knows how to clear the id3 information I would love to hear how.

---

### Post by slughappy1 on 2009-02-20
I guess I should have responded to my last as well. Since I couldn't do anything with the ID3 tags. I just ended up using Audacity. A slower method true, but at least it works ;-)

---

### Post by mgmiller on 2009-02-20
> If someone knows how to clear the id3 information I would love to hear how.```
sudo apt-get install easytag
```This program will allow you to do anything with ID3 tags.

So after you combine the mp3's, open them in easy tag and modify the ID3 tags to your liking.

The program exfalso can also do this.

If you just want to remove the tag, in the top bar of easytag, there is an icon that looks like a little whisk broom.  That will remove the tag from the high lighted file.
I'm not sure if the file length is part of the ID3 tag, or part of the meta data of the file.  If it's metadata, then an ID3 editor probably won't do what you want.

Here's a thought, what happens if you combine the mp3's with the command line as instructed above and then open the new combined file in audacity and make sure the time slider sees the whole file instead of just the first one.  Then save it with a new name and maybe the time meta data will be correct.

---

### Post by TunaCanTommy on 2009-05-05
When I rip audiobook CD's I use "abcde" it will pad the track number with zeros so that you can sort the files in the right order. This is important because I then use the "cat" command to combine them into a single file.  Go here to learn about "ABCDE".
 
[HTML]http://www.andrews-corner.org/index.html[/HTML]

Each CD is ripped to a folder labeled DISC01, DISC02, DISC03, etc.
Then open a terminal, navigate to the first folder and execute:

```
$ cat *.mp3 > Disc01.mp3
```

Rinse / Repeat . . . until you have one file for each "original" CD.
You original files will be unchanged but a new file will be created that contains all the files on the disc.  Now go to the next folder and execute the same code but make sure you change the output to Disc02.mp3 . . and so on.
Once you get all the files combined move them to a new folder and open a tag editor program, I use Audio Tag Tool.  Delete all the existing tags on the new files and retag them. Auto Tag lets you use the file name for the TITLE tag, and it will auto-increment the TRACKNUM.
I think of an audiobook as a music album; ARTIST=AUTHOR, ALBUM=BOOK, TITLE=TITLE, TRACKNUM=TRACKNUM.
Most MP3 player are happy with ID3v2 tags. ( I have a Sansa CLIP )  With my player it wants the GENRE to be set to "audiobook" - it's not on the pick-list, just type it in.
If everything works OK I go back and delete all the original ripped files.

---

### Post by Didius Falco on 2009-05-05
If you have RhythmBox installed, you can edit the tags in that program. Just import the mp3, highlight it, right-click, go to properties and edit it anyway you want.

I often sit and listen to music while I'm editing my own tags. I prefer to do it myself, because I often make custom albums - kind of an mp3 mix tape.

(Yes, I **am** old enough to remember those!) :rolleyes:

---

### Post by freak42 on 2009-05-05
cat'ing mp3 will produce non-standard conforming mp3 files, while most players will be able to handle this more or less gracefully, there is no guarantee for it. I don't recommend it.

---

### Post by logos34 on 2009-05-05
> **TunaCanTommy said:**
> When I rip audiobook CD's I use "abcde" it will pad the track number with zeros so that you can sort the files in the right order. This is important because I then use the "cat" command to combine them into a single file. 

But there's a single command for that, TunaCanTommy!

> abcde -1 -M -o mp3

makes a single mp3 file out of entire CD + cue sheet.

Then you can divide it back up into the individual tracks again with separate app [mp3splt]("http://mp3splt.sourceforge.net/mp3splt_page/home.php"):

> mp3splt -c file.cue file.mp3

done.

Saves a lot of time.  Many people overlook that abcde option.  (unfortunately, abcde will only separate into individual tracks again if you use flac format, which is the only one to contain an "embedded" cue sheet)

---

### Post by TunaCanTommy on 2009-05-06
Thanks LOGOS34 . . . I've previously used the -1 option to rip Audiobook CD's and most other options I've been putting in the abcde.conf file.  After your post I looked at the "man" for abcde and see there's quite a few options at the command line . . . good info.

---

