---
title: "Notification System"
date: 2006-08-31
forum: Programming Talk
---

### Post by rnodal on 2006-08-31
Hello all:

I'm trying to use notify-send with php but it does not work because the command gets executed as user: www-data. Is there a way around this? How do I tell notification-daemon which user to notify? 

Thanks a lot for your time.

-r

---

### Post by ifokkema on 2006-09-01
Don't know the notify-send program, but you could make a bash script that calls the program, chown it to the user you want it to run as, chmod 755 the file, and set the suid bit...

HTH

---

### Post by rnodal on 2006-09-01
notify-send is part of the package libnotify-bin. Here is the description:
sends desktop notifications to a notification daemon.

Anyway thanks for your answer it seems that thats the solution. Thanks for your time.

-r

---

