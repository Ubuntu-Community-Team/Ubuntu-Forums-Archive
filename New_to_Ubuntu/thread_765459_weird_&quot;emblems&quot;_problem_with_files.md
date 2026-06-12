---
title: "weird &quot;emblems&quot; problem with files"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by robalcorn on 2008-04-24
I did a fresh installation of hardy this morning and its awesome but experiencing something weird. Every mp3 ,jpg or anything I copy over to my home directory shows the little read only emblem icon on the corner of each file. Is there a way to globally change that so it doesnt show what I am guessing as "read-only"? On everything....

---

### Post by dark_harmonics on 2008-05-21
It sounds to me like you need to take ownership of the files again. try a sudo chown -hR yourusername folderofmp3files to take ownership of the files again. those emblems are warning you about permission (at least thats my guess).

---

