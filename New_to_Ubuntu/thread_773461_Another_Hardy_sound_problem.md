---
title: "Another Hardy sound problem"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Ken Jannot on 2008-04-28
Hi folks. I seem to have cleared up all my Hardy installation problems except for one: I have no sound whatsoever. The little speaker icon has a mute symbol on it, and when I click on it, I get the message, "No volume control GStreamer plugins and/or devices found."

I tried reinstalling GStreamer apps through Synaptic, but that seems not to have changed anything. Any ideas?

---

### Post by Ken Jannot on 2008-04-29
Problem solved. I used the Sound Troubleshooting guide. Had to go through and recompile my drivers, but that was successful. Now I am greeted by the familiar drumbeat and Ubuntu music when I log on!

:guitar:

---

### Post by dragonspitfire0 on 2008-05-28
Can u plz explain more .. because it seems like i have the same issue and i cant even find a sound trouble shooting ..

---

### Post by bark50 on 2008-05-28
Dragonspitfire, maybe Ken was referring to this:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I recently lost my sound after an upgrade, and the instructions in the link helped me get it back.  Essentially, this is what I did:

(1)Go to Applications &#8594; Accessories &#8594; Terminal
(2)Copy and paste into the terminal the command "find /lib/modules/`uname -r` | grep snd"  without the quotes. 
(3)This got me nothing which, I guess, is what it's supposed to do.  If you get some sort of results, I'm not sure if you should or shouldn't go to the next step.
(4)Assuming you've gotten this far, copy and paste into the terminal &#8220;sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic&#8221;  Again, do this without the quotes.
(5) Restart the pc and my sound was back.

Disclaimer:  This worked for me and hasn't screwed anything else up in my Hardy os.  YMMV.

---

