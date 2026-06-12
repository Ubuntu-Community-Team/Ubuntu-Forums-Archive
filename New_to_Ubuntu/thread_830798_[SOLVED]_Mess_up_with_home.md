---
title: "[SOLVED] Mess up with /home"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by wariskampar on 2008-06-16
Hello, i try to setup /home on a dedicated partition. I followed one tutorial but some instruction break along the line. As far as I remember, I made a back up of my /home in / and then create mount point (/home) in /. Then I mounted /dev/sda3 to /home and move /home inside it. But error message (about permission) pop up (in terminal) during this moving process, thus I decide to abort it. I try to umount /dev/sda3 after that but still can not (at that point I can see /home in Nautilus. When I restart my system, I can not boot to desktop (Message pop up saying that can not find home!). So right now, i'm hoping someone can assist me to to put back /home to it original location using LiveCD (i'm writing this using LiveCD). Please assist me....

---

### Post by wariskampar on 2008-06-16
ok solve! Phew!!!! I edit my fstab in LiveCd and problem solve. Now I successfully re-locate my /home to dedicated partition. Thank you all

---

