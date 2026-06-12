---
title: "a little question for a novice ubuntu network user"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by brian123321 on 2008-09-24
i was wondering how i can hide my tracks when moving around a network. i created files in a classmates folder bc he has his permissions turned off. but when u ls -als u can see that i was the person who put the file in there. i know there is a way to hide this from the network. does anyone know how to do this and is willing to help?

---

### Post by brian123321 on 2008-09-24
also the cd rom command . . . cdrom eject or what ever it is . . . is it possible to log into another machine and open up someone else cdrom?

---

### Post by ohzopants on 2008-09-24
the easiest way i can think of to eject someone else's cd drive is to ssh into their machine.  You need to have an account on that machine though, if it's at a school this is probably already the case.

then you just do ```
eject /dev/XXX
``` where XXX is the cdrom, finding that might be a bit trickier.

---

### Post by brian123321 on 2008-09-24
what is this command doing?

the cammand o eject is eject cdrom . . . 


what is dev?

---

### Post by brian123321 on 2008-09-24
we ssh into our professors network then in the home directory has everyones folders who is in the class . . .  do i go to their folder or their machine . . .how would i log into their machine?

---

