---
title: "Problem with IPBlock"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by mity on 2008-08-28
I have been using IPBlock for a few months now with no problem for the past week it has been freezing on the start up. I have tried uninstalling and reinstalling. it did not work. 

has any one else come across this problem?

---

### Post by lovinglinux on 2008-08-28
No I didn't, but maybe we can figure what is going on.

Have you uninstalled it completely using Synaptic? Try uninstalling it completely and delete /var/cache/iplist content. Install again and see if works.

---

### Post by nicedude on 2008-08-29
You can just use apt-get with purge option to both uninstall it and delete it compleately then just install it again and it should work. I have not had any real trouble out of mine and it seems to work as well as peergaurdian does in windows.

COMMAND TO REMOVE IT

sudo apt-get purge iplist

COMMAND TO REINSTALL

sudo apt-get install iplist

That should do it and without you have to manually delete anything :-)

---

### Post by lovinglinux on 2008-08-29
> **nicedude said:**
> That should do it and without you have to manually delete anything :-)

Just meake sure /var/cache/iplist files were deleted.

Most problems I had with PeerGuardian were list cache related, so I guess it could also be messing with IPBlock.

---

### Post by nicedude on 2008-08-29
Using purge instead of just remove in an apt-get command will not just uninstall but also will purge the package from your system and any directories the software in question made when it was installed should be deleted as well. And yes you are dead on right that this is probably a problem with his cache as I used to have the same problems with peerguardian back in my dark Windows days :-)

---

### Post by mity on 2008-08-29
I tried to purge it and reinstall it. all the files in /iplist were deleted. 
I tried to install from the terminal, but i got an error mes. 

i reinstalled iplist from this location

[http://sourceforge.net/project/showfiles.php?group_id=198679](http://sourceforge.net/project/showfiles.php?group_id=198679)

my problem did not get resolved

can some one recomend another course of action

---

### Post by lovinglinux on 2008-08-29
> **mity said:**
> I tried to purge it and reinstall it. all the files in /iplist were deleted. 
I tried to install from the terminal, but i got an error mes. 

i reinstalled iplist from this location

[http://sourceforge.net/project/showfiles.php?group_id=198679](http://sourceforge.net/project/showfiles.php?group_id=198679)

my problem did not get resolved

can some one recomend another course of action

I'm not a experienced Linux user, but maybe you could try this:

Open Synaptic manager, click File > History and browse the folders with dates just before the problem appeared and look if something was installed that you think could be messing with IPBlock.

---

### Post by uljanow on 2008-09-23
Just for the records, the solution can be found [here]("https://sourceforge.net/forum/message.php?msg_id=5307194").

---

### Post by lovinglinux on 2008-09-23
Thanks for the info. Please don't forget to mark the thread as solved.

---

