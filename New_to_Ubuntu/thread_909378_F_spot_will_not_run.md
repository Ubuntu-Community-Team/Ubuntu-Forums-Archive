---
title: "F spot will not run ??"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by aja on 2008-09-03
Could some one please help ??

I have loaded f spot "Photo managing soft ware" via add/ remove programs. the problem is that i click on it an it will not start ?  I have tried unloading  and loading , tried re-installing , but it does not start. Does any one have any ideal ??

Thanks
AJA

---

### Post by philinux on 2008-09-03
Some would say you're lucky. I uninstalled it.

I can't stand it and use gthumb.

---

### Post by WRDN on 2008-09-03
Type "f-spot" in the Terminal to find what is happening when it starts. If/ when an error appears, you can post it here if you are not sure what it means.

---

### Post by aja on 2008-09-04
Tried in terminal, and this is what i got


Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()


Any ideals ??

---

### Post by philinux on 2008-09-04
Someone solved it by doing this.

> **Should i laugh or cry? F-Spot doesn't run** 			 			 			 		   		 		 		I solved this problem by removing the f-spot database: ~/.gnome2/f-spot/photos.db.  I think (speculation) that f-spot failed to load because the program expects to find pictures at ~/Photos, but Gnome 2.22 does not have this folder. It is called, "Pictures" now.


---

### Post by cespinal on 2008-09-04
Yes, I have an idea: 

Get Picasa

F-spot is useless

---

### Post by rmls on 2008-09-05
I had the same problem and solved it as above (deleteing ~/.gnome2/f-spot/photodb.) But it is as others have said pretty 'em.. I don't know what you are looking for but if it is a RAW Photo processing software try Raw Therapee from [http://www.rawtherapee.com/](http://www.rawtherapee.com/) there is a Ubuntu installer that worked grand for me.

Cheers
rmls

---

