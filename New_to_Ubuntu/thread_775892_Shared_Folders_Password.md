---
title: "Shared Folders Password"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dover19 on 2008-04-30
I'm trying to connect to the shared folders I've defined using System>Administration>Shared Folders.

It asks me for a user and password, so I figure that's probably my ubuntu login. So i put in my ubuntu user id and password but it keeps asking me for my password as if it's incorrect.

---

### Post by mlentink on 2008-04-30
> **dover19 said:**
> so I figure that's probably my ubuntu login
Actually it isn't. Folders shared that way are smb-shares, so you're being asked for a samba password. I guess you're not running Hardy?
'Cause if you were, setting permissions on that folder to general guest access (without a samba account) would be as easy as right-clicking on that folder, clicking 'sharing options' and ticking the appropriate box.

---

### Post by dover19 on 2008-04-30
No, I'm running Gutsy. I installed it about 1 week ago. Not sure I wanna upgrade right away since Hardy's new.

---

### Post by drsox1899 on 2008-04-30
To have samba in 7.10 you should follow this thread :

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Works very well in 7.10 (can speak from experience of it )

---

### Post by dover19 on 2008-04-30
Thanks to all, I got it working. Finally! lol

---

### Post by betes on 2008-04-30
> **mlentink said:**
> Actually it isn't. Folders shared that way are smb-shares, so you're being asked for a samba password. I guess you're not running Hardy?
'Cause if you were, setting permissions on that folder to general guest access (without a samba account) would be as easy as right-clicking on that folder, clicking 'sharing options' and ticking the appropriate box.

Hi-

I *am* running hardy, and i will say this seems a whole lot easier than it was when i tried it under gutsy, but I'm still having one little problem. 

I right clicked on the folder and used the sharing options for some folders on both my laptop and my desktop (both running hardy).  Accessing the laptop from the desktop works fine, i'm promped for my samba password and can mount the folder.  Accessing the desktop from the laptop I have the same problem the OP does, it repeatedly asks me my password.  If I "tick the appropriate box" as you say I can access my desktop folders from my laptop without a password, but I would prefer to have a password.  

Any ideas why my desktop seems to have automatically set up a samba account and my laptop (using the same "right-click to share" method) didn't?  And how do I set up a samba account for my laptop.  Thanks for any help!

---

