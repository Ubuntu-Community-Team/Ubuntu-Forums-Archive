---
title: "[SOLVED] intrepid broken - cannot log out, broken graphics"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-11-02
I just did a fresh install of Intrepid and merged my old /home directory to the new one. 

When I log out, the screen goes black, tries to load the logon screen several times, then kicks me to a horrible low-res screen.  I am wondering if it is the nvidia 177 driver I chose as opposed to the 173 driver.  I haven't seen this issue reported yet.  Any ideas?

Thanks

JTS
Edit: forgot to mention that shutting down and restarting works.  The initial login works fine, it is simply logging out and logging back in that breaks it.

---

### Post by rouge568 on 2008-11-02
Have you tried switching the drivers and seeing if that fixes it? I think the 177 might still be beta.

---

### Post by jimmy the saint on 2008-11-03
that was it.  bad implementation or something.  the earlier driver works fine.

---

