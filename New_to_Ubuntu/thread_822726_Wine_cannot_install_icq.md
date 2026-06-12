---
title: "Wine cannot install icq"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Luuka on 2008-06-08
Hey guys, I searched the threads for it, but I didn't find anything unless I was looking in the wrong place.

I need to install icq on my Ubuntu 8.04. I have wine and I downloaded the Install_ICQ6.exe but it doesn't work. It gave me false hope when it pulled up install shield wizard, but then this is what it said.

"Unhandled Exception
Error Number: 0x80040702
Description: Failed to load DLL: MoveIt

Setup will now terminate"

What do I do in this case? I'm not exactly sure how to go about installing things, if Wine won't even go past that screen. Any ideas, suggestions? I'm going out of my mind here.

---

### Post by django0909 on 2008-06-08
Forgive me if I'm wrong, but can't you ICQ with Pidgin?

---

### Post by RequinB4 on 2008-06-08
You're on 6.04... what version is your wine?

```

wine --version

```

Might help a bit to upgrade, if it'll work at all.

Always check the appDB with Wine - [http://appdb.winehq.org/appview.php?iAppId=55](http://appdb.winehq.org/appview.php?iAppId=55)

Edit - I'm assuming you want to use wine for a certain reason, because Pidgin (formerly gaim) does ICQ....

---

### Post by kellemes on 2008-06-08
[Pidgin]("http://www.pidgin.im/") supports ICQ.

```
sudo apt-get install pidgin
```

---

### Post by Elos on 2008-06-08
other clients i do not know but pidgin is a good program for icq and others (msn etc)

---

### Post by Luuka on 2008-06-08
Well, see, that's not the problem. I figured that out eventually, thanks to my friend. He told me that after I posted this thread, but now my mom wants icq on her desktop. I finally got her into Linux, from Winblows, and while I have done icq using pidgin, she wants the full version, i.e. the Winblows one that has an animated avatar you can create. Have you guys seen that before? That's why I was trying to use wine, but it gave me that error? Is it possible at this point, or am I going to have go through the aggravation of reinstalling that terrible os onto a different computer just so that she can have her animated avatar.

---

### Post by yossibin on 2008-11-08
Also ... ICQ supports sending SMS to mobile phone.
Pidgin is good enough to replace MSN (MSN is more user friendly with it's remote help request)

---

