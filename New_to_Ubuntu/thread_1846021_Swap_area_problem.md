---
title: "Swap area problem?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by sakibmoon on 2011-09-18
I know Ubuntu keep a separate section section called swap and someone told me that this place is used as an alternative to RAM. Using too much swap will slow down my PC.

My pc is currently using 5% of it's swap area that is 45 MB. Is it too much? Only 40% of my main memory is being used.

---

### Post by Lisiano on 2011-09-18
Why do you get that suspicion? Swap is just reserve memory in case your PC ever runs out of RAM, Ubuntu and every Linux distro uses your RAM as much as it can. So unless your RAM usage is 5% and Swap 90% (and it's not something like 100mb) then there is no alarm.
This is not Windows that after a set amount of time puts whatever it can into swap. This is Linux and we keep your RAM used all the time.

---

### Post by sakibmoon on 2011-09-18
Thanks for the info.

---

### Post by Paqman on 2011-09-18
If you want to decrease the amount that the system uses swap you can [adjust the swappiness setting]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F").

---

### Post by sakibmoon on 2011-09-18
Thanks. Works great. I reduced my setting from 60 to 10.

---

