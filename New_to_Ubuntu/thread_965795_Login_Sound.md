---
title: "Login Sound"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by airencracken on 2008-10-31
Ibex specific.

I disabled it, and yet, it still plays when I log in. Thoughts? Suggestions?

---

### Post by diablo75 on 2008-10-31
Not sure why it would continue to play...

What happens if you tell it to play a different sound?  Will it play that new sound instead of the old one?  (by the way, nice avatar :)

---

### Post by Keen101 on 2008-10-31
interesting. I have the opposite problem. I have the startup sound enabled, but it doesent play at startup. It doesn't really matter though. I can manually play it. Ibex also.

---

### Post by airencracken on 2008-10-31
> **diablo75 said:**
> Not sure why it would continue to play...

What happens if you tell it to play a different sound?  Will it play that new sound instead of the old one?  (by the way, nice avatar :)

I haven't tested that. Good suggestion. Yeah, I don't know why it would continue to play either. The lappy has the same problem.

Thanks! I'm a huge NIN fan. :D

---

### Post by ebazz on 2008-11-03
Hello,
I just upgraded to Ibex and my startup notification won't play.
Everything else works. I disabled my mother board sound card and no change.
I can play the startup tune within the settings screen but thats all.

Can someone help with this? I find it strange that the log off tune plays but the startup won't.

Thank you.
[email]ebazz@yahoo.com[/email]

---

### Post by dtgolder on 2008-11-03
Agreed...can't seem to change the sound preference for any custom sounds...was able to install the sound theme from medibuntu but things like mail notification, error sounds, etc. that can be customized don't save any changed settings.

Also--now that I've played with the sounds, my "empty trash" papercrinkle sound is no longer working.

This all worked fine in Hardy--and I did a full clean install in Ibex (wiped the drive clean).

Anyone have any ideas?

---

### Post by shifty_powers on 2008-11-03
strangely enough, my start-up sound in kubuntu 8.10 is very erratic. it never plays the ful sound. sometimes i barely get the first second...

---

### Post by dtgolder on 2008-11-03
More info...

If I change a sound from a theme (say the "minimize window" sound) from "Default" to anything else...

I can click the little play arrow and the sound will play--BUT--

It doesn't work with the appropriate action (so when you minimize a window, there is no sound).

AND--it breaks the other sounds--so that by changing a sound from a default to anything else means I no longer have a log-in (or any other system) sound.

Changing the theme drop down in "Preferences>Sound" resets they system sound.

So essentially the net result is that I can have a theme log-in sound (but no other sounds--even if included in the theme (like the log-out sound).

Any ideas? Driving me nuts...have deleted/reinstalled alsa, and pulseaudio, with no help.

Again, fresh Intrepid Ibex install (not an upgrade)...and used to work in Hardy.

----------------------

Looks like it's a bug in Intrepid:

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

Add this:
deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main

to your "third-party" Software Sources (System>Software Sources), and it will show up as an update in update manager. Install that, and it SHOULD be set (for the most part).

(Note: this fix screwed up my conky startup, and I had to delay the start as per here:

To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

gedit .conky_start.sh

copy the code below and past into the file. Save and close

#!/bin/bash
sleep 10 && conky;

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Not using beryl so I changed it to sleep 2 && conky; Make sure the script is executable:

chmod a+x .conky_start.sh

Now, add it to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/>your user name/.conky_start.sh)

Not sure why the sound fix would alter the display but adding it in just in case it helps someone else out.

---

