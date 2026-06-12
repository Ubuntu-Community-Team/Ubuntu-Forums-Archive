---
title: "vlc help"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-13
i am using xubuntu(main os) & Ubuntu(desktop installed) in 11.10 in my pc .i have a problem with vlc in xubuntu . i cant find the bottom end in it . its working performance also not good . 


thanks in advance

---

### Post by mc4man on 2011-09-13
Don't know xubuntu but there is a current longstanding issue in ubuntu 11.10, a window that extends forever to the bottom is one of the bad effects.
you can try this - 
install qt4-qtconfig
open it up & change the gui style to something other than the default which is gtk+ (clearlooks is good

Then open home folder, browse to .config/vlc/ and delete vlc-qt-interface.conf

current 11.10 bug, affects more than vlc
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303)

---

### Post by raja.genupula on 2011-09-14
thank you very much ,  i will do it when i get back to my room & i will post here what i got .

---

### Post by raja.genupula on 2011-09-14
> **mc4man said:**
> Don't know xubuntu but there is a current longstanding issue in ubuntu 11.10, a window that extends forever to the bottom is one of the bad effects.
you can try this - 
install qt4-qtconfig
open it up & change the gui style to something other than the default which is gtk+ (clearlooks is good

Then open home folder, browse to .config/vlc/ and delete vlc-qt-interface.conf

current 11.10 bug, affects more than vlc
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303)

hey 
thank you very much , its working . now everything fine with vlc .

---

### Post by raja.genupula on 2011-09-14
my vlc problem in xubuntu 11.10 got solved by the advice of mc4man . but in ubuntu 11.10 its still . here it is a different problem . its slowly loading like a movie screen . very slow loading . i choose banshee also, but that also not working in my Ubuntu 11.10 . 

help me with this guys 
thanks in advance

---

### Post by raja.genupula on 2011-09-15
hi guys , please make a look at my thread

---

### Post by raja.genupula on 2011-09-17
well i have reported in launchpad 
closing this 
thanks to all who pick this.

---

