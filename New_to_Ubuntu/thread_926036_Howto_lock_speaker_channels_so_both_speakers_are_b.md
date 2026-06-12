---
title: "Howto lock speaker channels so both speakers are balanced"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-09-21
Hi Ubuntu Community:

I had some trouble getting my speaker channels to be balanced and found other threads on the forums... others have had this problem, also. See:

[http://ubuntuforums.org/showthread.php?t=250140]("http://ubuntuforums.org/showthread.php?t=250140")

and

[http://ubuntuforums.org/showthread.php?t=250140]("http://ubuntuforums.org/showthread.php?t=250140").

Here is what has worked for me. Readers should be aware that I have an external sound card with the internal sound card disabled (see: [http://ubuntuforums.org/showthread.php?t=921980]("http://ubuntuforums.org/showthread.php?t=921980")). 

So what worked for me may be only suggestive for readers that have internal sound cards enabled with no external sound card. I think you'll see what could work, however, so here is my post:


1)DOUBLE click on the sound icon (for me this is the Gnome/Gstreamer Volume Control that is an icon on my upper panel. **For Gnome users: to add this icon, right click on your upper panel > + to panel > volume control > + ADD**)

2)file > change device ... make sure some sort of playback button is active. For me, it was “playback ALSA on front:2" is active... probably because of my external sound card.

4)click on the chain link to “lock” the 2 channels

Now, with all of this said, expect this to NOT be a permanent solution for some reason. In my case, when I use the gnome volume control (SINGLE click on the volume control icon and use the slider bar) to adjust volume, it unlocks the channels.

However, when I use the gnome control and DOUBLE click on the speaker icon sign, and adjust the MASTER volume in the pop-up window) the speakers remain locked and balanced.

I realized that alot of other people have had this problem... there were lots of "views" on the above cited links with no really good solutions that I could find.

I can't claim that my suggestions here will be the final word, or even correct for most people, but it is a starting place.

I'm using Hardy.

Best regards,
Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2008-09-21
Ubuntu Community:

One more thing:

If you want to "fine tune" your balance:

1) in a terminal window type "kmix" This will bring up the KDE mixer. (add using synaptic if you don't have it.)

2) choose: settings > dock to panel > apply > ok (if you want this in your upper panel).

3) If you followed 2), then click on the teal blue speaker icon that is now in your upper panel. 

4) the slider bar seems to control the volume of both speakers without unlocking the balance adjustment described in my post above. 

5) to fine tune your balance, click on the teal speaker icon > mixer . On the bottom of mine I see a slider bar to adjust the right and left balance. ALso, becuase my sound card is an external USB sound card, it says "USB audio codec" to the right of that balance slider bar.

Hope this helps.

Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2008-09-21
**For really improved sound quality**, disable that onboard sound card and install an improved sound card.

Select your soundcard after reviewing the community page on sound cards that:

1) are autodetect, and

2) works according to the documentation at [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards")

See the thread: [http://ubuntuforums.org/showthread.php?t=921980]("http://ubuntuforums.org/showthread.php?t=921980") to see how I disabled my sound card and the posts listed above.

Your onboard sound card make work, but even a $39 external USB sound card will give **DRAMATICALLY IMPROVED SOUND**.

Best regards,
Phil Smith
Duluth, GA

---

### Post by markbuntu on 2008-09-21
There is no need to disable your on board sound card to use a different one, all you need to do is change the default and if you are using pulseaudio, you can change the default alsa sound to pulseaudio and use them both. That's what I do:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by Old Jimma on 2008-09-21
Thank you, Markbuntu! 

Readers, please review Mark's post and follow the links.

Phl

---

### Post by markbuntu on 2008-09-21
Hey Phil. Don't PM me.

---

