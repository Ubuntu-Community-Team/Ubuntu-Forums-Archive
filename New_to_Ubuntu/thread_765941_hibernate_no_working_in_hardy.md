---
title: "hibernate no working in hardy"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by k66473 on 2008-04-24
I have just installed a clean hardy to ext3 partition (note : no swap partition defined).
After the installation completed, I immediately tested the hibernate function and it is not working, it just said fail fail... and bring me to the lock screen.
Do U have any idea?

---

### Post by Paqman on 2008-04-24
No swap = no hibernate.

---

### Post by k66473 on 2008-04-24
If I use swap image file, can the system do the hibernation?

My answer:
I tried and it does not.

I reinstall the system and this time I create a swap partition and
...... it can hibernate very well although I see some fail (activation fail ..) on the screen

---

### Post by Glaxed on 2008-04-28
i have 2 GB swap (yes, 2) and no Ubuntu version save for Gutsy has properly hibernated...
It always sleeps, and when you turn it on again, the screen goes blank..
I have a suspicion that it is an Intel problem.

---

### Post by Hero of Time on 2008-04-29
I'm having about the same problem, but for me, it either goes to hibernate or it does not. I think it has something to do with Compiz-fusion. I did a full clean install of Hardy and the default hibernate and suspend worked right away. But sometimes, it just won't hibernate. I really have no idea why this happens. With Gutsy, I could even run a VM and a game when going to hibernate while Compiz was running (though the VM would crash and close immediatly upon resume).
Anyone that can shine some light on this issue? I will try going to hibernate with and without compiz running, see if that will make a difference.

Edit:
Compiz off: Hibernate works.
Compiz On: Hibernate failes. It goes to the initial state of hibernate, but it does nothing. Just a black screen with a flashing cursor.

---

