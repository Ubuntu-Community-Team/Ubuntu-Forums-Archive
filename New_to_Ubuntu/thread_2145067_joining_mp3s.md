---
title: "joining mp3s"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by anevilgiraffe on 2013-05-14
slightly annoyingly my decent mp3 player died and my back up has a habit of randomly moving mp3s playing order in a way I have yet to fathom. As I listen to a lot of audio dramas which are broken up into tracks, this is sub optimal so i need to join each track into a single mp3 for each audio.

I have tried U Splitter, which appear to only work with joining files that it has already split, and tried the terminal commands to combine mp3s in the folder, but that has caused a formating error and a 2 hour mp3 only has the first track audio and nothing for the rest of the 2 hours.

So, am I missing some obvious way to combine these mp3s into a single (long) track?

I have also tried Audacity, but really can't figure the hell out of it, so if that can do it, basic steps please...

Thanks in advance.

Chris.

---

### Post by HermanAB on 2013-05-14
It would be more optimal to make a playlist.  You could simply cat the files together, but here are better methods:

[http://superuser.com/questions/314239/how-to-join-merge-many-mp3-files](http://superuser.com/questions/314239/how-to-join-merge-many-mp3-files)

[http://stackoverflow.com/questions/62618/what-is-the-best-way-to-merge-mp3-files](http://stackoverflow.com/questions/62618/what-is-the-best-way-to-merge-mp3-files)

[http://stream-recorder.com/forum/join-multiple-mp3-files-t4656.html?](http://stream-recorder.com/forum/join-multiple-mp3-files-t4656.html?)

---

### Post by anevilgiraffe on 2013-05-14
I tried cat at the terminal prompt, gave a format error which I figure would tally with the comments on one of your links regarding the the first track only being played from a combined file. a quick look at those does show some alternatives, so will have a look when I get home tonight.

---

### Post by Dennis N on 2013-05-14
Audacity is the way to go. Basically, here would be the steps. You probably need to get some orientation with the basic usage of the program first if you are unfamiliar with it. 

To join two files:

Open file 1 (File > Open).
Open a new window (File > New).
Open file 2 (File > Open) in the new window (window 2).
In window 2, Copy the track (Edit > Copy). 
In window 1, move cursor to end of track.
Paste (Edit > Paste).
Apply Normalize Effect.
Export as mp3.

---

### Post by coffeecat on 2013-05-14
As the links that HermanAB posted point out, simply doing a cat creates a file with each header and set of IDv3 tags somewhere in the stream. Worse, some music players will simply stop when they get to the first header inside the stream.

If Dennis N's suggestion for using Audacity doesn't work for you, have a look at this post:

[http://ubuntuforums.org/showthread.php?t=1768491&p=10868154#post10868154](http://ubuntuforums.org/showthread.php?t=1768491&p=10868154#post10868154)

Read from after the links, which are now dead. They described how to do this from a Mac terminal, and my 1,2,3,4 notes are how I did this in Ubuntu. Which worked a couple of years ago, but it is something of a fiddle.

---

