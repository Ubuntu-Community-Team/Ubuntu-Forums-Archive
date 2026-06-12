---
title: "Isolate IP Address as a Variable"
date: 2009-11-25
forum: Programming Talk
---

### Post by dr_latino999 on 2009-11-25
I'm trying to isolate a systems IP address so as to make it a variable in a script I am creating, and I haven't figured out exactly how to do it. Most Google searches just reference the act of viewing a systems IP by using the **ifconfig** command and using the ol' eyeball, which really doesn't help in this case. The closest I have come is the following:
**Input**
```
ifconfig |grep "inet addr"

```[B]Output
[/B]```
inet addr:192.168.64.132  Bcast:192.168.64.255  Mask:255.255.255.0
          inet addr:127.0.0.1  Mask:255.0.0.0
```But this outputs too much additional information. How would I go about just returning the address of 192.168.64.132?

---

### Post by diesch on 2009-11-25
```
LANG=C ifconfig eth0 | awk -F'[: ]+' '/inet addr:/ {print $4}'
```

---

### Post by dr_latino999 on 2009-11-25
deisch, thank you for the prompt assistance, that is exactly what I was attempting to do.

---

