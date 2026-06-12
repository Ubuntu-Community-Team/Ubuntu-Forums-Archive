---
title: "[SOLVED] Starting Mediatomb at boot"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by stuart264 on 2008-07-06
Ok, I am doing something wrong here to get Media Tomb to start at boot, I have added this line into my rc.local file

mediatomb -e eth01 -d -c /etc/mediatomb/config.xml start

And still it wont start on boot, go to console and enter mediatomb and it runs straight away, does anyone know whats going wrong with it?

Stuart.

---

### Post by nothingspecial on 2008-07-06
system > preferences > sessions.
Click add, fill in the boxes eg

```
Mediatomb

mediatomb

Media server
```

Should start at login :)

---

### Post by stuart264 on 2008-07-06
Thanks knew it had to be something really simple but I just couldnt figure it out and all the install guides seem to be for a PS3 rather than the Internet Radio I am using

---

### Post by nothingspecial on 2008-07-06
Don`t forget to mark this thread solved.:-({|=

---

### Post by godlike on 2009-10-19
thats not solved its starts at login not at boot

---

### Post by buntunoob on 2009-10-28
try Flexion's init script [http://wiki.flexion.org/InstallingMediaTomb012.html#5.3](http://wiki.flexion.org/InstallingMediaTomb012.html#5.3)

---

