---
title: "Avant window navigator"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-07-27
i've installed Avant Window Navigator, but each time i start ubuntu it does not appear. i need to go to application -> accessories and then select Avant Window Navigator, for it to appear on my desktop. is there a way to make AWN appear automatically on desktop each time i start ubuntu?

---

### Post by Troll_the_Great on 2008-07-27
Sure, go to System-Preferences-Sessions and ad it under StartUp Programs.
Cheers!

---

### Post by wariskampar on 2008-07-27
I don't know about your AWN (version?), but in my case, I just tick the "Automatically Start AWN during login" at General tab. Otherwise, Troll... answer is also applicable.

---

### Post by flytripper on 2008-07-27
user have experienced problems with the start up hanging the system i beleive. you may need a script that will allow it to pause first before it loads so other processes have a chance.  ```
#!/bin/bash
sleep 10 && avant-window-navigator

``` 
add this to a file called awnstartup or to that effect then browse it when you add the start up item

---

