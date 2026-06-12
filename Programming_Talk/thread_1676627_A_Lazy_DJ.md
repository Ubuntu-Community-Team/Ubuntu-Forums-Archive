---
title: "A Lazy DJ"
date: 2011-01-27
forum: Programming Talk
---

### Post by dduckett on 2011-01-27
Here's the situation: I use Rhythmbox with Ubuntu to DJ at a dance club. There is a certain formula for most of the night: 2 salsa songs, 2 merengue, 2 bachata, 2 reggaeton, repeat. Usually I have to create a playlist by hand, which is very inefficient.

I send a humble request to the programmer's out there to ask if there is an easier way to do this. Is there some sort of script I could write to create a playlist that would read music files and plug them in (randomly) for a genre sequence I specified  (while not repeating that song again in the playlist)? Or would tackling this problem be much more involved (involving more than just a script , perhaps another programming language)? I've only dabbled around in programming, but I catch on to new stuff fast.

Thanks in advance for any help.

To clarify: I would like to write a file that would specify genre:
Salsa
Salsa
Merengue
Merengue
Bachata 
Bachata
Reggaeton
Reggaeton
Salsa
Salsa
etc.

and have the script/program read this information and plug in songs (choosing a random song from a particular genre) in the sequence I specify without repeating any songs.

---

### Post by Kirboosy on 2011-01-27
Doesn't rhythmbox have a Smart Playlist that you can setup? (It will only work if you keep your media organized very well)

---

### Post by dduckett on 2011-01-27
It does, this limits things down, but it doesn't sequence the songs in sets of two, and it also tends to pull overly much from a single genre. For example, I just created an auto-playlist, and it pulled 70% Bachata and had places where there were 12 songs in a row... If I could get it to pull equally from each genre then that would work because it wouldn't be so much trouble to reorganize....

---

### Post by Kirboosy on 2011-01-27
Hmm it doesn't seem like it should be that hard to do. You should be able to make a script of something that says genre genre ************* repeat. I have looked around and I haven't found any such plugin for Ryhthmbox.

Maybe another media player would have that feature. Then again it shouldn't be that big of a deal because after all you are getting paid to be a DJ ;)

---

### Post by dduckett on 2011-01-27
No pay, just do it because I love to dance and bring people out to do it as well. The benefit of DJing is you know the songs coming up and get first dibs on dancing with the ladies :) I'm just a college student I'm afraid (which is why I'd like to script it because it would probably cut the time to get a good playlist in half). I'll look more into what can be done..

Edit: 
[http://linuxreviews.org/quicktips/playlists/](http://linuxreviews.org/quicktips/playlists/)

Here is a start, this would generate a play list, but how would I specify that certain songs were a certain genre.... I need something to either read the files or my own way of tagging my files.

---

