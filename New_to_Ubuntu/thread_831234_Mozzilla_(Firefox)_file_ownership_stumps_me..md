---
title: "Mozzilla (Firefox) file ownership stumps me."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by 4nick8or on 2008-06-16
Hi: 
  Not exactly a newbie, but I feel like one.
Hardy, upgraded from Gutsy. All was fine before the upgrade.
Prob: Firefox no workie - As root= all good. As newly created user= all good. As me (tom, the prime user)= not good. 
  I suspect this is a permissions problem. I own the .mozzilla folder, however I have no file permissions. When I check them on the properties/permissions gui, click apply to all folders, it refuses to accept the change and returns to a (-) in the checkoff button. Searched plenty, tried various terminal solutions, like "sudo chmod 777 -R /home/tom/.mozilla" all to no effect. 
   Why can't I get file ownership permissions for these files, and what happened to cause the upgrade to alter their ownership? I would be grateful for suggestions or solutions.

---

### Post by MasterSander on 2008-06-16
You can try to log in to nautilus as root and then try to change it.

---

### Post by ayenack on 2008-06-16
Try re-installing Firefox.

sudo apt-get install --reinstall firefox

Might sort things out for you.
SORRY:- Should have put the **install** in.

---

### Post by 4nick8or on 2008-06-17
MasterSander: nope no workie... thanks.

         AYENACK : Reinstall seems the better solution, thanks. Now I can control SOME extensions, some not.... It did serve to remind me that Firefox is not my cup of tea - I much prefer Opera. I really miss Maxthon. I have it dialed on my windows boxes. 
  
  Still, I'm sticking with Ubuntu, just because it's challenging & fun to tweak. Someday Linux will come as natural to me as XP. I really would like an equivalent to System Restore to come along. Making images is a waste. 

  Back on topic: Thanks to youz for taking the time to reply. (I'm still clueless why I'm unable to take control of file r/w when I own the folder.

Regards

---

### Post by ayenack on 2008-06-30
Not sure if you have it or not but just in case you can install Opera like this.

In Treminal.
**sudo apt-get install opera**

---

