---
title: "Cannot disable monitor power saving"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gnurfos on 2011-10-02
I'm on Gnome Classic now, but I had the same problem under Unity: no matter what I set under "system settings", my monitor switches to power saving after some 10 minutes of user inactivity.

How does this work, and how can I fix it ?
Thanks.

---

### Post by grandtoubab on 2011-10-02
look here
[http://ubuntuforums.org/showpost.php?p=11301692&postcount=19](http://ubuntuforums.org/showpost.php?p=11301692&postcount=19)

---

### Post by Toz on 2011-10-02
```
xset -dpms
```

Reference link: [http://v2kblog.blogspot.com/2008/08/disabling-monitor-power-saver.html]("http://v2kblog.blogspot.com/2008/08/disabling-monitor-power-saver.html")

---

### Post by Gnurfos on 2011-10-04
Thanks, it works.

But how do I make it permanent ?
I mean, I don't want to run a command on every reboot, even if this is automatized. It sounds wrong. Surely those settings are stored somewhere and could be changed there ?

---

### Post by zenarcher on 2011-10-04
I'm having the same issue with one of my Kubuntu installs.  I have three identical machines, all with clean installs and current updates.  Power saving works fine on two of them, but not the third one.  I'll also give this a try.

Thanks,
zenarcher

---

### Post by Toz on 2011-10-04
> **Gnurfos said:**
> Thanks, it works.

But how do I make it permanent ?
I mean, I don't want to run a command on every reboot, even if this is automatized. It sounds wrong. Surely those settings are stored somewhere and could be changed there ?

Try creating the file **~/.xprofile** with the contents:
```
xset -dpms
```
...and make it executable
```
chmod +x ~/.xprofile
```.

---

