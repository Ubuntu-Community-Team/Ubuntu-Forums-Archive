---
title: "sound not as crisp and loud and video"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by misswham on 2008-09-08
I am dual booting xp and ubuntu.  When I listen to music or watch movies the sound isnt as crisp and loud as it is in windows.  I used VLC media player as a default because that is the one i like but it is the same with the other media players also.  How can I make it louder and more crisp like in windows?  Also, when I view pics or video the picture also is more Crisp in windows.

---

### Post by kpkeerthi on 2008-09-08
Open a terminal and type **alsamixer**

Look for the channel marked **Master** and **PCM** and adjust the volume. To avoid interference, you may want to mute the channel marked **Mic**

Use arrow keys to navigate and adjust volume
Press 'm' to toggle mute
Press 'Esc' to quit alsamixer

---

### Post by misswham on 2008-09-08
I did that and the first few controls were at 100% the last one which was front was at 80 so I moved that one up also.  Now the problem I am having is when I first installed ubuntu, I could get sound from my personal files but couldnt get sound from youtube.  Then I had a brainstorm after 2 weeks of tech assistance here, was to put another pair of speakers in the jack in the rear of the pc and bamn the streaming video sound came from the rear.  So from that point on the sound from my files like movies and music came from my bose speakers which were connected to the jack in the front and the youtube sounds came from the computer speakers connected in the back.  Now yesterday when I logged on the sound didnt come from the front.  I rebooted and it was back the way it was at first.  Now today it is the opposite.  How can I make it all come from one jack consitently?

---

