---
title: "Replacement for Linux DC++"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-20
I have had it with linuxdcpp!:mad::mad::mad:
It drives me nuts!It freezes every other minute and I just can't use it!Please give me a good linux alternative!!!:(

---

### Post by ruffEdgz on 2008-06-20
That is an interesting P2P application.

The only alternatives to that application would be to use just a bittorrent client like Azureus, Bittornado Client, or something like that. 

The one you want to replace seems like a IRC/P2P client which I have never seen before.

Sorry I can't be any more helpful but my knowledge is limited in this department.

---

### Post by kk0sse54 on 2008-06-20
Sorry I know of no other Linux alternatives. Have you looked into running a DC++ client through wine? Or you can just switch to a whole different p2p network like soulseek, torrents,or amule.

---

### Post by Troll_the_Great on 2008-06-20
Did somebody heard something about dcsharp?
I found it here :[http://code.google.com/p/dcsharp/](http://code.google.com/p/dcsharp/)
I am trying to install it, but it keeps complaining :"sh: gmcs: not found
scons: *** [bin/DCSharp.Base.dll] Error 127"
I don't know how to solve it, and I can't find a .deb file.:(

---

### Post by ruffEdgz on 2008-06-20
In the README file, it talks about getting the scons and I think you can get it here: [http://www.scons.org/](http://www.scons.org/)

I will have to try this since I have never heard of this before. Looks interesting :D

---

### Post by Troll_the_Great on 2008-06-20
I already got scons.I get passed that error by installing "mono-gmcs" but now I got another error, and this one is beyond me:
```
base/Backend/Managers/SegmentStrategy.cs(137,57): warning CS0168: The variable `pair' is declared but never used
Compilation succeeded - 1 warning(s)
gmcs -pkg:ndesk-dbus-1.0 -pkg:gtk-sharp-2.0 lib/notify-sharp/AssemblyInfo.cs lib/notify-sharp/Global.cs lib/notify-sharp/Notification.cs -out:lib/notify-sharp/notify-sharp.dll -target:library
lib/notify-sharp/Notification.cs(92,25): error CS0103: The name `BusG' does not exist in the current context
Compilation failed: 1 error(s), 0 warnings
scons: *** [lib/notify-sharp/notify-sharp.dll] Error 1
scons: building terminated because of errors
```

---

### Post by Troll_the_Great on 2008-06-20
Come on you linux gurus! We need you!:)

---

### Post by Troll_the_Great on 2008-06-21
Did somebody manage to install dcsharp?If yes, please tell me how....:(

---

### Post by alexef on 2008-06-21
> **Troll_the_Great said:**
> I have had it with linuxdcpp!:mad::mad::mad:
It drives me nuts!It freezes every other minute and I just can't use it!Please give me a good linux alternative!!!:(

Give a try to ApexDC++ [http://www.apexdc.net/](http://www.apexdc.net/) through wine. I'm using it regularly, and I'm pretty satisfied with it. There are some minor graphical interface problems (icons, auto-scroll, config window size), but the application is usable.

Hope it helps.

---

### Post by Troll_the_Great on 2008-06-21
Thx, but I tried ApexDC and I wouldn't work so well.I need a good linux client.I found dcsharp, but I don't know how to install it (see the above posts).If somebody could help me...

---

### Post by ThomasNovin on 2008-07-07
Linux DC++ 1.02 was released a couple of days ago. Read [http://ubuntuforums.org/showthread.php?t=193984](http://ubuntuforums.org/showthread.php?t=193984) for info on how to install (isn't any Hardy packages yet AFAIK).

---

### Post by Troll_the_Great on 2008-07-10
I saw the release and I don't know what to do...I hope is more stable that the previous ones...Should I try to compile it from source or wait until a .deb appears?And by the way, nobody manage to install dcsharp?

---

### Post by hittudiv on 2008-12-01
> **Troll_the_Great said:**
> Thx, but I tried ApexDC and I wouldn't work so well.I need a good linux client.I found dcsharp, but I don't know how to install it (see the above posts).If somebody could help me...

apex is working fine with wine...

and u can use Valknut instead of linuxdcpp..
valknut is a little annoying at the beginning..but it simply rox whn u start using it...:popcorn:

---

