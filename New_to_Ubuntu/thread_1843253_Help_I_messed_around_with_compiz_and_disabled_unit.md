---
title: "Help: I messed around with compiz and disabled unity"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Jumponskis1 on 2011-09-13
[http://ubuntuforums.org/showthread.php?t=1743747&highlight=compiz](http://ubuntuforums.org/showthread.php?t=1743747&highlight=compiz)


Same problem as in this thread but the solution given did not work for me.  messed around with compiz  cause i used to use it on hardy heron but this fix didnt work for me  and i got an error message that states warning no display variable set,  setting it to :0 and name error: global name "GError" is not defined

---

### Post by jumponskis on 2011-09-13
I finally figured it out. Went and created gdmsetup launcher, loaded up ubuntu classic, and ran ```
service gdm restart
``` which left me with ubuntu classic. I then went to system>compizconfig settings manager, enabled unity plugin then ran gdmsetup again, re-selected the ubuntu option (unity I suppose) then in terminal ran ```
service gdm restart
``` again and now everything is back to normal.


I would mark as solved but other account is now deleted

---

