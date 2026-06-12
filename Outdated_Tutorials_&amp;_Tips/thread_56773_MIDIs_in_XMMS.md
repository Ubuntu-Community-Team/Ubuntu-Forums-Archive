---
title: "MIDIs in XMMS"
date: 2005-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Limulus on 2005-08-14
So I was doing a little surfing and wanted to listen to the MIDIs I downloaded from [this page](http://ingeb.org/Lieder/keinentr.html).  What an adventure that turned out to be! ;)  Instructions like the ones in [this](http://ubuntuforums.org/showthread.php?t=8736) or [this](http://ubuntuforums.org/showthread.php?t=30963) thread are terrifying to anyone without a lot of Linux experience ^_-;  But after several hours of [searching](http://www.xmms.org/plugins.php?details=42), I figured out how to play them (in XMMS on my PC runnning Hoary) in just FOUR easy steps :)

First, go to Synaptic and install "timidity" and "freepats" (and if you don't have it already, install "xmms" too ;).

Second, download [xmms-midi](http://vemod.net/debian/dists/sid/packaged/binary-i386/xmms-midi_0.03-1qerub3_i386.deb) from [this page](http://vemod.net/cemos/debian/packages) and save it to your Desktop.

Third, run the following two commands in Terminal:

[I]sudo dpkg -i ~/Desktop/xmms-midi_0.03-1qerub3_i386.deb
sudo cp /etc/timidity/timidity.cfg /etc/timidity.cfg[/I]

Finally, right-click a MIDI (such as one of those from the page, saved to your Desktop), "Open with Other Application..." and select XMMS.

That should work just fine :)  Note that XMMS takes a bit longer to close after loading a midi, but otherwise should perform normally.

---

### Post by Lux Perpetua on 2005-08-25
All right. I did exactly what you said; installation had no issues. But when I tried to play a midi, XMMS just locked up and I had to kill it from a terminal.

---

### Post by littlered on 2005-08-25
Thanks for this.... I tried one of those others and really couldn't make heads or tails of it. This one didn't work on the first try, but then I decided to see if reinstalling timidity and freepats would make a difference, and it did, because it works. :)

Thanks again,

LR

---

### Post by Arktis on 2005-09-14
Thankyou so much!  This got midi working in breezy for me, and now I can use the 'play' feature of songwrite! :grin:

---

### Post by emendelson on 2005-09-15
Very useful tip - thanks! 

Problem: I can get midi files to play when I open them in XMMS, but when I right-click and Open with... xmms, the program opens for a second then closes. I've tried various reinstalls, with no luck. If anyone knows a solution, I'll be very grateful.

---

### Post by Nai on 2006-01-31
Alright, XMMS will open the file, if i start the program, and then open the file through the program, but if i right click on a file, and click 'open with another application,' it opens the browser for about 2 seconds, but doesn't show anything, and then an error comes up, and it says "The Application "nautilus" has quit unexpectedly." before it closes the browser. Also, when i try to *play* the file in XMMS, the program just quits without warning. Any help would be greatly appreciated!

---

