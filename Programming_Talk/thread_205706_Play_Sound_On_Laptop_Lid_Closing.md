---
title: "Play Sound On Laptop Lid Closing?"
date: 2006-06-28
forum: Programming Talk
---

### Post by UnknownOrigin on 2006-06-28
Howdy. Anyone have any ideas on how to make linux play a sound when I close my laptop lid? It would be handy since sometimes I only close my lid half-way so the screen blanks but to allow ventilation.

---

### Post by H.E. Pennypacker on 2006-06-28
Back in Windows, I'd turn on some music, lock and close the laptop lid, and walk away.  It would continue playing the music, eventhough the screen was locked, and the lid was closed.  

I believe we're talking about the same thing here.  With me, when the lid is closed, ventilation continues, so I don't have to worry about that.  I am mostly concerned with the music playing interrupted while the screen is locked and the lid is closed.

Anyone know how this is done?

---

### Post by UnknownOrigin on 2006-06-29
Actually, I was looking for ideas on how to have a sound play when the lid closes, so I don't have to bend down and look to see if the screen shut off.

---

### Post by UnknownOrigin on 2006-06-29
Well, after searching around a bit, I found an answer on the Gentoo forums. This can easily be accomplished by editing the /etc/acpid/events/lid file to say:

event=button[ /]lid
action=mplayer path-to-sound-file

and /etc/init.d/acpid restart

---

