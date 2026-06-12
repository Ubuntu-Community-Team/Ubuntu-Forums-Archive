---
title: "Grub Error 17 After Restart"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by mbarvian on 2008-06-27
Hi guys,

So far this has happened to me twice.  When I set the power options to suspend when I close the laptop's lid, and I close the laptop's lid, it suspends properly.  However, when I open the lid, the screen does not turn on and after five minutes I have to turn off the computer manually and turn it back on.  After I do this, when it tries to load GRUB, it says:

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17

```

and that's as far as it goes.  I cannot log in to ubuntu or xp:confused:  Any suggestions

---

### Post by sharks on 2008-06-27
Dont know what it is but restoring the GRUB may solve this:
insert the live cd and follow this:
[www.sorgonet.com/linux/grubrestore/](www.sorgonet.com/linux/grubrestore/)

and this is another:

[http://www.linuxquestions.org/questi...-error-188769/](http://www.linuxquestions.org/questi...-error-188769/)

or use SuperGrubDisk

---

### Post by mjwhitfield on 2008-06-27
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)
> 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Have you fiddled with your partitions lately?

---

### Post by mbarvian on 2008-06-27
> **sharks said:**
> Dont know what it is but restoring the GRUB may solve this:
insert the live cd and follow this:
[www.sorgonet.com/linux/grubrestore/](www.sorgonet.com/linux/grubrestore/)

and this is another:

[http://www.linuxquestions.org/questi...-error-188769/](http://www.linuxquestions.org/questi...-error-188769/)

or use SuperGrubDisk

Thanks, I'll try this out and post the result

> **mjwhitfield said:**
> [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)


Have you fiddled with your partitions lately?

No, I haven't done anything to the partitions other than when I installed Ubuntu, which was a few weeks ago.

---

### Post by sharks on 2008-06-27
this can be useful:
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)

---

### Post by manishtech on 2008-06-27
> **sharks said:**
> this can be useful:
[http://ubuntuforums.org/showthread.php?t=804696](http://ubuntuforums.org/showthread.php?t=804696)
In this link, Error 17 has the reference 
> 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.       

File system type not recognized by GRUB?

---

### Post by sharks on 2008-06-27
better restore GRUB or reinstall Ubuntu

---

### Post by earthmeLon on 2008-06-27
Good luck :D

---

