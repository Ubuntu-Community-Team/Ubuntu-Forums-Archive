---
title: "After certain amount of time, Ubuntu becomes unusable"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by Mark Lyons on 2013-09-05
I'm having problems where my computer goes into an unresponsive state. I originally thought this was being set off by something I was doing routinely. However, it appears that this is brought on by time more than anything else. I  tested by starting up my computer and leaving it to sit and I came back  and it was in the same unresponsive state, which is often accompanied  by the following problems:

  
[LIST=1]
[*]Top bar white icons (sound, bluetooth, etc) are flashing in and  out. Sound icon was replaced with hyphens where the "sound waves are"  and that is not the mute icon.

[*]Applications cannot be opened, some are unresponsive.

[*]Unable to shut down or restart. Sometimes I can get to the  dropdown menu by clicking power button, but when I click shut down, the  confirm dialog box does not appear.

[*]If I press power button once, it goes to a terminal like screen and does not proceed past that to shutdown.


[/LIST]
  I have no idea what is happening or how to solve this problem.

---

### Post by cariboo on 2013-09-06
There is probably something running that is using all your resources, you can check this out two ways. First open a terminal and type:

```
top
```

or open System Monitor, and click the Processes list, to see what is using all your resources. Using System Monitor, you can easily stop the process that is using all your resources.

---

### Post by Mark Lyons on 2013-09-08
Looks like 'compiz' at 74m RES is the highest use one. I don't know if that is the problem though. It takes a while and then it randomly stops working.

---

