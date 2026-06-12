---
title: "Duplicate songs in music library..."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by OZFive on 2008-07-03
So I was finally able to rescue the data off my old Mac hard drive and load the music into my Music library.  YAY!  But the songs that I had on my ipod and the ones from my library are now causing duplicate songs all over my playlists.  I know yuour asking, how did the files copy if they are the same file...  Well I updated the ID Tags off I Eat Brainz using Picard and unified all the file names with Audio Tag Tool.  I wanted a clean folder and files to have the correct tags.  The new files.... Not done and now it is too late to redo them all.


How do I remove duplicate music like I did with iTunes?

Help!

---

### Post by ChameleonDave on 2008-07-04
Hmmm, let me think...

If you go to the relevant directory and type in the following:

```
ls -Ss
```

Then you will get a list of files in size order.  Files with exactly the same size will be next to each other and you will thus be able to see that they are the same file.

With a bit of thought I could make a script that would automatically delete one of each of those files.

---

### Post by ituen on 2008-07-04
When i used windows, i encountered that problem. But there is a yahoo widget that can help you eliminate double files. Ita a itunes player and gives u the option of deleting duplicate files.

If u want it, quote me when replying and i would get the link for you

---

### Post by OZFive on 2008-07-04
thos eare both good suggestions thanks, but isn't there some way to do it like in iTunes where you can use a media player to do it for you easier?  Does Banshee, Rythmbox, Exaile, or others have a way to do this?

---

### Post by OZFive on 2008-07-09
No better ideas?

---

### Post by decoherence on 2008-07-09
If the songs are actually duplicates of the same file (as opposed to the same song downloaded twice) the program fslint should be able to do what you want. It's basically a GUI for filesystem cleanup chores, among them finding duplicate files. Note, that's "duplicate files" and not "duplicate songs."

Here is the related feature request in Banshee's bugzilla [http://bugzilla.gnome.org/show_bug.cgi?id=133109](http://bugzilla.gnome.org/show_bug.cgi?id=133109)

---

### Post by OZFive on 2008-07-09
I will give that a try and see what happens.  Thanks!

---

### Post by achristoffersen on 2009-01-03
maybe this: [http://linux.softpedia.com/get/Multimedia/Audio/Duplicate-Music-Matcher-4889.shtml?](http://linux.softpedia.com/get/Multimedia/Audio/Duplicate-Music-Matcher-4889.shtml?)

---

### Post by ddarkjedie on 2011-05-17
Just do this:

```
cd ~/.config/banshee-1 
```

```
rm banshee.db
```

And then re-scan your music library in Banshee.  Bam, fixed!  

Tested in Banshee 2.0.1

---

