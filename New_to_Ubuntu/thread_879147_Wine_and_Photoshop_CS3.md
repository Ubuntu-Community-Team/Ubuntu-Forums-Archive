---
title: "Wine and Photoshop CS3"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by EmilM on 2008-08-03
This is my first day, or evening, with Ubuntu. I've experience with Debian as server, but never a Linux workstation. So far I'm impressed, but in my work it's important to use Photoshop so I've tried some guides how to get Photoshop to work with Wine on Ubuntu - and it almost works, however I'm not able to accept the "End License Agreement" and the text field is just empty. If I run it from Terminal I get a lot errors like "fixme:shdocvw:InPlaceFrame_SetStatusText (0x16864c)->(0xf7ebe735)" (not aware if you need all the errors?).

Hope some of you can help me, else I'm forced back to Windows :(

---

### Post by Liolikas on 2008-08-03
Try C2 it works better.
Also look here:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by vandorjw on 2008-08-03
Have you tried "Virtual Desktop"?
Under Configure wine, then look under "graphics.

Also, Sometimes, you can use Windows DLL's, to make stuff work.
DO NOT DELETE the Wine DLL's, (Just rename them if you have to)

[http://www.dll-files.com/](http://www.dll-files.com/)

download them from there, then put them in the system32 folder.

There is an option in "configure wine" to use different DDL's, make sure that after you put them in, you tell wine that they are there.

this is going to be pain -stacking, but you can continue to try different combo's until it works.

Cheers- CC7

ps: "fixme:shdocvw:InPlaceFrame" -- to me this looks like something that can be fixed using the "virtual desktop"

---

### Post by EmilM on 2008-08-03
Thanks for the answers, I'll try my CS2 then instead.

---

### Post by Vorian Grey on 2008-08-03
Be sure to check out winetricks and install the windows fonts and the gecko html engine. CS2 runs perfectly in wine but I prefer CS3 so I use Virtualbox.

---

### Post by silkstone on 2008-08-03
CS2 is supposed to work well under Wine, but CS3 does not.

You may like to explore the GIMP which is really very good but also a lot different from PS. If you do take the time to learn the GIMP, it may do what you need and save a great deal of money in PS upgrades etc. :)

---

### Post by Brightbelt on 2008-08-03
If you have any performance issues on CS2, it might be worth getting Linux CrossOver - the "pay" version of wine. It's only $39.95 and I found it made a huge difference in quality for running Photoshop 7.0. 

The interface was cleaner, more held together the way it should be when I used CrossOver. 

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/) 

Just an idea to keep in mind.

Frank B.

---

