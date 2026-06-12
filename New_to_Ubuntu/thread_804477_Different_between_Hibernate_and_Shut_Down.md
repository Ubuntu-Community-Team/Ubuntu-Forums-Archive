---
title: "Different between Hibernate and Shut Down"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-23
Hello, 

Yesterday I post question about SWAP partition because  it seem not working during Hibernate. The issue has been resolve yesterday but today I'm a bit confuse with Hibernation process. I think Hibernation and Shutdown do the same thing. I expect when hibernate, our sys will re boot faster compare if complete Shut Down. Beside, all open program will be restored. However, these are not happen in my case. Do I am the only one with this problem

---

### Post by sdennie on 2008-05-23
Hibernate doesn't insure a faster startup when compared to shutdown (it just insures the system is in the same state after resume).  In fact, depending on your system and how you use it, it might be a lot slower than restarting your system.  There are kernel patches that can compress the memory image as it writes it to disk but, that's a pretty drastic step to take.  If you are interested in quick shutdown/startup times, I would try using suspend instead of hibernate.  My laptop usually comes up in about 5 seconds after suspending it.

---

### Post by Raccoon1400 on 2008-05-23
Shutdown powers off the machine.
Hibernate dumps the ram into swap and then shuts down.

---

### Post by sayakb on 2008-05-23
+1 to suspend
For my case, I have a 9-cell Li-Ion cell which show not more than 1-2% battery drop for my laptop if I leave it in sleep mode overnight. Suspend just puts the laptop in a very low power mode which can quickly be awakened to fully active mode by either moving the cursor/pressing a key/pressing the power button depending on the laptop.

---

