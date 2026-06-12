---
title: "Update manager problem HH"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Tomsolomon on 2008-04-30
OK I've just tried to update and the update manager has hung it reads:-
* debian/control:
 - add a conflict against "libnfsmap1" to "mount" to help the 
   apt resolver calculate dapper->hardy upgrades (LP:#157763)

Some how I get the impression its waiting for a response from me, but you may as well be asking me how long is a piece of string?/????
Anyone help please I've done a search and can't find anything specific to this problem.....

---

### Post by aheckler on 2008-04-30
Which Ubuntu are you updating from?

---

### Post by Tomsolomon on 2008-04-30
As I explained I'm using the "Update Manager".
And although subtle and unobtrusive I thought the "HH" in the title of the post would have given it away.......:)

---

### Post by aheckler on 2008-04-30
Ahh shoot, yes, I didn't see that, my bad. Well, your problem appears to be related to [this bug]("https://bugs.launchpad.net/ubuntu/hardy/+source/util-linux/+bug/157763"), but I'm not quite sure how to go about fixing it.

---

