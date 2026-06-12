---
title: "SetWindowsHookEx, ToAscii, and dead keys"
date: 2008-08-01
forum: Programming Talk
---

### Post by nanotube on 2008-08-01
A question about some tricky bits of windows api (sorry, i know this is an ubuntu forum, but i am hoping that some of you experienced guys might have some windows knowledge still rattling around in your brains :) )

there's a bug in the pyhook library that breaks dead keys (the ones that let you type accented and tilda-ed and umlauted letters), which appears to be caused by some funky behavior of the ToAscii function (which also occurs in ToAsciiEx, ToUnicode, ToUnicodeEx - so there's no simple workaround just to use an alternate). 

Please see this bugreport thread here for details, and my latest post there with the best explanation i could find:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1624870&group_id=65529&atid=511317](http://sourceforge.net/tracker/index.php?func=detail&aid=1624870&group_id=65529&atid=511317)

I am still not clear what exactly it is that ToAscii function resets/clears/breaks to screw up the deadkeys, and how exactly to stop it from doing it (or to properly restore the state after it does it).

Could someone please explain this to me in detail to help me fix this bug (or point me to some good detailed documentation - the MSDN api reference does not mention this issue).

---

