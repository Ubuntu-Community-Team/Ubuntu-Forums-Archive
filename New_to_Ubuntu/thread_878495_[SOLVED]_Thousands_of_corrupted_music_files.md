---
title: "[SOLVED] Thousands of corrupted music files"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-08-03
I built a computer last week and am running 64-bit Ubuntu.  I have two hard drives, both are still rather empty so far.  I installed with just the one, and then I mounted the other one later as a slave drives.  There have been no problems until just now.  I have been uploaded my CDs onto the slave drive, (the mount point for the drive is /stor, music is in /stor/music) and have almost 2,000 songs uploaded.  Or should I say 'had'.

I was just playing Sauerbraten, and it froze on me.  Not really a big deal, but I had to Ctrl+Alt+Backspace out of it (no other programs were open at the time).  When I logged back in, I gnome-opened a music file (which defaults to Totem) and it gave me an error, saying "Failed to connect to stream: Invalid argument".  I opened Banshee, and tried to play a song.  A red circle with a line through it (like a do not enter sign) appeared next to the song, and then appeared next to all the other songs!  Each song name was prepended with "(Unknown error)".  None of them play.  They could have been messed up before this, I hadn't played any music in a few hours.

I have no idea why, unless somehow the entire /stor/music folder got corrupted.  There are other folders in /stor; /stor/programs and /stor/pictures are unaffected, and my programs and pictures remain there.

Everything looks fine in the /stor/music directory, it's just that nothing plays.  'ls -l' shows nothing abnormal, and I don't know any commands that would point me to the error.

It's very frustrating since I just uploaded about 2,000 songs in the last few days, and now none of them work :(.

I am going to buy an external hard drive to back up all my files, especially the music files, but I'd prefer not to have to re-upload all of them to do so.

Any help would be greatly appreciated.

---

### Post by ConMan318 on 2008-08-03
Well I unmounted, restarted, remounted, and they play now.  Quite peculiar.

---

### Post by jordanmthomas on 2008-08-03
It sounds more like an issue with your players not finding the appropriate codecs to play the files.

Maybe you could try downloading some random mp3 off the internet and see if it plays.
[http://www.meditation-power.com/sample.mp3](http://www.meditation-power.com/sample.mp3)  <-- some random mp3

If it doesn't play, then your files are probably fine and you just need to figure out what's up with your players.


edit
nevermind, seems solved.  :)

---

### Post by ConMan318 on 2008-08-03
As I am thinking about it I think it might have had more to do with Sauerbraten than I originally thought.  Whenever I play, I have to quit Banshee or I get no sound.  Maybe the hard logout left it in the Sauerbraten mode of audio (whatever that is, Ubuntu has some quirky sound issues) and it couldn't play other audio files.

Thanks for the response though :p.

I'm definitely going to buy an external and back all of it up tomorrow.

---

