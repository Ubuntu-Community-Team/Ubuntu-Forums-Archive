---
title: "[SOLVED] synaptec update manger and add remove not working"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-04
basically im getting this message that no programs support my amd64 settings.```
OpenOffice.org Office Suite cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
```

example i cannot install ubuntu restricted extras and the systems states that it is up todate although ive had it up for at least 3 days and in perspective updates were available immediately all other times i installed ubuntu kubuntu xubuntu etc

---

### Post by schmidtbag on 2008-09-04
if this is a fresh install i'd first of all recommend you get 32 bit ubuntu.  64 bit, to me, only seems practical for servers.

i remember hearing a while back about force installing.  obviously a SU task, this allows you to install something whether you get errors or not.  i wish i knew exactly what the terminal code was, but it shouldn't be hard to find.

also, why isn't OOo already installed?  or, why don't you install it from the repositories?  if neither of those things are the case then just go to their website and download the 64 bit version, if available

---

### Post by philinux on 2008-09-04
In a terminal use this and post back the output.

```
uname -m
```

64 bit works just fine. Flash Java everything.

---

### Post by PatrickMoore on 2008-09-04
> **philinux said:**
> In a terminal use this and post back the output.

```
uname -m
```

64 bit works just fine. Flash Java everything.

sorry guys it was an issue with my repositories i resolved it rather simply when i was pointed in the right direction thank you though

---

