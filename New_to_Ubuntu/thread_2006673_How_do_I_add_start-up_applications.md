---
title: "How do I add start-up applications?"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-06-19
Sorry about this one guys but I've looked everywhere and all I can find are guides from 2005/2007.

I go to the Startup Applications Preferences, the same place that has the GNOME login sound.

I suppose I click "Add" but what do I select as a file to launch? All the files in user/share/applications don't work from here... so I guess I'm clicking the wrong ones.

I'm trying to run skype-wrapper on start up, basically.

---

### Post by Drowz0r on 2012-06-19
> **Drowz0r said:**
> Sorry about this one guys but I've looked everywhere and all I can find are guides from 2005/2007.

I go to the Startup Applications Preferences, the same place that has the GNOME login sound.

I suppose I click "Add" but what do I select as a file to launch? All the files in user/share/applications don't work from here... so I guess I'm clicking the wrong ones.

I'm trying to run skype-wrapper on start up, basically.

Oh, actually, I found it. It was some script thing in usr/bin

---

### Post by Cheesemill on 2012-06-19
If you ever need the full path to an application you can use the which command:
```
root@quantal:~# which firefox
/usr/bin/firefox

```

---

### Post by Drowz0r on 2012-06-19
> **Cheesemill said:**
> If you ever need the full path to an application you can use the which command:
```
root@quantal:~# which firefox
/usr/bin/firefox

```

Ahh, that's really useful. I was trying to get that as well before :)

---

