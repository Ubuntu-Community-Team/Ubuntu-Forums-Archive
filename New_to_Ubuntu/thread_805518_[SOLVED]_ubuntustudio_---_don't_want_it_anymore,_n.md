---
title: "[SOLVED] ubuntustudio --- don't want it anymore, now what do I do?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by raequin on 2008-05-24
This is with regards to a Hardy Heron system.

I installed Hydrogen in order to create an instrumental version of a song.  I opened the mp3 to listen to the song, prior to opening Hydrogen.  Then I started working in Hydrogen.  I created a beat, but nothing happened when I went to play it, ditto with the demo files in Hydrogen.

I thought maybe something was missing in my install, so I installed ubuntustudio with:

sudo apt-get install ubuntustudio*

Turns out the problem was that I can not play an mp3, leave that program open, and then open Hydrogen and play a song in it.  The reverse is true too.  I can play one or the other, but not both.  If I open Hydrogen first then I can play the Hydrogen file, but not the mp3 until I close Hydrogen, and visa versa.

Anyway, I had no idea what ubuntustudio was.  I did not know that it was a whole theme and a huge suite of software.  I do not want it.  I want to go back to my old setup.  How can I do that?

---

### Post by alienexplorers on 2008-05-24
You could try:
> sudo apt-get remove ubuntustudio*

Next time you load something use aptitude instead.  It makes it a lot easier to remove files and dependencies when you don't want to use that software anymore.

---

### Post by raequin on 2008-05-24
I followed your instructions.  It returned the appearance of my system.  The applications are all still here.  I guess I can just remove those individually using Applications -> add/remove.

Thanks.

---

