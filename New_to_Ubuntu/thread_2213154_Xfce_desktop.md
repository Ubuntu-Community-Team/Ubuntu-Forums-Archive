---
title: "Xfce desktop"
date: 2014-03-25
forum: New to Ubuntu
---

### Post by Michael_Walker on 2014-03-25
I recently installed Ubuntu 12.04.4,After a few days I decided to add Xfce desktop,thinking it was a good idea at the time,following instructions that I had googled.Now when I turn on Ubuntu, I get the opening page Xubuntu and the following message "The disk drive for /tmd is not ready or present",then gives me the option to wait,skip or manually recover. Then goes on to the existing Ubuntu desktop and works fine. What else do I need to do to get Xfce desktop, as you will be aware from my query I am not technically,computer savvy, so any advice,instruction should be relatively easy to follow,including leave well alone and don't mess with things that I know nothing about.Any help would be appreciated,thanks.  -   Mike

---

### Post by bshatt1987 on 2014-03-25
I've gotten that message before as well, but I usually just wait it out and it doesn't take long for the drive to be ready.  I'm not really sure what it means, but...
Anyway, to load into the XFCE Desktop, when the login screen comes up there should be a little Ubuntu icon right in the login box area.  If you click that it will give you the option to choose which desktop to load.  I believe the default says "Ubuntu" which will load the Unity environment, but you should be able to click for XFCE/Xubuntu in that little menu I mentioned.  
Hopefully I described that well enough for you to understand.

---

### Post by steeldriver on 2014-03-25
It sounds like you have enabled autologin - which means that the system will skip the login screen (which is where the choice between the installed desktops is offered) and start whatever your last desktop was. Try doing a 'Switch User' and explicitly selecting xfce from the menu (press the little Ubuntu logo by your name on the login screen). If that doesn't work, temporarily disable autologin so that you get to the login screen on next boot.

The 'disk drive for /tmp is not ready' message is unrelated I think - and is probably bogus (the default installation doesn't use a separate tmp partition). I was getting the same message for a while on my 12.04 laptop, then it went away after a kernel upgrade.

---

