---
title: "Authentication failure"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by albaqui on 2011-10-28
Hi 
Yesterday I possibly changed log in screen. Now whenever I open it shows "authentication failure" in spite of putting my password. 

Can you help me to LOG-IN/UNLOCK

Thanks

---

### Post by nothingspecial on 2011-10-28
Post moved to it's own thread in ABT.

---

### Post by tartalo on 2011-10-28
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by albaqui on 2011-10-28
> **tartalo said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thank you very much. I did all this but still i could not finish.
I reset my passwors and came back to resume normal boot. 
it showed .... -laptop log in:
I wrote .... -laptop
password: ... 
now it shows: ~$

Now what should i do?

please help me.

---

### Post by tartalo on 2011-10-28
It's booting to a command line, did you remove your Desktop Manager? (GDM, LightDM, KDM...)

You could try this:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by albaqui on 2011-10-28
> **tartalo said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thank you very much. I did all this but still i could not finish.
I reset my passwors and came back to resume normal boot. 
it showed .... -laptop log in:
I wrote .... -laptop
password: ... 
[COLOR="Red"]now it shows: ~$[/COLOR]

[COLOR="red"]Now what should i do?[/COLOR]

please help me.

---

### Post by albaqui on 2011-10-28
> **tartalo said:**
> It's booting to a command line, did you remove your Desktop Manager? (GDM, LightDM, KDM...)

You could try this:
```
sudo apt-get install ubuntu-desktop
```


I tried with above.

It shows
E: Could not open lock file/var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the adminstration directory (/var/lib/dpkg/), are you root

Now what should I do?

Please guide me.

---

### Post by lolpenguin on 2011-10-28
Are you still booting into Recovery mode? Has your Login Display Manager been removed?
Following from what tartalo said, were any critical packages removed? Try this, and make sure you have the sudo part, it will ask you for a password.
```
sudo apt-get install gdm
```
If it has the same error as before, check that sudo is before the command.

---

