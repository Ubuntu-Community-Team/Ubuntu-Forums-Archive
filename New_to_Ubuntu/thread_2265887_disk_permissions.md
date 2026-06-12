---
title: "disk permissions"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by hmiersch on 2015-02-18
hi.
I have an external HD with all my media files, created under OSX. now, under ubuntu, i can read those files, but i can not write to that HD. on my user account it says it is a read-only file system, and on my admin account the GUI shows the HD but does not even let me see the contents, let alone use them ("You do not have the permissions necessary..." and so on) and the /media/sysop folder is empty. so what can i do? how can i change the permissions so that i can write to the HD from my user account? i guess it involves temporarily changing my user account into an admin account, right? is that even possible?

PS. losing all those files is NOT an option, and copying them, formatting the HD and copying them back is not possible due to lack of storage. we're talking almost a terabyte (on a 2-terabyte HD) here...

---

### Post by grahammechanical on 2015-02-18
This might help you

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

A lot will depend on whether that external hard disk was being journalled under OSX. You should also change your thread title to be more specific about your need to get read/write access to an OSX partitioned hard disk.

Regards.

---

### Post by hmiersch on 2015-02-19
Yes, that HD is journaled :-(
So the question is, how do I turn that off? In disk utility (in OSX) there's a toolbar button and a menu item to turn journaling on (both greyed out) but nothing to turn it off. Do I have to take that HD to the apple store?

---

### Post by hmiersch on 2015-02-22
update: took the HD to the apple store and they told me the only way to turn journaling off was to reformat the HD. so IOW, journaling can be turned on but not off. well **** you very much, apple.
formatting the HD is not an option because i would lose all my media files. copying them to another HD is not an option because i dont have enough spare capacity, and buying another HD is not an option either because i dont have the spare change. so i'm stuck between a rock and a hard place. anyone have any ideas?

---

