---
title: "Cannot start KDE 4 through GDM, KDM, or KDM-KDE4"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by theharshone on 2008-10-19
Hello
I cannot boot into KDE4 from a graphical login manager. I can start KDE4 if I start X and KDE4 individually with 
     sudo X&
     DISPLAY=:0 /usr/lib/kde4/bin/startkde
If I try to start it through a login manager, it freezes before the first icon on SplashX comes into view. I do not know where the logs for this type of event are kept so I cannot post any. I have checked /var/logs and could not find the log for gdm/kdm/kdm-kd4 that shows more than X starting up.

Thanks in advance for the help :)

---

### Post by theharshone on 2008-10-19
Bump :(

---

### Post by theharshone on 2008-10-27
Does no one have an answer? Maybe just a place to get the kdm/gdm logs?

---

### Post by Neo_The_User on 2008-10-27
open up terminal

```

ls /etc/init.d/

```

Look for something that ends with dm or kde4 related.

After wards

```

sudo /etc/init.d/ (kde4 desktop manager nickname goes here) start

```

Be nice if Ubuntu didn't get all cute and you just type in startx and it launches the GUI like slackware...

---

### Post by theharshone on 2008-10-28
I tried all three(KDM, GDM, KDM-KDE4) , none of them work.

---

