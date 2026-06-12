---
title: "Tried Installing ATI Video Drivers, Now nothing works -_-"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Inject on 2013-03-03
After getting annoyed with Ubuntu's "Unity Dash Home" being very laggy, even after getting compiz and making edits, I had decided to try to get the official ATI Video Card Drivers working (AMD if you really must). I also intend to play game on my Ubuntu Install as I have steam So I'm fairly certain that this would be recommend anyways. So I installed "Additional Drivers" (the software item from the software centre), and got a bit confused by it told it to cancel at 20% although for some reason it did something anyways, where as on most well programmed applications it would revert what it did, making we wonder why the cancel button even exist if it can't be used. 
Anyways;

So now when I boot up and log in, I see my desktop icons. Unity Bar does not load and "XScreenSavers" Freaks out with errors when I leave my PC to long. Basically nothing works. I tried unity --reset in terminal and stuff and what not but nothing works.

What should I do :(

---

### Post by Mark Phelps on 2013-03-03
You will need to remove the drivers and reinstall the default Radeon open-source drivers.  Instructions are in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

And for future reference, it is really a BAD idea to cancel something part way through.  Better to let it complete and then just remove or uninstall it.

---

### Post by Inject on 2013-03-03
OK, thank you very much. That worked well I used the following command from that wiki to fix it:
> sudo apt-get remove --purge xorg-driver-fglrx fglrx*   sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core   sudo dpkg-reconfigure xserver-xorg
XScreenSavers appears to not work now for some reason, perhaps I'll have to reinstall that? Not really sure why though.

New Issue has arose however,
I got my Unity bar back and all that fun stuff. However, after that I went into software sources - additional drivers - and then applied the proprietary drivers for ATI, it broke everything again.

What am I doing wrong?

How Can I get the Offical ATI/AMD Video Drivers for Radeon HD 5870 working? I plan to game on this so I'm sure I'd need them.
I've followed wiki's on this nothing appears to work.

If you can help that would epic :D
Thanks :/

---

