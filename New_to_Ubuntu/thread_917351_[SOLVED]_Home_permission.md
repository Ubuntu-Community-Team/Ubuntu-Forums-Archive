---
title: "[SOLVED] Home permission"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Ntweat on 2008-09-11
a unique problem... well... i was fooling around and i mistakenly did something with .ICEauthority ..... so... in an attempt to fix it i rebooted... it did not lock .ICE so in a depirate attempt to login i did this

sudo chmod 777 /home/ntweat

now all dir in ntweat have write access... how to make it normal without re installing... thanks

---

### Post by Iowan on 2008-09-11
My home directory has 755 permissions - I suppose you could **sudo chmod 755 /home/ntweat** to see if the original problem comes back.

---

### Post by Ntweat on 2008-09-11
thanks will try

---

### Post by Ntweat on 2008-09-11
worked beautifully thanks

---

### Post by Iowan on 2008-09-11
You're CERTAINLY welcome - mark this one [SOLVED] (under Thread Tools) !=D>

---

### Post by Ntweat on 2008-09-11
Done....

---

