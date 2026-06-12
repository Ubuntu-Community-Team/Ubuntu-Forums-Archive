---
title: "Macro on Lock Screen?"
date: 2013-03-23
forum: Programming Talk
---

### Post by dberm22 on 2013-03-23
Hi all! New to the forum...

I am running the standard gnome screensaver and I am trying to detect when the lock screen shows so that I can run a macro when it does. I looked in gnome-screensaver-command, but could not find anything. All my macro would do would be to simulate the tab key and then the enter key to bring me to a new menu which I find much more attractive as a lock screen. There might be better ways to do this, but this seems like it would be the easiest option. Any ideas on how I can accomplish this?

I've seen this, but I dont follow: [http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock](http://unix.stackexchange.com/questions/28181/run-script-on-screen-lock-unlock)

Thanks

---

### Post by dberm22 on 2013-03-25
Wow, thanks for nothing :P. 

Anyway, for everyone else who might have this same problem, I wrote a script to lock the screen which i named "switchuserlock.sh":

```

#!/bin/sh
# Use "Switch User" screen as lock screen


gnome-screensaver-command -l
xdotool key Alt+w
xdotool key KP_Enter

```

And I use xautolock to launch it. I added this line to my etc/rc.local file

```

xautolock -time 10 -locker "switchuserlock" &

```

But it's not working. Can anybody tell why?

---

