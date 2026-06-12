---
title: "matlab bamboo-wacom incompatibility?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by SkippoGuangiacomo on 2008-08-22
Hi,

I've successfully installed the pen tablet bamboo (Wacom) on my system after following the tread posted on:

[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)

However, after that I've done this, unexpectedly I get logged-out of the desktop any time that I commit an error in Matlab (e.g. if in the matlab desktop I type ")" I get logged out of the system).
What happens, litterally, is this: I type the mistake, matlab make the bios beep, I get the log-in screen of ubuntu (version 8.04 KDE). Worthless to say that Matlab was working perfectly fine before that I installed the tablet.
It gets weirder: I've noticed that when I do not commit errors in Matlab, everything actually works fine, I don't get logged-off, I can make figures, graphs, you name it; UNLESS if it requires matlab to beep...

It got even worse, I tried to re-install matlab (version 2007b) thinking that maybe something weird had happened when I installed it, however during the installation when I got asked to insert CD2 I got logged out again. Which means I cannot terminate the installation of Matlab anymore. 
Because I need Matlab, I went for the ultimate solution, which is to reinstall kubuntu all over again, after formatting the partion where it was installed previously.
The re-installation goes fine, I get Matlab up and running again, and VERY confident I reinstall the tablet.

Same story! Anytime I make an error in Matlab I get logged off... 

I did another test too: I tested if it was just the bios beeping that created the logging-off procedure, but after installing a software that makes the bios beep, I got no problem (i.e. the bios beeped and i happily remained in kubuntu :)) Caught by desperation I unplugged the cables which connect the speaker to the bios, and the idea was that I would have been logged off, but without beep. It did happen, also without beep, so the problem is not on the cables... :)

Conclusion: I don't know why this happens, and what the source could be. I could not replicate the error outside matlab (but I tried only the options I could think of) so now I'm considering a kind of Matlab-Bamboo incompatibility which seems rather nonsense, but I must admit I'm resourcesless...

The solution would be to don't use bamboo given that i need matlab more, but it seems a kind of very sad solution :(

Any help would be very appreciated!

Thx
SGG

---

### Post by kjohansen on 2008-08-22
not a real solution, but you could use octave.

there is a decent gui for octave called qtoctave.

there are some differences between octave and matlab but in my use of it I have yet to find a difference.

---

### Post by SkippoGuangiacomo on 2008-08-23
Hello kjohansen,

thx for the reply. I know Octave and I know there are not many differences (or that's what I've heard). The problem is the toolboxes, which are not developed as much if you need to do digital signal processing. Do you have experience with that?

Thank you a lot.
SGG

---

### Post by kjohansen on 2008-08-24
i dont personally do any signal processing, im a machine learning person. but i asked some of the people from the signal processing lab here (at my college) and they made mention of octave-forge and signalpak to mimic matlab functionality.  I dont know how close the functionality is but...

---

### Post by SkippoGuangiacomo on 2008-08-24
Oh, that's nice. Thank you, I'll give a look!

Actually, I've just noticed that i get the same error with Kate. I was compiling some c code, and when i pushed the arrow to scroll down with the line in the command window I got logged out again...

So it becomes now more complicated than what i thought.

Thx for the suggestions Anyway.

---

