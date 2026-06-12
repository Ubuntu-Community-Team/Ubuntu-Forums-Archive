---
title: "Grub question"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by r_avital on 2013-08-20
Every time I do a fresh install, as long as GRUB is never invoked, a cold-boot or reboot proceeds directly to a login screen, as it should.

If for any reason, upon boot/reboot, I invoke GRUB (left-Shift), GRUB starts, as expected, but after that first invocation, every boot/reboot automatically starts GRUB whether I want it to or not.  Doesn't bother me much, but just curious.

Why is this happening, is it normal, and is there a way I can prevent GRUB from starting like that, without removing the ability to invoke it later with left-shift if I need to?

Thanks.

---

### Post by sudodus on 2013-08-20
You can read about grub and in particular the hidden feature at this link

[https://help.ubuntu.com/community/Grub2#Hidden](https://help.ubuntu.com/community/Grub2#Hidden)

I hope it helps :-)

Edit: See also [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by r_avital on 2013-08-20
sudodus,

Many thanks.  Perfect explanation.
My grub file shows a timestamp of having been edited yesterday.  I know I didn't touch it.  The only thing in that file that could explain the behavior, is GRUB_HIDDEN_TIMEOUT which was set to 0 and commented out.  I know I did not comment it out, never opened that file until today.  I can only guess it gets commented out when a second kernel gets installed as part of an update.

At any rate, commented it back in.  Just trying to get a quicker bootup, which is already impressivley very sort.

Thanks again :)

---

### Post by sudodus on 2013-08-20
You are welcome :-)

When you feel happy with the solution, please mark this thread as SOLVED according to this link

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by r_avital on 2013-08-20
My bad, sorry about that.  I mean, I still don't know who/how/why the change was made, but it's good enough that I can undo it.

---

