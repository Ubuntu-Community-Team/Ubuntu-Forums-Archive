---
title: "How to run minimized application in terminal ?"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by kamrava on 2013-05-26
Hello there.
I saw some topics about this problem, such as ("[Here]("http://askubuntu.com/questions/4876/can-i-minimize-a-window-from-the-command-line") and [Here]("http://askubuntu.com/questions/4876/can-i-minimize-a-window-from-the-command-line")"). But my problem doesn't solved !

I would like run an application in minimized (or system tray)  with terminal.

I tried below but just run application without minimizing :
```
goldendict -systray 
```
and
```
goldendict -min 
```

Any idea? :)

Regards

---

### Post by ajgreeny on 2013-05-26
Install alltray and then start goldendict with the alltray option in the command ```
alltray goldendict
```

---

