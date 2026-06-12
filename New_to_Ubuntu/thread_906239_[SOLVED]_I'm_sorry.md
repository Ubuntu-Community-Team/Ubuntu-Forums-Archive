---
title: "[SOLVED] I'm sorry"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-08-31
A bit pissed here.
I followed this guy's tutorial on here:
[http://ubuntuforums.org/showthread.php?p=5699001#post5699001](http://ubuntuforums.org/showthread.php?p=5699001#post5699001)

And he totally screwed up my computer.
I mean, I can't get the lockscreen to work, and I want to undo everything he said to do, but I don't know how.

Can you just tell me how to do that, or at least just get lockscreen to work. I'm running Hardy Heron

---

### Post by nothingspecial on 2008-08-31
Beware following very old tutorials. This was written in 2006 about Dapper.
It probably doesn`t apply anymore.

Excuse my ignorance but what is a lockscreen. If I new that I might be able to help.

---

### Post by arch0njw on 2008-08-31
We all definitely get frustrated.  The community is generally quite willing to help.  It looks like a couple of commands go changed.  Have you attempted going backwards through the steps and unsetting/resetting the commands?

---

### Post by nothingspecial on 2008-08-31
Your system is no hosed, this is fixable. Just undo what you have done.

System > prefrences > sessions and uncheck xscreensaver -nosplash in the startup programs tab.

Reboot.

System > preferences > main menu > system > preferences > screensaver -
Right click, select properties and in the command tab type
```
gnome-screensaver-preferences
```
```

sudo apt-get remove xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```

Then go to both power management in system > preferences and set them how you like.

Remove the launcher from the panel if you ever got one.

Hope that helps.

---

### Post by Rhubarb on 2008-08-31
nothingspecial is correct, this should not be hard to undo at all.
I had replied to the original howto thread here:
[http://ubuntuforums.org/showpost.php?p=5699145&postcount=4](http://ubuntuforums.org/showpost.php?p=5699145&postcount=4)
There is a more detailed description of how to do it there.

---

### Post by Elephantman5 on 2008-08-31
> **nothingspecial said:**
> Your system is no hosed, this is fixable. Just undo what you have done.

System > prefrences > sessions and uncheck xscreensaver -nosplash in the startup programs tab.

Reboot.

System > preferences > main menu > system > preferences > screensaver -
Right click, select properties and in the command tab type
```
gnome-screensaver-preferences
``````

sudo apt-get remove xscreensaver xscreensaver-data-extra xscreensaver-gl-extra
```Then go to both power management in system > preferences and set them how you like.

Remove the launcher from the panel if you ever got one.

Hope that helps.

> **Rhubarb said:**
> nothingspecial is correct, this should not be hard to undo at all.
I had replied to the original howto thread here:
[http://ubuntuforums.org/showpost.php?p=5699145&postcount=4](http://ubuntuforums.org/showpost.php?p=5699145&postcount=4)
There is a more detailed description of how to do it there.

I over exaggerated. It was just that one command 
```

sudo chmod +x /usr/bin/gnome-screensaver
```that bothered me. Sorry, again.
Kudos, and I'll give thanks to the guy who wrote that uninstall guide out!

> **nothingspecial said:**
> Your system is no hosed, this is fixable. Just undo what you have done.

...

Hope that helps.

Sorry dude. Heh...maybe i was just really tired. :)

---

### Post by nothingspecial on 2008-08-31
Glad you got it sorted

:guitar:

---

