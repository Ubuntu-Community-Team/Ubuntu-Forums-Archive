---
title: "Default gateway"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by StrangerSa on 2012-10-01
Hi Guys, how do I find my default gateway ?

---

### Post by The Cog on 2012-10-01
Use the command ```
route
``` or ```
route -n
``` for numeric output.

---

### Post by androssofer on 2012-10-01
> **StrangerSa said:**
> Hi Guys, how do I find my default gateway ?

do:

```
route -n
```

the gateway is at the bottom:

usually something like:

```
192.168.0.0
```

---

### Post by grahammechanical on 2012-10-01
click on the Network Manger icon and select Connection Information if you are connected.

The gateway is the same as the default route, which is usually the same as the Primary DNS. If I am correct, of course.

It also seems to be the same as the http:// address that is used to log into the router/hub for administration purposes.

Regards.

---

### Post by StrangerSa on 2012-10-01
Thank you very much guys
@ Grahamm

can't find a network manager icon.?

---

### Post by pqwoerituytrueiwoq on 2012-10-01
you can run [FONT=Courier New]nm-tool[/FONT] in a terminal to get the connection information
if you only want the gateway address:
```
nm-tool | grep Gateway | awk '{print $2}'
```

---

