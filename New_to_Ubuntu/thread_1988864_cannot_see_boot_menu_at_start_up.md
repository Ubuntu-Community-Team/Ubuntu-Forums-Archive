---
title: "cannot see boot menu at start up"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by ziggutas on 2012-05-28
I have installed ubuntu 12.04lts alongside windows xp on my oldish compaq desktop pc. Now I cannot find a way to boot into windows. It  always ends up getting the ubuntu log in screen, and that seems to work (mostly) ok.

This is what happens when i turn the power on:

[LIST]
[*]Compaq screen displays, where you can press f1 for settings etc-this works ok.
[/LIST]

[LIST]
[*]Screen goes black with following message "current input timing is not supported by the monitor display. Please change input timing to 1280x1024@60Hz". The monitor buttons do not respond at this stage.
[*]Screen stays the same for a while, then ubuntu log in screen displays. Ubuntu works ok.
[/LIST]
I am new to ubuntu (apart from a quick dabble last year) and unable to understand much of the command line help offered across the forum but have spent a day on this, and have discovered a few things that may help to understand the problem.

I suspect the grub boot menu is actually present, but the monitor is having a problem displaying. As the time passes it boots ubuntu by default. (Very recently i installed ubuntu on an old laptop with windows and ubuntu will always install first if i press no keys.)

Monitor is dell p190s. Display settings in ubuntu are set to 1280x1024 (5:4).
Windows is present; i can access files from home page.

I retrieved an older monitor from the attic that i had working on another pc with dual boot windows and ubuntu last year and tried that. Same problem. The display just seems to be unable to configure at start up...until ubuntu login is reached.

Anybody got any ideas?

---

### Post by ziggutas on 2012-05-28
Found this post

[http://ubuntuforums.org/showthread.php?t=1741623](http://ubuntuforums.org/showthread.php?t=1741623)

Followed clear instructions by Sinopa to edit and update grub. ( I changed the resolution numbers to 1280x1024 that monitor wanted)

Rebooted, but problem persisted.

Went back to the post, read on to page 2, where Jerry Storey wondered whether removing a hash mark in grub would help for his problem... and it did. 

Worked for me too.

Endless thanks to Sinopa and Jerry Storey for their clear communication!!

Time for a lie down.

---

### Post by daslinkard on 2012-05-28
Please marked as solved.  Thank you!

---

