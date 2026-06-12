---
title: "No MIDI -jack audioserver ?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by its_jon on 2008-09-11
The only problem I have with linux at the moment having just migrated from XP is midi....

Found and installed compiz and emerald ... great !
Nvidea drivers - check :)
Envy24 mixer .... yup (working great with audio)

can't seem to find the midi output slider on any mixer.....

When I open a midi it wants to open in sound garden (I write music) which reports the following error

-failed to connect to JACK audio server- 

I then see the midi file appear and soundgarden appears to be processing it perfectly......just no sound ?!
Totem plays my midi but again with no sound.

I can't find anything muted or with the volume all the way down in the mixer....

Any idea's chaps ?

I see lots of midi stuff in synaptic but unsure if I need any of it - if I simply need to enable something already installed ?

help :)

Thanks
John

---

### Post by its_jon on 2008-09-11
Just thought I would bump this post up to a new time zone.... as Ubuntu is such a vast forum, I may catch someone this time.... I wont do it again..:oops:

Thanks in advance for any ideas.
Jon

---

### Post by tonymoloney on 2008-09-11
Have you got Timidity installed?

In a terminal, type timidity -iA -B2,8 -Os1l -s 44100
 
If you get an error here, then you will have to install Timidity. 

I'm sorry, I lost my reference to this procedure, but if you go to the multimedia forum, you should be able to get some specialist advice there.

---

### Post by spiderbatdad on 2008-09-11
I install timidity also, then uninstall it...totem retains the ability to play midis after uninstalling. As a quirk, totem always complains, on closing, after the file has played, that it can't play the file.

---

### Post by its_jon on 2008-09-12
Installed Timidity and now its working ! immediately working

THANKS !

but.... why did my Ubuntu install not have midi playback built in out of the box ?
(just so that I know whats going on) ....thanks

---

### Post by kuric on 2011-01-03
To get sound from Rosegarden (the music editor/maker) I had to uninstall Jack2 and install Timidity.

---

