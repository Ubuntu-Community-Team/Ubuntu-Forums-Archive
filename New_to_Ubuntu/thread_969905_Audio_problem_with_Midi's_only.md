---
title: "Audio problem with Midi's only?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-03
Hi Gang

I followed all the directions for fixing audio, but audio worked for everything except midi files.  Works better after making all the changes, but midi still don't work.  The Apple Movie Trailers all work fine from the test here area, but none of those are midi's.

Here is what happens with midi's, they Cache Fill: to only 0.46%+- and stop.
Then the word STOPPED comes up.

I've tried disabling extensions and the like, makes no difference, everything except midi's seems to work OK, including movies.

I've already worked with MozillaZine guru's, since everything else works, it has to do with some package from here.  like Ubuntu Firefox Modifications 0.5, however, with it enable or disabled, I see no difference, the places the work, work and those with midi's don't.

I have M-player and Gecko Mediaplayer and the gecko media player plug-in.

So I'm lost here gang!

TTUL
Gary

---

### Post by quibbler on 2008-11-04
Try Timidity, you can find it in Synaptic.

Regards quibbler

---

### Post by Kellemora on 2008-11-08
Hi Quib

Thanks for the shot!  
I downloaded and installed it, but can't find it.
It didn't come up in the list of available players for some reason.

My problem so far is that no matter what player I try to use, it won't cache, stops at 0.46% on the midi file I'm using for testing.

TTUL
Gary

---

### Post by Kellemora on 2008-11-18
Still looking for some advice to get midi files to play in Firefox without getting Cache Fill and STOPPED problems!

Saying mine works is NOT a solution to the problem!

TTUL
Gary

---

### Post by nothingspecial on 2008-11-18
[http://ubuntuforums.org/showthread.php?t=778552](http://ubuntuforums.org/showthread.php?t=778552)

---

### Post by SunnyRabbiera on 2008-11-18
> **Kellemora said:**
> Hi Quib

Thanks for the shot!  
I downloaded and installed it, but can't find it.
It didn't come up in the list of available players for some reason.

My problem so far is that no matter what player I try to use, it won't cache, stops at 0.46% on the midi file I'm using for testing.

TTUL
Gary

Timidity is actually a command line application so it wont be in your menu's.
Actually for a graphical front end for midi there is kmid, it will get the job done but it will stand out as its not a gtk application.

---

### Post by Kellemora on 2008-11-18
Thanks guys!

I guess this 3rd post on the matter wasn't as specific as the first one.

I'm using FIREFOX and NO midi file will play.  CacheFill stops at 0.46% on midi's, all other files play perfectly.

I worked with the Mozilla team for 2 weeks and they are pointing their finger at the Ubuntu Firefox Modifications 0.5 package as being the problem.  But with it disabled, problem still exists.

Others who have responded just say, theirs works fine!

I have Ubuntu on 5 different computers here, and midi's do not play on ANY of them!  And we have uninstalled, reinstalled, tried many different packages.  They all work for everything except midi files.
Those that offer a way to increase the cache size, increasing the cache to 10 times it's size causes the cache fill to drop down to 0.10% not go up as one would expect.

I can watch streaming video, 2 hour movies, mp3, but not listen to a tiny midi file from any source.

TTUL
Gary

---

### Post by Kellemora on 2009-01-09
Bump

---

### Post by Kellemora on 2009-02-14
Hi Gang

FWIW:  I FINALLY SOLVED the problem on all 6 of our computers, including the newest 64 bit machine..........

The problem had absolutely NOTHING to do with Firefox!

And once we removed the offending program, midi's will now play direct from Firefox (when it hit's midi's that is) via any one of several players you can select.  I chose Totem (which would NOT WORK when the offending program was installed, and neither would Timidity by the way.)

The BAD BOY causing all of these problems since late August of 2008 when I first began installing Ubuntu on our computers is none other than GNOME Media Player, which is the Gecko Media Player!

Two IT guru's spent 4 and 6 hours here respectively and never figured out the problem either, so it's not surprising the folks at Mozillazine, Gnome or Launchpad could figure it out either.

Doing a Complete Removal of the Gnome Media Player allows Firefox to (with Mozplugger) to find and use Totem or many other players!

TTUL
Gary

---

