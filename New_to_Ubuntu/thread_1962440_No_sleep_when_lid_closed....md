---
title: "No sleep when lid closed..."
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Futant on 2012-04-21
Hello, I am running Ubutu 11.10 on a Dell XPS L502x and almost everything works perfectly...the only problem I'm having at the moment is when I close the lid the poor thing won't sleep! I have set it to suspend when lid closed in power settings, and suspend works fine from the desktop. Not a big deal, just curious if anyone can help? I saw a similar thread from a couple of years ago, didn't help though, hopefully someone can now. Ta!

---

### Post by hakermania on 2012-04-21
If you get your hands a little dirty you may solve this. This is how to capture the event that lid is closed: 
[http://ubuntuforums.org/archive/index.php/t-1076486.html](http://ubuntuforums.org/archive/index.php/t-1076486.html)
And that's the custom command you have to run in order to put it in suspend:


```
dbus-send --system --print-reply --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend
```

The command works fine for me, so you shouldn't have any problem with this. But let us know whether the tutorial on how to capture the lid close action is outdated or something and you cannot follow!

---

