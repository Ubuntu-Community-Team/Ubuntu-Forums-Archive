---
title: "CompizConfig, hot corners not working"
date: 2015-09-13
forum: New to Ubuntu
---

### Post by greentea2 on 2015-09-13
Hello I´ve installed the Compiz Configurator on my Ubuntu 14.04 in order to use the hot corners, but it does n´t work. I think I followed all the basic instructions - also installed in Synaptic Compiz-plugins-exra. 

The corners I´ve tried to setup is are:
General Options/Key Binding/Show Desktop > Bottom Right
Windows Management/Scale/Bindings/initiate windows picker > Bottom Left (scale enabled!)

Really would appreciate any comments! ;)

__
....Besides is there an option to put a custom command for a hot corner. I would like to have an hot corner option for "shut down"

---

### Post by CantankRus on 2015-09-13
Both of those settings work for me in 14.04 with or without the **compiz-plugins** package.
Sometimes you may have to log out and back in after a change.
What does this terminal command give you....
```
dconf read /org/compiz/profiles/unity/plugins/core/show-desktop-edge
```
eg mine...
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] dconf read /org/compiz/profiles/unity/plugins/core/show-desktop-edge**
'BottomRight'
```

PS: **compiz-plugins-extra** is a [**_[COLOR="#B22222"]transitional dummy package[/COLOR]_**]("http://askubuntu.com/questions/20377/what-exact-purpose-have-transitional-packages") which just installs the **compiz-plugins** package as a dependency.

---

### Post by monkeybrain20122 on 2015-09-13
Doesn't work in what way? That it doesn't work at all or after reboot? There have been problems with the scale addon forgetting hot corners after reboot. The workaround: in ccsm go to Preferences > Plugin List to disable automatic plugin sorting and then move scale to the very bottom of the list (or close to the bottom. It seems that since 14.04 if you put it below unity plugin it will kill the desktop so it has to be above unity, the bottom two or three works ok)

---

### Post by greentea2 on 2015-09-15
Sorry, for my late answers! I have been out for some days. I am using 14.04 on one laptop and 15.04 on VB as guest at another laptop and both times this problem with Compiz. Here my answers/questions: 

> **monkeybrain20122 said:**
> Doesn't work in what way? That it doesn't work at all or after reboot?Exactly !! ..after rebooting. 

> **monkeybrain20122 said:**
> There have been problems with the scale addon forgetting hot corners after reboot. The workaround: in ccsm go to Preferences > Plugin List to disable automatic plugin sorting and then move scale to the very bottom of the list (or close to the bottom. It seems that since 14.04 if you put it below unity plugin it will kill the desktop so it has to be above unity, the bottom two or three works ok)I have tried it, putting it on the bottom, playing around, but still no reaction. :frown:

---

### Post by greentea2 on 2015-09-15
> **CantankRus said:**
> Both of those settings work for me in 14.04 with or without the **compiz-plugins** package.
Sometimes you may have to log out and back in after a change.
What does this terminal command give you....
```
dconf read /org/compiz/profiles/unity/plugins/core/show-desktop-edge
```
eg mine...
```
**[COLOR=#006400]glen@Trusty:~$[/COLOR] dconf read /org/compiz/profiles/unity/plugins/core/show-desktop-edge**
'BottomRight'
```

  
...but how you can define on which hot corner you want to put which command?

---

### Post by CantankRus on 2015-09-15
You said you were using Compiz Configurator which I took to mean **compizconfig-settings-manager** (ccsm)
which is all you need.
But as monkeybrain20122 said, hot corners and and edge triggers have been a bit flakey for a while now so try his solution.

I have a couple of edge triggers+mouse1 set up to run commands which disappear after a logout.
Running ```
compiz --replace
```
restores them.

---

### Post by monkeybrain20122 on 2015-09-15
> **greentea2 said:**
> 

I have tried it, putting it on the bottom, playing around, but still no reaction. :frown:

Then try this. Copy these into your text editor, save it under a name like, e.g, hotcornerfix.sh. 

```
#!/bin/bash
#fix scale hot corner
sleep 6
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"Disabled"'
sleep 1
dconf write /org/compiz/profiles/unity/plugins/scale/initiate-all-edge '"TopLeft"'
exit 0
```

Make it executable (either right click and check the box in Properties, or "chmod +x /path/to/script") Then run it automatically every time you boot by adding it to Startup Applications (search for it in Dash and add the script to it)

This basically disables and re-enables the hot corners automatically. Since this has to happen after loading the desktop, you may need  to change sleep 6 to other values depending on how long it takes your desktop to load(e.g my desktop loads rather fast so 6 is good, but if your desktop takes 10 sec to load then you would want to set it to 12 etc, always give sufficient time for desktop to load) I use this for one machine and it works quite seamlessly (the other machine remembers without any funny workaround. So I think it has to do with hardware somehow)

---

### Post by mc4man on 2015-09-15
The 'General Options/Key Binding/Show Desktop > pick a spot' is a loser here also. It works once per session then dies off
The scale one should work as long as you're not picking Initiate Window Picker for Window Group which can only be enabled via a command & dbus & has to be integrated to last more than a few days if you do shutdowns/restarts, ect.

So for the scale one try - 
open ccsm > scale > bindings. For the one you're trying to set click on the x icon to far right, will set to none. Then re-enable but pick a spot you don't want & aren't currently using. From there reset to the spot you do want (bottom right.) See if it works.
Edit: or use above post which may also work, missed it as this forum performs like crap for me at times...

As far as Show desktop you could use the command plugin & xdotool (xdotool key ctrl+super+d) but user created commands tend to disappear as mentioned

---

