---
title: "strange unresolvable dependancies and removed programs after update"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by DGINSD on 2012-01-17
So I installed the XFCE4 package cause Ubuntu was just too slow on my pile O junk, that went fine, afterwards I thought it had been a while since my system notified me an update was needed so I did a manual one. It looked a little different than it usually does but I didn't think much of it, during this upgrade it removed a bunch of packages some having to do with multimedia (I tried finding a list but I don't know how) FFMPEG was one it removed my DVD95 and my K9Copy. I tried to just re-install K9 and DVD95bu they say they need FFMPEG and I get dependency issues when I try to install that. All this from a simple update I'm totally lost?!??! Please Help?

---

### Post by llamabr on 2012-01-17
It may be helpful if you would post the actual error, or the actual output.  That is, from a terminal, post the output of:

```
sudo apt-get install ffmpeg
```

---

### Post by DGINSD on 2012-01-17
Ok I'm really confused, get this it installed just fine with the BASH command so I  used apt-get to install dvd95 and k9, no problamo. Is there something wrong with synaptic and or update manager that caused this? How do I fix it just reinstall? I tell u the longer I use Linux the more and more I realize the command line is king.

---

### Post by mcduck on 2012-01-18
> **DGINSD said:**
> Ok I'm really confused, get this it installed just fine with the BASH command so I  used apt-get to install dvd95 and k9, no problamo. Is there something wrong with synaptic and or update manager that caused this? How do I fix it just reinstall? I tell u the longer I use Linux the more and more I realize the command line is king.

Synaptic, Update Manager and Ubuntu Software Center all use exactly the same repositories and underlying package management tools that apt-get uses. So there shouldn't be any difference between them.

Perhaps the software repository you are using was just updating it's contents at the moment, or having some kind of problems, and simply waiting a bit was what fixed the issue?

---

### Post by DGINSD on 2012-01-18
The thing that got me was why did update manager remove that stuff in the first place.

---

