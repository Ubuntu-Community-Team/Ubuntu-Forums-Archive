---
title: "Speaker issue"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by moon2 on 2014-05-16
Morning All ):P

I am running Ubuntu 14.04 LTS on a custom made desktop - although I can get sound, it only comes out of one speaker, not both.  The speakers are Dell A215s and worked fine when running XP.  The setting I can see for what I assume is the sound card is sb live 24 bit analogue (not sure as I'm very new to finding out all this stuff).

When I ran Windows if you had issues you would just check for a new driver and install it and usually that cured most problems.

Do you do that Ubuntu?  If so how?  Really simple answers please as I really am very new to all this stuff.

Thanks
Moon

---

### Post by m-dw on 2014-05-16
Linux (and Ubuntu in particular) generally comes with working drivers for most hardware, so no need to go looking for a newer one yet.  Firstly, check under "sound settings" (click the volume control in the panel notification area) to make sure your audio isn't faded all the way to the left.  You could also install gnome-alsamixer, which has more setitngs.  I also found this thread:
[http://ubuntuforums.org/showthread.php?t=161817](http://ubuntuforums.org/showthread.php?t=161817)

Also don't rule out the obvious.  I had a similar problem after I upgraded to 14.04 which took me ages to resolve.  I couldn't get sound out of either the centre speaker or subwoofer of my Altec Lansing 5.1 setup.  I eventually remembered that I'd switched it into 2/4 speaker input mode as I'm using it as an external amplifier for a hardware media player.  Check that the speaker jack is inserted correctly.intothe sound card.

---

### Post by moon2 on 2014-05-16
Hi

Thanks for your reply - volume is on 100%
When I run Alsa is comes up with: An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly - when I click on details there's nothing there.
I've checked all the plugs and everything seems to be well plugged in and still only getting sound out of one speaker.
I've tried looking at various posts using google and I can't see any answers.

Cheers
Moon

---

### Post by m-dw on 2014-05-16
Alsamixer may not have been the best mixer application to suggest (as Ubuntu runs PulseAudio).

Install pavumeter (Pulse Audio Volume Meter) if it isn't already installed.  Run it while using the "Test Audio" applet which is available from:[INDENT]System settings -> Sound -> Test sound[/INDENT]

When you test the quiet speaker, does paumeter show any activity?

Also, if the sound card is working properly you should have a slider for Left/Right balance (assuming stereo) on the System Settings -> sound page.  Do you have that?

Another place to look is in the PulseAudio Volume control (pavucontrol) and check that one of the channels isn't muted.

---

### Post by rook3 on 2014-05-16
Howdy :) First time here, which says something about Ubuntu's(Lubuntu in this case) useability so far. Is there some netiquette about posting on threads when you have the same issue?

---

### Post by moon2 on 2014-05-21
Morning All :) - I have resolved the issue - nothing to do with Ubuntu - I removed the microphone and speaker plugs from the sound card and plugged them into something else - assume the motherboard - which has inbuilt audio settings and this works - I now have both speakers and the microphone works too - oh the wonders of modern technology!!!

Rook3 - I don't think there's any netiquette as long as it's relevant :)

Thanks for all your suggestions.

Regards
Moon

---

### Post by grahammechanical on 2014-05-21
What value does a "me too" comment give to discussion? Except to increase the length of the thread. 

On the other hand your fix is something that I shall look into because I have struggled with this problem myself. In fact when you first posted this problem I spent a lot of time trying to find a fix and I ran out of ideas. I would not have noticed your solution except for you marking the thread as solved. At lot of people do not do that.

One form of "bad manners" is to ask about a different problem instead of starting a new thread. It is not easy trying to help with two different problems in the same thread.

Regards.

---

