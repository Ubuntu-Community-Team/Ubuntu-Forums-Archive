---
title: "Newb on the edge  (loving &amp; hating Hardy)"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by uubailey on 2008-05-03
So I may not be an _absolute_ beginner, because I have been using kubuntu since around the beginning of this year, but this is my first installation on my own.

After this morning found me alternately getting "locked" out of the admin account and at the blissful peak of setting up samba without asking anyone (personally) for help without a single error, I'm left again frustratedly scratching my head.

Now - get this - a FONT is keeping me out of my installation. I can't get in via recovery / rescue modes and I don't even get the chance to try using another account. The most irritating thing, is my gut feeling on this is that it would be very simple to fix if I just knew what to do.

Essentially what happens is the text part of the boot goes fine, but then when it gets around to entering the GUI, I get a message that says "Could not start kstartupconfig. Check your installation."

Then the real teaser comes in - as I logout, I get the messages "...Free Font Path recount is 2, should be 1; fixing." and then it hangs on that. When I try to logout again after 15 minutes or so, I get another message saying that x font server "xfstt" gets the ugly red fail of death.

I've had some real highs and lows the last couple of days with Hardy - for the most part it's been great, but it's been extremely frustrating for me on the other hand.

Please, please let me know what I should do so I can put this thing to bed and actually start enjoying it! 

Eternally grateful to you guys at the forum,
Bill

PS - I have reinstalled my nvidia drivers and dpkg-reconfigured xserver-xorg - both didn't do a lick of good. I'm really in a bind!

---

### Post by nosrednaekim on 2008-05-03
Looks to be a problem with kstartupconfig, not your fonts. Try running "mv .kde kde-backup" and re-logining in. if that works, we can move from there

---

