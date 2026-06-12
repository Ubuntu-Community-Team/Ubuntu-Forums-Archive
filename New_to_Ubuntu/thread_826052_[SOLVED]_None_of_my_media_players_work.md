---
title: "[SOLVED] None of my media players work"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by AOZ on 2008-06-11
Iv never had this problem up until today when i installed banshee-1. banshee worked perfectly until i restarted my computer. now it doesn't play anything. when i press play the pause sign comes up but the slider stays at the start of the song. i installed rhythmbox again and now that doesnt work either. I'm pretty sure I've got all the codecs or ti wouldn't have worked before. Anyone know of this bug? any help would be appreciated

---

### Post by sdennie on 2008-06-11
Do you have your sound muted?

(This sounds simplistic but, it's best to start simple)

---

### Post by AOZ on 2008-06-11
haha no i dont. when i listen to music online or watch youtube the sound works fine. The wierd thing about rhythmbox/banshee/vlc is that it thinks its playing but the song stays at 0:00. and this just happened out of the blue. i might have downloaded some package that screwed everythign up i guess. i was hoping this was a somewhat common bug..

---

### Post by moore.bryan on 2008-06-11
can you check the output? i had this problem a while back with audacious and it was because no "output plugin" was selected in the preferences. setting it to alsa and/or oss might make it "miraculously" work...

---

### Post by Metaleks on 2008-06-11
What format is the music you're trying to play?  To be safe, go into your Add/Remove menu and install GStreamer extra plugins, GStreamer plugins for aac..., and anything else you might think you're going to need.  Then try running Banshee again.

(Make sure to select "All Available Applications" or nothing will appear.)

---

### Post by sdennie on 2008-06-11
That's fairly odd because vlc and Rythmbox don't share the same codecs.  What happens if you go to System->Preferences->Sounds and change some of the options from whatever they are currently set at to ALSA (or possibly Pulse Audio).  Does Rythmbox work after that?

---

### Post by AOZ on 2008-06-11
i installed all the Gstreamer plugins and none of that did anythign. i couldnt find any output option in preferences for banshee or rhythmbox. heres a screenshot of what i look at when i play music. notice that the pause thign is up, menaing it should eb playign but the time slider stays at zero for ever

---

### Post by AOZ on 2008-06-11
wow thank vor i had my settings set to autodetect and i set them to also and now eveyrhtign works. but i dont really undertsand why because youtube worked so did music on myspace and stuff but rhythmbox/banshee/vlc didnt. well watevr it is its workign now thanks alot guys

---

### Post by _sphinx_ on 2008-06-11
Is totem(the defalut player) able to play your audio file??

---

### Post by wildcat1961 on 2008-08-03
If I may piggyback on this question....
I have the same problem as this fellow has... or rather had.   I tried the solutions presented by the previous posters but still no luck.
Curiously, when I sign out and sign back in, the player works.  Otherwise Banshee thinks its playing, but the 'slider' doesn't move and no sound comes out.
I also have Amarok instlaled, and it works perfectly.  All other system sounds work as well. 
Thanks for any help in advance.

---

