---
title: "How Do I Make an update to Hardy look like... Hardy...?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by the_hardy_kid on 2008-07-15
Ok I admit, the title is terrible...

So anyway, I upgraded from Feisty(?) and the panels stayed the same.

How do I make em look like a fresh Hardy install?

Thanks, the_hardy_kid...

---

### Post by echo314 on 2008-07-15
The panels look the same because when you upgraded, you kept your same /home directory. In Ubuntu, your personal settings are stored in hidden directories within /home, and begin with a '.' 

I have not used GNOME in a bit, but I believe there are several config folders like ./gconfig or something like that, that you can reasonably guess are for gnome. Just enable viewing hidden files and delete them (or rename in case they were something else and you want to restore them)

Upon reboot you should see a fresh desktop.

---

### Post by LowSky on 2008-07-15
just change your theme

---

### Post by the_hardy_kid on 2008-07-18
Thanks both of you.

LowSky, that does not change my problem, but thank you for taking the time to comment.

echo314, thank you. I'm not sure if this will work, as I do not really want to delete / play with those folders. Thank you though.

Sincerely,
Tyler

---

