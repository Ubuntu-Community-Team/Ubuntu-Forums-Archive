---
title: "[SOLVED] Openbox Start-Up Script"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by saj0577 on 2008-11-08
At the minute I am using:
```

#!/bin/sh 
openbox &
eval `cat $HOME/.fehbg` &
gedit
```

As my start-up script all works perfectly unless I close down gedit and then it logs me out.
I obviously dont want to have to keep gedit open so I tried:
```

#!/bin/sh 
openbox &
eval `cat $HOME/.fehbg` &

```
and
```

#!/bin/sh 
openbox &
eval `cat $HOME/.fehbg

```

and it wont log in and with the other one it will log in but openbox does not work i.e right click menu not active.

How can I remove gedit from the script but keep it working as I dont want to have to keep gedit open at all times.

Saj

---

### Post by eriqjaffe on 2008-11-08
I'm pretty sure that the last command has to end with a "&" as well.

---

### Post by saj0577 on 2008-11-09
```
#!/bin/sh 
openbox &
eval `cat $HOME/.fehbg` &
gedit &
```
Does not load the openbox part fully (the title bar with minimize,maximise,close does not appear.) Also the right click menu does not work.


```
#!/bin/sh 
openbox &
eval `cat $HOME/.fehbg` &
gedit
```

No matter what program I replace gedit with when I close that program down it logs me out.

Saj

---

### Post by kukibird1 on 2008-11-09
Try:

#!/bin/sh 
eval `cat $HOME/.fehbg` &
gedit & 
openbox &

or [http://icculus.org/openbox/index.php/Help:Autostart]("http://icculus.org/openbox/index.php/Help:Autostart")

---

### Post by saj0577 on 2008-11-09
```
#!/bin/sh
feh --bg-scale "hello.JPG"
exec openbox

```

Works.

Saj

---

### Post by urukrama on 2008-11-10
If you use the autostart.sh file (default in /etc/xdg/openbox, your modified copy in ~/.config/openbox) you shouldn't add *openbox &* or *exec openbox* to the list. Have a look at the [Openbox documentation]("http://icculus.org/openbox/index.php/Help:Autostart") or my Openbox guide (link in signature) to understand how Openbox's autostart file works.

---

