---
title: "dota window mode in linux"
date: 2009-05-23
forum: Philippine Team
---

### Post by glitch16 on 2009-05-23
mga sir tanong po paano po ba gagawin para maging window mode ung dota d2 sa ubuntu 8.10. bali napagana ko na po ung dota using wine.tsaka pag nilalaro mo na sya ung cursor di sya lalabas sa window,
pde po ba yun?

---

### Post by badrra on 2009-05-23
Open terminal window run this command:

winecfg

A window comes up, choose Graphics Tab, then put a check mark on "Emulate a virtual Desktop" then choose the size of the window (800x600) etc depende kung anong gusto mong size. 

So lahat ng application using wine will all run on window mode rather than full screen. 

Kung pwede i confine ung mouse sa window na yun lang , yan di ko alam. You may need to research on that.

---

### Post by exkludge on 2009-05-27
gawa ka ng shortcut ng exe mo tapos lagyan mo ng parameter na:

-window


sample:

frozen throne.exe -window

hope this helps ;)

---

### Post by jenue on 2010-04-03
i'm running in window mode but it runs very slow... is there something i have to configure to make this run faster?

---

