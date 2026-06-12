---
title: "blank screen after reboot?"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2011-10-26
I just installed Lubuntu. Was working well, got the wireless working, then a box popped up asking to me activate the Nvidia propority driver. So i did, it downloaded and installed. Asked me to reboot. 

Now I sit here with a blank screen. 
I can get to console and run startx and I get:
Fatal server error:
server is already active for display 0
 If this server is no longer running, remoce /tmp/.X0-lock and start again.


How do I get back to my desktop?

---

### Post by carverj on 2011-10-27
I found some info that might help you sort this at:

[http://www.x.org/wiki/FAQErrorMessages#I_keep_getting_the_message:_.22Server_is_already_active_for_display_0.22](http://www.x.org/wiki/FAQErrorMessages#I_keep_getting_the_message:_.22Server_is_already_active_for_display_0.22)

Good luck

---

### Post by BuzzStPoint on 2011-10-27
Thanks. 
I used that link, and was able to start another X and remove the nvidia drivers.

---

