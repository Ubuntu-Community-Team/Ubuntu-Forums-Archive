---
title: "Start up"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by dragon2600 on 2012-07-13
Hi is there anyway to find out when the few time my ubuntu machine was started?

Thanks.

---

### Post by codemaniac on 2012-07-13
> **dragon2600 said:**
> Hi is there anyway to find out when the few time my ubuntu machine was started?

Thanks.

In a commandline (press alt+ctrl+T) use the **uptime **command .

```
uptime
```

[COLOR=#111111][FONT=Arial]The below command will  display the time of last system boot.
```
who -b 
```
 [/FONT][/COLOR]

---

### Post by dragon2600 on 2012-07-13
Im sorry I missed a word out from the OP I need to find out the last few times the machine was started.

Thanks

---

### Post by dargaud on 2012-07-13
the command 'last' lists logins and reboots, with dates.

---

### Post by codemaniac on 2012-07-13
The below command will display the system shutdown entries and run level changes.

```
last -x
```

refer man pages for more information .

```
man last
```

---

