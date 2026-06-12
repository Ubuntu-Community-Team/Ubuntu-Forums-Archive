---
title: "Resurrecting my iTunes playlists on Rhythmbox, no dual-boot"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by Commanche1 on 2012-04-29
I'm a new ubuntu user. I've installed 12.04 onto a clean desktop (no dual-booting) and am trying to retrieve my iTunes playlists off my old/dying Win XP laptop. iTunes crashed on the laptop long ago and will no longer run w/o being reinstalled.

The song files themselves were on an external HD (named E:\ on the old laptop), which has nearly crashed as well ("failure imminent" as the diagnostics say), tho I've been lucky enough to transfer its full contents to my new machine before it's completely dead.

I've also been able to salvage the iTunes Library files, in both .itl and .xml formats. I've managed to rewrite a copy of the iTunes xml as a Rhythmbox library database, via [http://www.njamin.org/blog/tutorials/import-itunes-library-into-rhythmbox-ratings-and-playcounts-included-121.php](http://www.njamin.org/blog/tutorials/import-itunes-library-into-rhythmbox-ratings-and-playcounts-included-121.php)

So here's my question...

Can I somehow point Rhythmbox to the new location of the song files, so it can then recreate the playlists I had on my old system?

They original filepaths for the entire library have been preserved, except for the all-important E:/. Seems like all the right pieces are there, they just won't fall into place!

---

### Post by oboedad55 on 2012-04-29
> **Commanche1 said:**
> I'm a new ubuntu user. I've installed 12.04 onto a clean desktop (no dual-booting) and am trying to retrieve my iTunes playlists off my old/dying Win XP laptop. iTunes crashed on the laptop long ago and will no longer run w/o being reinstalled.

The song files themselves were on an external HD (named E:\ on the old laptop), which has nearly crashed as well ("failure imminent" as the diagnostics say), tho I've been lucky enough to transfer its full contents to my new machine before it's completely dead.

I've also been able to salvage the iTunes Library files, in both .itl and .xml formats. I've managed to rewrite a copy of the iTunes xml as a Rhythmbox library database, via [http://www.njamin.org/blog/tutorials/import-itunes-library-into-rhythmbox-ratings-and-playcounts-included-121.php](http://www.njamin.org/blog/tutorials/import-itunes-library-into-rhythmbox-ratings-and-playcounts-included-121.php)

So here's my question...

Can I somehow point Rhythmbox to the new location of the song files, so it can then recreate the playlists I had on my old system?

They original filepaths for the entire library have been preserved, except for the all-important E:/. Seems like all the right pieces are there, they just won't fall into place!

I don't think the iTunes file will do you any good. When I use Rhythmbox or Banshee and add music to my iPod it shows up as before when using iTunes.

---

### Post by Commanche1 on 2012-05-03
Thx, oboedad55, looking more and more like you're right. I suppose part  of the ubuntu learning process is learning to "let go and start over."

---

### Post by oboedad55 on 2012-05-03
> **Commanche1 said:**
> Thx, oboedad55, looking more and more like you're right. I suppose part  of the ubuntu learning process is learning to "let go and start over."

Sure thing, let us know how you come out. I've been running Linux a long time so I'm used to it, but it's sometimes confusing making the transition from Windows. You're used to scouring the Internet to find programs, fight with anti-virus programs and so on. With Linux it's extremely rare to have to do any of that. All the programs are in the repos and there is generally no need to fret about viruses and malware. Have fun!

---

### Post by helotbc on 2012-06-05
My situation is that I have copied the iTunes files/folders from an old Mac HD to my Ubuntu system.  I expect to be able to use the Rhythmbox File>Import Folder command to import the music, but that doesn't seem to be the case.  Any thoughts would be appreciated.  -Brendan

---

### Post by oboedad55 on 2012-06-05
> **helotbc said:**
> My situation is that I have copied the iTunes files/folders from an old Mac HD to my Ubuntu system.  I expect to be able to use the Rhythmbox File>Import Folder command to import the music, but that doesn't seem to be the case.  Any thoughts would be appreciated.  -Brendan

Are these music files? If so, what format are they in? In Banshee I just drag and drop albums from Banshee to the iPod. I believe Rhythmbox is the same.

---

### Post by helotbc on 2012-06-05
> **oboedad55 said:**
> Are these music files? If so, what format are they in? In Banshee I just drag and drop albums from Banshee to the iPod. I believe Rhythmbox is the same.

They're .m4p's.  My issue is not getting the files from Rhythmbox to the device, it's getting the files to be recognized by Rhythmbox.  I've copied the folders/files into my ~/Music directory, where RB keeps its repository.  I guess I need to know how to rebuild the RB database to include these files in the UI.

---

### Post by helotbc on 2012-06-06
I uninstalled/reinstalled Rhythmbox.  No change.  I installed Banshee.  It scanned my hd and found all the music files, old and new.  

Correction:  the new files are of type .m4p.  The old files are .m4a.  I think that's my issue.  Now I either need to get the players to play m4p or convert the files.  Thx.

---

