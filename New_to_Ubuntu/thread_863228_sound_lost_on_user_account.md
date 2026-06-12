---
title: "sound lost on user account"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by candtalan on 2008-07-18
I still have sound with my first user (sudo enabled) account, but the second user (no sudo facility) account has lost any sound. A club uses this second user account so something might have got messed up (without sudo).

I am the first user login (admin) with sudo ability so I can reset the other user, but what should I look for and change to get the sound working again please?

tia

---

### Post by Morpheun on 2008-07-18
Make sure the second user is in the appropriate groups for whichever sound utility you're using (probably one of the pulse groups)

---

### Post by markjensen on 2008-07-18
^^^  Agreed that it is almost certainly a matter of the new user not being part of the "audio" group or such.  I recall doing this on an initial setup of Xubuntu.

You can do it by **adduser *xxxxx* audio** (if the group is still called "audio"), or by using the GUI tools under user administration.  Add the privelege to use audio to that them when you modify that user's properties.

---

