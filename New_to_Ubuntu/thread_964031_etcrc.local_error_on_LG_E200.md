---
title: "/etc/rc.local error on LG E200"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by nnamdi on 2008-10-30
how do i get to fix this cause my young brother got a LG E200 laptop but when i try running ubuntu or linux mint live cd or want install but it get to a point were i cant get through pls how do i get to fix this

```

*Starting deferred executionscheduler atd                    [ok]
*Starting periodic command scheduler crond                   [ok]
*checking batttery state...                                  [ok]
*Runnung local boot script (/etc/rc.local)                   [ok]

```

that is where it stops or hangs with the cursor blinking
and i also noticed that the graphic is an ATI card thank you

---

### Post by tjwoosta on 2008-10-30
well etc/rc.local is an empty script by default
(it doesn't do anything)


i dont think it is the cause of your problems
> 
*Starting deferred executionscheduler atd                    [ok]
*Starting periodic command scheduler crond                   [ok]
*checking batttery state...                                  [ok]
*Runnung local boot script (/etc/rc.local)                   [ok]


its probably the next item in line that is causing the problem (what that would be, i have no idea)

---

