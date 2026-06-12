---
title: "No Sound In Flash Movies"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Skeet on 2008-05-25
I am trying to view flash movies online (YouTube etc). I get the image, but no sound. Why is this happening? I have the latest Flash Player from Adobe.

---

### Post by bikeboy on 2008-05-25
What method did you use to install flash? ie. did you install from the repositories or from the Adobe site?

---

### Post by Skeet on 2008-05-25
I installed using Mozilla, when I tried to play a movie it popped up at the top of the window asking what I wanted to install. I selected Adobe Flash Player and it installed fine. Mozilla reopened and I got video but no sound.

---

### Post by bikeboy on 2008-05-25
I can't remember how that method works behind the scenes. You could try opening up Synaptic and looking for [i]flashplugin-nonfree[/i/], that's what should be installed.

Also, try the different options under System > Preferences > Sounds. In particular, look at 'Sound Playback' under 'Music and Movies'. You might have success with ALSA rather than Pulseaudio, thougb Pulse works for me.

---

### Post by Chr0mis on 2008-05-25
Does the sound work for you in rhytmbox or amarok? And have you turned off all the other applications that make sound? 

Have you tried installing libflashsupport? 

Have you tried the solutions mentioned in the following threads? [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
[http://ubuntuforums.org/showthread.php?t=710641](http://ubuntuforums.org/showthread.php?t=710641)
[http://ubuntuforums.org/showthread.php?t=802564](http://ubuntuforums.org/showthread.php?t=802564)

---

### Post by Skeet on 2008-05-25
I did

```

sudo apt-get install libflashsupport

```

And it fixed it, cheers alot.

---

### Post by Skeet on 2008-05-25
I get random crashes while its trying to play the movie now, but I do get sound when its not busy crashing. Whats causing this?

---

### Post by titico on 2008-05-25
Do'nt know.
Try to re-install the app. 
and be sure every time you are about to watch a video, to close all musice applications.

---

### Post by bikeboy on 2008-05-26
libflashsupport caused it in all likelihood. The reason I didn't suggest installing it is the reports of instability when it's used. Late in the Hardy dev cycle, libflashsupport was removed as a dependency of flash for this very reason, it still needs work.

---

### Post by lostlinuxkiwi on 2008-05-26
Do you use XMMS? I had this problem a while ago and found that xmms was taking total control of my sound card making it unavailable for any other applications including flash videos in firefox. I stopped using XMMS.

---

