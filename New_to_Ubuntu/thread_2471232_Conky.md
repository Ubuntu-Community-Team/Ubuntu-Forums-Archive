---
title: "Conky"
date: 2022-01-24
forum: New to Ubuntu
---

### Post by annieuk on 2022-01-24
Anyone able to get Conky to launch at startup on Ubuntu 21.10? I have added it to the startup apps and added --pause=60 to the conky command, it just does not want to display :( unless you launch it manually quite a time after the PC has booted up

---

### Post by ActionParsnip on 2022-01-24
if you make a script to pause, then launch conky, you can run the script in the startup item and should help

Run something like
```

sudo vi /usr/bin/delayconky; sudo chmod +x /usr/bin/delayconky

```

Then add the below:
```

#!/bin/bash
sleep 60
conky

```

(Or whatever command you run conky with). Then edit your startup item and make it run "/usr/bin/delayconky" instead.

Should do it.

---

### Post by annieuk on 2022-01-24
Thanks [ActionParsnip]("https://ubuntuforums.org/member.php?u=1079078")[COLOR=#000000] but I've already tried that and it does not work :(

Edit: Using HTOP conky seems to have the usual 5 entries running but nothing is displayed on screen until I manually start conky myself[/COLOR]

---

### Post by T6&amp;sfpER35% on 2022-01-24
you could try installing **Stacer** and from there choose startup apps?
[https://oguzhaninan.github.io/Stacer-Web/]("https://oguzhaninan.github.io/Stacer-Web/")

---

### Post by annieuk on 2022-01-24
Why would that be any different to the Ubuntu default **Startup Application** app? It seems to be another interface to exactly the same task

---

### Post by annieuk on 2022-01-24
Done another web search and came across a script that works :)

```
[FONT=var(--ff-mono)]#!/bin/sh
[/FONT]
/usr/bin/conky -d
sleep 5
killall -SIGUSR1 conky
```

Conky then comes up practically instantly with all the other desktop icons :)

Hope this helps anyone else having the same issue with Ubuntu 21.10

Thanks for those who tried to help

---

