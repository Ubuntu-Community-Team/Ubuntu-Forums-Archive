---
title: "No sound"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by Bob_Dennis on 2013-12-27
I had sound about a month ago and it disappeared.  Sound card is OK--I am running Ubuntu Studio (Precise) dual boot with Windows 7, and sound is fine in Windows.  

No sound in:  Audacious; Web sites such as YouTube; Rosegarden (that would be synthesized Midi).  I don't remember hearing any system sounds either.

What I've done:  Search for mixers that might have turned sound off, tried running and not running a variety of sound software.  One thing I noticed:  When there is a started Jack Studio, Audacious doesn't play an MP3 file.  When there is no Jack studio, or there is one but it is stopped, Audacious appears to play--the progress indicator moves, as does the display in the bottom RH corner.  But still no sound.  

I'm not sure whether I should be using a Jack studio for anything other than Midi work.

Other posters with sound probles have been asked to run an Alsa script.  I've done that, and the result is at [http://www.alsa-project.org/db/?f=0fa959d4ca81da1d4e73b82683fd1207ac07e0b](http://www.alsa-project.org/db/?f=0fa959d4ca81da1d4e73b82683fd1207ac07e0b).

I'd be very grateful for any help.  Fishing around empirically doesn't seem to cut it.

---

### Post by Bob_Dennis on 2013-12-27
I had sound about a month ago and it disappeared.  Sound card is OK--I am running Ubuntu Studio (Precise) dual boot with Windows 7, and sound is fine in Windows.  

No sound in:  Audacious; Web sites such as YouTube; Rosegarden (that would be synthesized Midi).  I don't remember hearing any system sounds either.

What I've done:  Search for mixers that might have turned sound off, tried running and not running a variety of sound software.  One thing I noticed:  When there is a started Jack Studio, Audacious doesn't play an MP3 file.  When there is no Jack studio, or there is one but it is stopped, Audacious appears to play--the progress indicator moves, as does the display in the bottom RH corner.  But still no sound.  

I'm not sure whether I should be using a Jack studio for anything other than Midi work.

Other posters with sound probles have been asked to run an Alsa script.  I've done that, and the result is at [http://www.alsa-project.org/db/?f=0fa959d4ca81da1d4e73b82683fd1207ac07e0b](http://www.alsa-project.org/db/?f=0fa959d4ca81da1d4e73b82683fd1207ac07e0b).

I'd be very grateful for any help.  Fishing around empirically doesn't seem to cut it.

A little further info:  I'm trying to follow the instructions at [https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections).  The Jack "Connections" window does not show any of the clients  shown in those instructions.  Instead the readable clients are "PulseAudio Jack Sink" and "system"; writeable clients are "PulseAudio Jack Source" and "system".  They are cross-connected; ie the two Pulse-Audio clients are each connected to the system client in the other pane.  This seems wrong but I don't see how to change it.

---

### Post by de Bacon on 2013-12-27
Are you aware the shutting down jack without turning it off first, leaves it running in the background.   I am guessing here, but if you've shut it down, without turning it off, it could be locking up your main alsa audio system.

Like I said, i'm just guessing.
Regards

---

### Post by f2010185 on 2013-12-27
try running this sudo alsa force-reload. it worked for me. or you  edit the speech-dispatcher file.
sudo vi /etc/default/speech-dispatcher and change RUN=NO

---

### Post by ajgreeny on 2013-12-27
So, is this query solved or not?

There seems to be a question in your post, but you have also added the "Solved" flag to it.

---

### Post by Bob_Dennis on 2013-12-27
Thanks to both of you, but suggestions didn't work.  I closed Jack in the sequence de Bacon said, and I tried the force-reload suggested by f2010185: appeared to do it but still no sound.  The second command wasn't recognized.  Maybe I have the command on another path but i don't know enough Linux to find it.

---

### Post by mörgæs on 2013-12-27
Please stop multiposting. 
Merged.

---

### Post by Bob_Dennis on 2013-12-29
Sorry, Morgaes,  duplicate post was inadvertent.  This thread is unsolved however.

---

