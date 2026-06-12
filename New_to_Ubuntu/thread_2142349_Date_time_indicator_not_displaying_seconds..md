---
title: "Date time indicator not displaying seconds."
date: 2013-05-05
forum: New to Ubuntu
---

### Post by gtaskeraus on 2013-05-05
I want the clock at the top of the screen to display seconds.  The seconds disappeared after I upgraded from 12.10 to 13.04.  My attempts at doing so are unsuccessful and I'm stuck at how I just might get it to display the seconds in the time.  I've tried the standard settings via the configuration editor in both the "language support" and "Date & Time"  with no joy on either of those.

Any other ideas?

---

### Post by ibjsb4 on 2013-05-05
We are running different setups, but I can just right click on the time to add seconds.

---

### Post by Cheesehead on 2013-05-05
> **gtaskeraus said:**
>  I've tried the standard settings via the configuration editor in both the "language support" and "Date & Time"  with no joy on either of those.

Do you mean that the settings exist, but do not work? (bug report)
Or do you mean that the settings are no longer shown on those control panels?

---

### Post by MaZaMo on 2013-05-05
Click on the time in the bar and then on the dropdown click time and date settings. If you go to the clock tab there is an option for seconds. Are you saying that doesn't work?

---

### Post by stylintile on 2013-05-06
You didn't specify which flavor of Ubuntu you are using, and some are different.  On my Xubuntu, to add seconds I change the format from:
```
%H:%M
```
 to
```
%H:%M:%S
```

Hope this helps

---

### Post by Frogs Hair on 2013-05-06
Seconds can be toggled on and off in the Tweak Tool for Unity. If not installed use the software center or the following. ```
 sudo apt-get install gnome-tweak-tool 
```

---

### Post by gtaskeraus on 2013-05-06
> **Cheesehead said:**
> Do you mean that the settings exist, but do not work? (bug report)
Or do you mean that the settings are no longer shown on those control panels?

The second one.  In other words I go into the settings but there is nothing there to allow me to turn on the seconds display.  I'm running the Gnome desktop ubuntu 13.04.  Is there something in the gnome registry or even a command line work around that can make this happen?

---

### Post by lovebluesky2009 on 2013-05-06
I do not like show seconds, I and i used xubuntu, the methods are mentioned above

---

### Post by steeldriver on 2013-05-06
I haven't played with 13.04 yet, but in 12.04 it's in the /com/canonical/indicator/datetime/ schema - you can manipulate it via dconf (you may need to install the dconf command line tool - the package is called dconf-tools iirc)

```

$ dconf dump /com/canonical/indicator/datetime/

[/]
show-date=false
show-day=true
[COLOR=#ff0000][B]show-seconds=false
[/B][/COLOR]time-format='24-hour'
$

```

```

$ dconf read /com/canonical/indicator/datetime/show-seconds
false
$
[B]$ dconf write /com/canonical/indicator/datetime/show-seconds 'true'
[/B]$
$ dconf read /com/canonical/indicator/datetime/show-seconds
true
$

```

Or you can install the GUI dconf editor, which should give you GUI access to settable keys even if they aren't presented in the default configuration dialog

---

### Post by monkeybrain2012 on 2013-05-07
> **gtaskeraus said:**
> The second one.  In other words I go into the settings but there is nothing there to allow me to turn on the seconds display.  I'm running the Gnome desktop ubuntu 13.04.  Is there something in the gnome registry or even a command line work around that can make this happen?

Install the gnome-tweak-tools and then look for "advanced settings", open it and go to "shell" and change the clock setting.

---

### Post by gtaskeraus on 2013-05-08
> **monkeybrain2012 said:**
> Install the gnome-tweak-tools and then look for "advanced settings", open it and go to "shell" and change the clock setting.

Thanks!  This seemed to do it for me although I also had a go with steeldriver's recommendation as well.  It may have been both that helped.  Whatever it is working now.

---

