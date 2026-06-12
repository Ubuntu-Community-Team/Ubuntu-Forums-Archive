---
title: "Dapper's Conky is Busted ( slightly )"
date: 2006-06-12
forum: Repositories &amp; Backports
---

### Post by arsenic23 on 2006-06-12
I installed conky from the repos last night and set it up, got it working to where I was happy, and then went about building my display.  When I tried to use the if_mounted variable I'd get a segmentation fault.  I asumed it was something I was doing so I headed over to conky's IRC channel.  When I got there and presented my problem I was asked for the version of conky I was using.  

I told them and after a few seconds someone replied, "Another Ubuntu user!  We have got to do something about this."   So I just removed it and installed the newest version from source, everything is good now.


( Just thought I'd post this somewhere. )

---

### Post by seldon77 on 2006-06-20
wow... how did you install via source?

i tried it and it seems as though all the dapper dependancies are old / need to be updated for the latest conky to work.

---

### Post by arsenic23 on 2006-06-21
I followed a guide I found on this forum for building debs and installed it from the deb I built...  now where was that guide....

[http://www.ubuntuforums.org/showthread.php?t=51003&highlight=making+.deb](http://www.ubuntuforums.org/showthread.php?t=51003&highlight=making+.deb)

---

### Post by seldon77 on 2006-06-22
thanks!

I had previously tried via 'make', 'make install' etc and it doesnt work  that way (wrong dependencies)

if I can get this working well, then I'll see if i can get do a patch to automatix so that people can get a nice version of conky up and running.

---

### Post by seldon77 on 2006-06-23
hi again...

nope it won't let me build a .deb from the conky source...

have you still got the .deb you made? the version in  the repos is very old, and it wont build from the source in ubuntu.

if you have it, i'd be very grateful... [email]ubforum@pengo.us[/email] or upload it somewhere??? thanks!

---

