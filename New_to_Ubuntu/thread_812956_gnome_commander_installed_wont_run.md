---
title: "gnome commander installed wont run ??"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by lost4now on 2008-05-30
I have tried several times to install gnome commander but have yet to be able to get it to run. 
It notes at the bottom of the desktop it is loading but after a couple minutes it vanishes and no program.

Any hel would be appreciated...Thanks

It has been a couple weeks now and no replies. Any help would be appreciated.

---

### Post by lost4now on 2008-06-15
bump please

---

### Post by oldos2er on 2008-06-15
Can you post the output of running "gnome-commander" in a terminal?

---

### Post by lost4now on 2008-06-15
This is the result of command lin gnoime-commander


** (gnome-commander:7182): CRITICAL **: void gnome_cmd_con_ftp_set_user_name(GnomeCmdConFtp*, const gchar*): assertion `user_name != NULL' failed
Segmentation fault

Hope it means more to you than to me.   Thanks

---

### Post by louieb on 2008-06-15
How did you install it? Gnome-Commander installed via Synaptic works just fine for me.

---

### Post by lost4now on 2008-06-15
gnome commander via synaptic. Did it three times with the same results.

---

### Post by louieb on 2008-06-16
I don't have a clue why Gnome-Commander is not working for you. 
So heres a bump. 
One last question. Are you running 32 or 64 bit Ubuntu?

---

### Post by lost4now on 2008-06-16
32 bit 
Thanks

---

### Post by dani&lt;&gt;&lt;er on 2008-07-17
i had the same problem
i deleted all the lines from
/home/user/.gnome-commander/connections

and worked for me.

---

