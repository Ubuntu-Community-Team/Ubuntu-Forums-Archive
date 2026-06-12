---
title: "/dev/null permission"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by pruggles on 2008-10-18
I just downloaded Ubuntu 8.04 and I'm getting a dev/null permission error.  I've looked on the net, and I've seen other people with this problem, but it seems to be affecting the login of non-root users.  I am the only user right now, the error is blocking my login, and I'm not experienced enough to get around a normal login so that I can try any of the fixes. :confused:

---

### Post by RealPSL on 2008-10-18
During the count down of the boot process can you interrupt it and select the recovery mode. This will give you a prompt for root. You should be able to then fix the permissions. You can check them with this command ```
ls -l /dev/null
``` Your output should look like this ```
crw-rw-rw- 1 root root 1, 3 2008-09-28 17:59 /dev/null
``` If you do not have 3 pairs of "rw" then run the command ```
chmod 666 /dev/null
``` Run the above command again to confirm the change. Reboot your machine by running ```
reboot
```

---

### Post by pruggles on 2008-10-18
I went through the process and got it to display crw-rw-rw- 1 root root 1, 3 2008-09-28 17:59 /dev/null. Unfortunately after the reboot nothing changed.  I'm getting the same permission denial, and I still can't get to my desktop.

---

### Post by RealPSL on 2008-10-19
What are the permissions now? Can you post any error messages you are getting as well? What are you doing when you receive that error?

---

