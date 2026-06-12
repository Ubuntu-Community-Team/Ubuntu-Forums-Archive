---
title: "installation error : resource/jre/bin/java: Permission denied"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by then_dude on 2013-05-05
hello 

i'm trying to install a software. 
it's a plc software for Siemens Logo software. 

it can be found here. 

[http://www.automation.siemens.com/mcms/programmable-logic-controller/en/logic-module-logo/demo-software/pages/default.aspx#Demo%20software](http://www.automation.siemens.com/mcms/programmable-logic-controller/en/logic-module-logo/demo-software/pages/default.aspx#Demo%20software)

when i try to install it: sudo sh ./Setup.bin

i get the next error. 

[I]
Launching installer...

exec: 2470: /tmp/install.dir.8681/Linux/resource/jre/bin/java: Permission denied[/I]

could somebody shed a light on a possible problem. 

thanks

---

### Post by 3rdalbum on 2013-05-05
```
sudo chmod a+x /tmp/install.dir.8681/Linux/resource/jre/bin/java
```

will add execute permission to that file, which I imagine the lack is the cause of the "Permission denied" error.

---

### Post by then_dude on 2013-05-05
thanks, 

but saddly  it does not work

any other ideas ?

---

### Post by hendrel on 2013-05-19
Have you posted this question on the Siemens forum?

---

