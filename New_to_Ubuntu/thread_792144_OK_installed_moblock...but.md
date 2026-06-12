---
title: "OK installed moblock...but"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-12
Ive just installed moblock (linux peerguardian) and then noticed in small writing on the bottom of the ubuntu community docs that it isn't compatible with firestarter...so how do i remove firestarter? and will it effect anything? lol just worried that it will do what happened before by blocking my internet connection and everything:mad:

---

### Post by kamitsukai on 2008-05-12
moblock isnt blocking anything!!!

---

### Post by jre on 2008-05-13
moblock 0.9rc2 (the "moblock" package) is compatible with firestarter as long as it is started after firestarter. moblock 0.8 (moblock-nfq and moblock-ipq) are indeed not compatible with firestarter.

Are you sure that it doesn't block anything? Please try "moblock-control test" and "moblock-control status"

---

