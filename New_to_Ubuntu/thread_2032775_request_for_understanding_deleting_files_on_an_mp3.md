---
title: "request for understanding: deleting files on an mp3 player"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-07-24
Hi Y'all Ubuntu Community!!

I had problems with deleting files on an mp3 player. 

:(

I plugged it into the USB, Ubuntu mounted it, but after updating podcasts with GPodder, I could not remove (rm) music files that I had transferred to the mp3 player with Nautilus! I could remove them before that GPodder update. Not sure whether that had anything to do with it!

:confused:

When I tried to remove them, either with Nautilus, or from the command line, and whether I was superuser with either tool, I got the message something like

"Dude, this is a read only devise. Go away!" :twisted:

I found a solution: take the player over to a windows machine and was able to remove them with explorer. 

](*,)

But I don't understand! Why couldn't I remove them with Ubuntu??

:-k

Thanks!
Old Jimma
Jimmastan, GA

---

### Post by Bufeu on 2012-07-24
Tried *sudo rm /path/to/file*?

---

### Post by Old Jimma on 2012-07-25
Hi Bufeu:

Yes, I've tried

cd to directory
sudo rm *

the error message I get is: Read-only file system cannot remove

Thanks,
Old Jimma

---

### Post by Old Jimma on 2012-07-25
Bufeu:

My mp3 player has a function that allowed me to format that micro sd chip.... so I formatted it.

After formatting it, I was able to read and write to the drive from Ubuntu.

Not sure what happened, but it is working again.

Thank you for your reading my post, Bufeu.

Sincerely,
Old Jimma
Jimmastan, GA

---

