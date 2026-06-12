---
title: "Bypassing The Password Prompt"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by londonlad on 2008-06-01
hi all,

is there anyway to bypass the password prompt? everytime i check the update manager or something like that, ubuntu always asks for it..........is there any way to stop it?

thanks...

---

### Post by dracayr on 2008-06-01
no, and be glad for that.. else linux would have as many viruses as windows...

EDIT: ok, apparently there is a possibility. didn't know that.

dracayr

---

### Post by lswest on 2008-06-01
if you do  ```
sudo visudo
``` and uncomment the line below "Uncomment to allow members of group sudo to not need a password" and then make sure your user is in the group sudo.  (or else change the "sudo" to "admin"(without the quotes)).  It will no longer require a password from you, but it is a **huge security risk**

---

### Post by mikewhatever on 2008-06-01
No. For more detailed explanation see here [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414).

lswest, you should take a look at the above link too.

---

### Post by lswest on 2008-06-01
> **mikewhatever said:**
> No. For more detailed explanation see here [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414).

lswest, you should take a look at the above link too.

I fail to see how my advice is much different from that, i warned him it's a security risk, and essentially that's where he would need to go to remove the password requirement for using sudo.  I've never done it myself nor will I, so it may be that the option i mentioned he should uncomment is not the one that will do what he wants.  He asked a question and I answered.  After looking at your link i still believe what i posted above will do what he wants it to.

Sure, he could remove the password requirement for only his username, but what if he wants it to happen on multiple accounts?  I don't recommend doing it, but it is the way to do it (at least, one way).  Also, the link does have a more detailed explanation, and had i known about it i would have included it in my post.  If i'm misunderstanding something, be clearer please.

---

### Post by aysiu on 2008-06-01
Please read / re-read the link mikewhatever posted.

---

