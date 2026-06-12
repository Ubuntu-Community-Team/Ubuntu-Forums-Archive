---
title: "How to detect and remove automatically silences into an mp3 file?"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by honeybear on 2013-05-16
Hi,

I have made an audio recording, but I would like to process the mp3 file,
and ask Ubuntu to remove automatically the silences (when there is no noise at all, sort of no noise
background removal).

Would you know please how it can be done, preferably by a command line?

I know that you can remove the silences, or cut an mp3. that I know of course.

The question is how to do that automatically 

thanks

---

### Post by sudodus on 2013-05-16
***Audacity*** is a good tool for audio editing. It has a learning curve, but is very powerful.

It has a GUI, and I have not used it in automatic mode (maybe it is possible).

Good luck :-)

---

### Post by honeybear on 2013-05-16
as indicated into my first post, it is not possible (automatically )

---

### Post by tgalati4 on 2013-05-16
You can use *audacity* to find and mark silent passages.  That will create a text file based on time of each silent span.  Then you can use *sox* or  *audacity*  to remove the dead spaces between the vocal portions.  A simple google search on* audacity silence removal* brings up these links:

[http://audacity.238276.n2.nabble.com/remove-silences-td293043.html](http://audacity.238276.n2.nabble.com/remove-silences-td293043.html)

[http://theaudacitytopodcast.com/tap070-how-to-use-truncate-silence-and-sound-smarter-with-audacity/](http://theaudacitytopodcast.com/tap070-how-to-use-truncate-silence-and-sound-smarter-with-audacity/)

[http://forum.audacityteam.org/viewtopic.php?f=11&t=8150](http://forum.audacityteam.org/viewtopic.php?f=11&t=8150)

Once you have practiced doing it manually a few times, make a detailed list of procedures and try your hand at writing a script to perform the operation.  There may be a script out there already.

---

### Post by Cheesemill on 2013-05-16
You should be able to do the whole thing just using sox. I've not tried it myself but Google threw up some promising looking hits...

[https://www.google.co.uk/search?q=audio+silence+removal+sox](https://www.google.co.uk/search?q=audio+silence+removal+sox)

---

### Post by Devta on 2013-05-16
Try splitting by using silence detection in mp3splt and joining using MP3Wrap.

---

