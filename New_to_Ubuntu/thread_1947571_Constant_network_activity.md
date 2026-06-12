---
title: "Constant network activity"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by roodypoo on 2012-03-26
After running the netstat command I see a connection I would like to investigate. How do I find out what process is using the connection?

---

### Post by Ms. Daisy on 2012-03-27
You could post it here. Or you could Google the connection name.
```
man netstat
``` will give you commands to use with netstat for further investigation as well.

---

### Post by Ms. Daisy on 2012-04-03
Better late than never...
 
The command you want is
 
```
 watch netstat -anlpee 
```

---

