---
title: "Ardour Sound Playback issue"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by twistedoboe on 2011-10-11
So I upgraded my regular Maverick OS to the version for Ubuntu Studio so i didn't have to manually install all the programs with it.  before i did this Ardour worked great, i got nice quality playback and I could do work with Xjadeo since I do audio for videos with it.
Now that the system is updated Ardour loads painfully slowly and plays back all recordings  distorted, almost like there was a pulse to it but not sounding at all like the file should (played in other programs these files sound fine). The sync through JACK to Xjadeo isn't working right either when I start playback the film doesn't move through frames it just stays where is was; when i stop playback it jumps back forward where its supposed to be; this is not how the program is meant to work because I can't see where i am in the film to set music to it if I can't see the moving film!
I've synced Xjadeo with Rosegarden separately and it worked fine meaning the problem is in Ardour and not JACK or Xjadeo. I'm not sure if I configured something wrong or if its a bug.
The Problem isn't processing speed either because it wont even play a 10 second clip without any editing done to it properly.
I've been playing with it for a few days and I'm stumped, any ideas?

---

### Post by twistedoboe on 2011-10-13
Well I solved the playback problem in Ardour, I removed some of the Ubuntu Studio files (not all of them but the main ones that fixed I think were the audio plug-ins)  using terminal then I removed ardour, rebooted and installed ardor again but this time from source to try to make it more stable, Ardour is now running fine, the sync with Xjadeo is still not working properly though, the file will sync but only after stopping playback, i need it to move with my Ardour time-line so i can see that my music lines up with the action in the film... sigh so much frustration, oh well at least I'm not a a total standstill while I figure this one out I can get back to audio work at least :p  Any ideas about Xjadeo anyone?

---

