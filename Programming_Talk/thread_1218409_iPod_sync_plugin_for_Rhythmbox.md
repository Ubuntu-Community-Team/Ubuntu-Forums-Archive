---
title: "iPod sync plugin for Rhythmbox"
date: 2009-07-20
forum: Programming Talk
---

### Post by KingNeil on 2009-07-20
When you install Ubuntu, the default music player is Rhythmbox, and I believe it to be by far the best music player.

However, your average Windows user is used to being able to sync songs to his iPod using iTunes. This means, your library of songs is sent to your iPod, so that your iPod matches it.

There is no functionality to do this in Rhythmbox, and the syncing in Amarok, Songbird etc does not work properly when you have a large number of songs in your library.

Therefore, we clearly need a Rhythmbox plugin that synchronises your iPod. Various attempts have been made, such as [this one]("http://lonnieolson.com/blog/2007/11/16/rhythmbox-ipod-sync-plugin/") and [this one]("http://lonnieolson.com/blog/2008/04/22/updated-rhythmbox-ipod-sync-plugin/"). Both fail.

This is a very simple function to describe in English. You simply look at the library of songs locally, compare it with your iPod's library, and add/remove songs from the iPod as necessary. I can't stress how simple this is, yet it is missing! The people who developed Rhythmbox are easily capable of including this, yet they haven't. This is the sad story of many Ubuntu apps: so sophisticated, but missing a tiny piece of functionality that is key!

We need people with experience writing Rhythmbox plugins to do this.

Or, if you are good with Python, you may well be up to it, too. As I understand it, Rhythmbox plugins can be written in C or Python. I know a bit of Python, but am not up to this. There is a useful guide [here]("http://live.gnome.org/RhythmboxPlugins/WritingGuide#head-7fd5985806ac73cff392fa77027e2432f24bd4da") on how to create Rhythmbox plugins. Check it out, and reply to this thread if you think you can do this -- or if you know someone who could.

---

### Post by dribeas on 2009-07-21
Two way synchronization is not easy to implement correctly. When you have a disagreement (say a file is present in one of the ends and not in the other) you have to make decisions. But that is not, I believe, the hard part.

Apple uses an internal database in the iPod (or at least it did with the 2nd generation iPod I once owned) and you would have to process that format (it was an XML with the songs metadata plus the name of the song file in the disk, that was mangled somehow).

And this again complicates the first point: as the files are not just copied, but renamed and moved to different directory structures and the data added to the database, the test for a song being in the iPod already becomes harder. You would have to compare the metadata present both in the iPod and the music player to determine equality, and then the same song after the user has corrected one of the ID3 fields would not be exactly the same as the song already present in the iPod... 'Compare' is such an easy word to say in english, and at the same time

The point is: it is probably not rocket science, but it is surely not trivial to implement that plugin.

---

