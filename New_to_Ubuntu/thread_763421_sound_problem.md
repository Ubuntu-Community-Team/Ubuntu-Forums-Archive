---
title: "sound problem"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by corbett_1989 on 2008-04-23
I know this has been talked to death about but I'm ripping my hair out on this. I've tried everything..either I get a permission denied or insert disk that I don't have...now I can listen to music just fine and what not but if i want to listen to videos on the web or on my hard drive it just won't go...i'm running my sound through the standard C-Media Superior Quality Audio 7.1 channel CODEC on the motherboard if the name matters or not. Please be kind I am new with Linux so have some patience with me...Thanks in advance

---

### Post by subzero316 on 2008-04-23
You need 2 phrase your question better.you say  u can listen 2 music just fine .but cant on hard drive:confused::confused:
.Be specific

---

### Post by pellgarlic on 2008-04-23
corbett_1989 - it sounds like you are having a problem with a particular program? if your music plays fine (probably in rhythmbox) but videos dont have any sound (probably in totem player) then it could be to do with the particular program you are trying to use...

let us know which programs your music and videos open in. (if you are not sure, you can usually find out by clicking on the "help" menu of the program, then selecting the "about" option - it will usually tell you what the program is).

---

### Post by corbett_1989 on 2008-04-23
Well for my music I'm using Amarok and like I said it works just fine....I'm using Totem Movie Player 2.20.0 for the videos on the hard drive ...I'm using Firefox for my internet videos as well but I'm still not getting any sound from the movies on the internet so I figured it was a codec problem, but I thought I downloaded all the codec's I'll need.

---

### Post by pellgarlic on 2008-04-24
it seems likely that gstreamer is the issue here - i've been using linux for a few years now, and i still find the way it deals with audio confusing sometimes, but basically, there are different "audio systems" which can handle the audio requests that programs like amarok and totem make, and one of them is "esd", which is the default system activated for system sounds in ubuntu. it causes some kind of conflict with gstreamer (which totem uses to play sound). disabling system sounds, and changing from "esd" to "alsa" can help. 

(see this post for a more concise explanation: [http://www.bgevolution.com/blog/index.php/gstreamer-alsa-conflict-no-sound-totem-or-system/](http://www.bgevolution.com/blog/index.php/gstreamer-alsa-conflict-no-sound-totem-or-system/))

by the way, a good tip for trying to diagnose problems with programs, is to run them from - the terminal, i.e. - open "gnome-terminal", then type "totem" and press enter. this will run totem video player, and sould give you some text output in the terminal (sometimes you can add a "-v" argument to make the output of a program more verbose). this text can often help to figure out problems like this. maybe you could try that, and post any interesting errors or messages you see?...

---

