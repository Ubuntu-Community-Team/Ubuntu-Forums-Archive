---
title: "Unable to connect to wireless anymore?"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by Proto Blaze on 2011-10-27
Ok so I hopped on my Ubuntu partition for the first time in about almost 3 weeks. But something different happened... It won't connect to my wireless... I spent about 30 minutes trying to connect to it but it failed every single time. It detects it just fine, and my Windows 7 side connects just fine... so what gives? Please help... I miss Ubuntu lol

---

### Post by Proto Blaze on 2011-10-27
Le Bumpe

---

### Post by Diametric on 2011-10-27
Could you give a little more info?  Does Ubuntu "see" the signal?  Has anything changed in your network config?

---

### Post by Proto Blaze on 2011-10-27
yes, I did state in my first post that it detects it. Nothing has changed... last time I used ubuntu (18 days ago) it worked just fine... now it just wont connect. It sees it... but fails every time I connect

---

### Post by gandaran on 2011-10-27
> **Proto Blaze said:**
> Ok so I hopped on my Ubuntu partition for the first time in about almost 3 weeks. But something different happened... It won't connect to my wireless... I spent about 30 minutes trying to connect to it but it failed every single time. It detects it just fine, and my Windows 7 side connects just fine... so what gives? Please help... I miss Ubuntu lol
any kernel or drivers update that could have messed up?
what is the wireless chipset brand and drivers installed?
and the wireless router is it still the same one with the same configurations?

---

### Post by Proto Blaze on 2011-10-27
> **gandaran said:**
> any kernel or drivers update that could have messed up?
what is the wireless chipset brand and drivers installed?
and the wireless router is it still the same one with the same configurations?

Yes, same router, same config... nothing at all changed. I updated nothing so it confuses me as to why it doesn't work.. I might reformat and start over with linux

---

### Post by wolfen69 on 2011-10-27
> **Proto Blaze said:**
> I updated nothing

Maybe you *should* update and reboot.

---

### Post by Proto Blaze on 2011-10-27
> **wolfen69 said:**
> Maybe you *should* update and reboot.

Yea how can I update with no connection? It was working fine last time I used it... >_>

---

### Post by gandaran on 2011-10-28
try wiping all connections on the network manager wireless tab then reboot and see if it works.
if not paste the output of
```
rfkill list
```

---

