---
title: "Problem with Video card, and mp3s won't play"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kha02 on 2008-04-26
Hello all!

I am a new Ubuntu user, been using Ubuntu for a few months now, and I am loving it. That being said, I don't know if I did something fatally wrong or what but I feel like the more I try to fix it, the more things get messed up.

Okay so here's what's up. Been using 7.10 for a while now, all was good, and then the day 8.04 came out I upgraded as soon as I could. Now I understand that when a new release comes out, there is bound to be bugs and errors every now and then, so I'm okay with that, but a big issue that came up was suddenly my graphics card wouldn't work. I couldn't get any kind of info that would explain to me what to do about the problem, so I did what was probably a stupid move.
I re-installed 7.10 from a disk I made, thinking I'd just wait until 8.04 has whatever is wrong fixed (or at least until the new Firefox browser isn't in Beta anymore).
Since I did that, when I tried to enable my graphics card, I get a message saying the following: *The software source for the package nvidia-glx-new is not enabled.* So I went to Add/Remove to find the appropriate item and typed in "Nvidia." Everything that came up said: *Nvidia xxxxxxxx driver cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.* Now I know this should not be the case as I do have the proper hardware installed in my tower. Should I open it up and make sure it's in there tight or something?

Okay so that's the first problem, although worst comes to worst, I can live without it (there might be a better driver I can get somewhere else). The other problem is much more upsetting to me since my life in many ways revolves around music.

I tried installing gstreamer0.10-plugins-ugly from Add/Remove (as I had done before without a problem) and I got the following message:Cannot install 'gstreamer0.10-plugins-ugly' This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first. Switch to the 'synaptic' package manager to resolve this conflict. Now I'm not very proficient at all with the synaptic manager but I figured I'd go in an search for gstreamer0.10-plugins-ugly and I got a message saying in order to install this, I needed two other items: libid3tag0 and libmad0 in order for it to work, and when I searched for them, nothing showed up.

So, I don't know what to do. Is this fixable? Any terminal commands for me to copy? Anything at all? Please let me know. I am a complete n00b and chances are this is nothing, and I absolutely looooooooooooooove Ubuntu, so regardless of whether or not this is fixable, I'm still going to be working with nothing but Ubuntu. I would just reaaaaaaaaaaally like to fix this if possible.

Any suggestions, absolutely anything at all, would be greatly appreciated!

Thank you,
Khalid in Halifax, NS

---

### Post by Tatty on 2008-04-26
Im not sure about your second problem, but the problem with your graphics card seems to suggest that you have not activated all of the repos.  Go to System->Administration->Software Sources and make sure all of the repos are checked.

---

### Post by Kha02 on 2008-04-26
I just did what you suggested and immediately afterwards I got a notification saying there are 140 updates for me, so I have a feeling this may have solved the problem. Thank you so much in advance!!

---

### Post by dnns123 on 2008-04-27
I hope this works for you...

Prob 1: Go to System ->> Administration ->> Hardware Drivers
Click it and see if the graphics card is enabled. If not, enable it. this might ask you to download the 'new' Nvidia drivers.

Prob 2: In the add/remove window, type Ubuntu restricted extras. Try to install that and hope your MP3s will work.

Endorsments: Use Amarok! It rocks! hehe:lolflag:

---

### Post by Kha02 on 2008-04-27
Actually, what Tatty said was exactly what I needed to do for both problems. My graphics card is back up and running and my mp3s are playing as beautifully as ever. Thank you as well though for such a quick reply!!

---

