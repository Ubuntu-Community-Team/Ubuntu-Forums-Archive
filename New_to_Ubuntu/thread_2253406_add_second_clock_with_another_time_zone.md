---
title: "add second clock with another time zone"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-19
Hi all, 

How do I add in tray second clock with another time zone? 

Lubuntu 14.04.1 LTS

---

### Post by vasa1 on 2014-11-19
Why not use conky?

I have IST (local time) and UTC like this:
```
${time %a, %d %b} ${color B3492B}${time %H:%M}$color ${utime (%H:%M)}
```

---

### Post by marchello_lippi2 on 2014-11-19
Yes, it works great in conky 

${execi 1  date +"%T"}${color C2BAB6} (local)
${tztime America/New_York %H:%M:%S}${color C2BAB6} (NY)
${tztime America/Los_Angeles %H:%M:%S}${color C2BAB6} (LA)

Thanks.

---

