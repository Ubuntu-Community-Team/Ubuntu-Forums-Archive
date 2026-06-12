---
title: "Screen Dimming During Inactivity Despite Being Set to Not Do So?"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-25
Has anyone else noticed their screen dimming even though dimming is turned off?

---

### Post by mc4man on 2011-08-25
If does so here on 2 setups, around 10 min or so. At least here it has nothing to do with gnome-screensaver, something in the power settings/bios/monitor
Can take care of here through a blanket section in xorg.conf, noting that this doesn't affect the time to dim in gnome-screensaver, 2 different things

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```

---

### Post by moore.bryan on 2011-08-25
I don't have gnome-screensaver installed--don't use it--so I'm at a loss...

---

### Post by mc4man on 2011-08-25
As I see here, (& posted above) - my monitors will 'blank/sleep' after a certain amount of time, this has nothing at all to do with gnome-screensaver

In the past this could be stopped sometimes thru powersaver settings (time to idle, ect.) but the best solution & currently only one is thru a section in  xorg.conf as posted above.

---

### Post by moore.bryan on 2011-08-25
I've the updated Xorg, without a .conf file... I read on one of "bleeders" threads there "shouldn't" be an xorg.conf any longer; perhaps I misunderstood, though.

What I don't understand is why *all of a sudden* the dimming would pop-up as an issue.

---

### Post by lucazade on 2011-08-25
> **mc4man said:**
> As I see here, (& posted above) - my monitors will 'blank/sleep' after a certain amount of time, this has nothing at all to do with gnome-screensaver

In the past this could be stopped sometimes thru powersaver settings (time to idle, ect.) but the best solution & currently only one is thru a section in  xorg.conf as posted above.

I use both the xorg option you mentioned above and some gsettings for the disable completely screensaver and screen blanking

```
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set org.gnome.desktop.session idle-delay 1800
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```

---

### Post by moore.bryan on 2011-08-25
I've made an xorg.conf and used the gsettings suggested by lucazade; dimming continues after several reboots.

---

### Post by MacUntu on 2011-08-25
I've seen this on a second user account as well and got no idea how to disable it. However, I don't see it on my primary ones. This worked fine a couple of days ago.

---

### Post by moore.bryan on 2011-08-25
I'm wondering if one of the latest updates broke this... it wouldn't surprise me.

---

### Post by mc4man on 2011-08-25
You may want to try to see what is dimming the screen
Put back gnome-screensaver and set to 1 min. If it dims then set to 30 min
If it dims before 30 mins then something else is doing it (there is another thread on this where Seeker posted an xorg section that contained another line, maybe try
xorg here - 
> Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection

There is a file you could try deleting - it contains the dim setting, though it will also unset a few other things when deleted - no big deal
~/.config/dconf/user

---

### Post by MacUntu on 2011-08-25
Don't delete that file! It contains all your personal settings.

The dimming starts after 10 seconds here. I suspect it's caused by the power plugin of gnome-settings-daemon.

---

### Post by moore.bryan on 2011-08-25
> **mc4man said:**
> Put back gnome-screensaver and set to 1 min. If it dims then set to 30 min
There aren't any gnome-screensaver settings...

> **MacUntu said:**
> The dimming starts after 10 seconds here. I suspect it's caused by the power plugin of gnome-settings-daemon.
Same for me, but the power plugin has dim unchecked.

---

### Post by mc4man on 2011-08-25
> **MacUntu said:**
> Don't delete that file! It contains all your personal settings.

Please, you make it should like it's holding the family jewels 
All that does is set gsettings back to the defaults, 1 min or less to restore what one may want different
Just did here & had the benefit of clearing an indicator option that showed up w/ todays updates that I've nod need for (omnivision whatever.. - (cheese

---

### Post by MacUntu on 2011-08-25
It's like running 'rm -rf ~/.gconf' &#8594; no, it's not a matter of one minute to restore and *I* wouldn't remember what I've changed (the DB is holding 1000+  entries here).

---

### Post by lvanderree on 2011-08-29
I guess the power-settings screen is being oversimplified! In previous versions of Ubuntu you had the option to enable/disable dimming of the screen when idle when running on battery, but that option has been removed from the config-panel.

I find it very annoying that my screen is dimming automatically. I can't read my papers or websites anymore without me being required to move the mouse, or continue reading things in low brightness!

Isn't this the same issue you are experiencing?

---

### Post by paul_in_london on 2011-08-29
> **mc4man said:**
> If does so here on 2 setups, around 10 min or so. At least here it has nothing to do with gnome-screensaver, something in the power settings/bios/monitor
Can take care of here through a blanket section in xorg.conf, noting that this doesn't affect the time to dim in gnome-screensaver, 2 different things

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```

I did this too - also installed and ran **dconf-editor** and went to 'org --> gnome --> desktop --> screensaver and unchecked the box next to 'idle-activation-enabled'.

See this thread:

[http://ubuntuforums.org/showthread.php?t=1796888&page=2&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=1796888&page=2&highlight=screensaver)

---

### Post by lvanderree on 2011-08-29
Thanks!

This (dconf-editor) was the tool I was looking for, apparantly...

org.gnome.settings-daemon.plugins.power is the key to my issue! I disabled it and now my screen remains bright!

---

### Post by paul_in_london on 2011-08-29
> **lvanderree said:**
> Thanks!

This (dconf-editor) was the tool I was looking for, apparantly...

org.gnome.settings-daemon.plugins.power is the key to my issue! I disabled it and now my screen remains bright!

Glad that helped, even if only indirectly! :)

---

### Post by moore.bryan on 2011-08-30
I'll check this when I get home from work and report back this evening; perhaps we have a solution!

---

### Post by krippa on 2011-09-09
Strangely I have to uncheck the idle-dim-battery for this to work, even though I have the power cable connected. Did anyone else experience this problem is it some incompatibility with my hardware?

I have a Lenovo Thinkpad Edge E420s

---

### Post by MacUntu on 2011-09-09
No, that's the way it currently works. :-/

---

### Post by hotani on 2011-09-16
When I wake up the display after it shuts off, the screen is dimmed to about 10%. I have to adjust the system brightness to get it back.

---

### Post by kansasnoob on 2011-09-16
I only know that I don't get this with Lubuntu, only Ubuntu. And I also get this with Fedora and the default Gnome DE.

I've not bothered trying LXDE w/Fedora to see what happens but I fail to see the point.

IMHO this has to be a flaw in gnome 3. I tend to think the gnome devs focused on eye candy and forgot about functions that effect everyday usage :(

I'm now so happy with Lubuntu I doubt I'll ever go back to gnome.

---

### Post by Quackers on 2011-09-17
> **mc4man said:**
> If does so here on 2 setups, around 10 min or so. At least here it has nothing to do with gnome-screensaver, something in the power settings/bios/monitor
Can take care of here through a blanket section in xorg.conf, noting that this doesn't affect the time to dim in gnome-screensaver, 2 different things

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```
Interesting. I just tried that addition to xorg.conf and now it won't boot at all. If I remove quiet splash I get an "OK" half way down the right side of the (black) screen and that's it! No disc activity, no login screen, nothing.
After a couple more tries I tty'd and removed xorg.conf and rebooted.
Now it will boot fine.
I'm confused. 
I'm using gnome-shell on 64 bit. Would that have anything to do with it?

---

### Post by mc4man on 2011-09-25
At least here the screen 'dimming' or blanking was also affected by DPMS (Energy Star)
So the xorg section was effective in preventing that.
Just ran across this thread which was informative & has an alt. method I like better  - posts 17 & 18
[http://ubuntuforums.org/showthread.php?t=1483345](http://ubuntuforums.org/showthread.php?t=1483345)
( to check - xset -q 
off - xset -dpms
back on - xset dpms

---

### Post by Danilo on 2011-09-26
FWIW, org.gnome.settings-daemon.plugins.power has  the relevant keys, as mentioned above: idle-dim-ac, idle-dim-battery and idle-dim-time. However, default values do not seem to be properly respected by the plugin, but if I "force" the setting (i.e. click the checkbox twice: once to change it, another time to restore it back), it starts working properly. I didn't have to restart Ubuntu or log out and back in, but I did try it out from within GNOME Shell. I didn't see this problem on my desktop (but I also run Unity there, though I suspect that has nothing to do with it, and it's more the fact that this is a laptop).

If this is indeed the case, it sounds like a bug in gnome-settings-daemon that needs to be fixed.

---

### Post by effenberg0x0 on 2011-09-26
I dealt with it on friday. I had one hour to make the HTPC work right or the wife would file for divorce. I threw in all settings I could find and succeeded to avoid dimming, blanking and screensaver. But it was made on a rush: It works, but I don't know exactly which settings are really necessary. 

~/quick_fix.sh
```

#!/bin/bash
# Work dammit

# Disable screensaver start
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome_settings_daemon/screensaver/start_screensaver false

# Disable screensaver locking
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-screensaver/lock_enabled false

# Disable screensaver altogether
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-screensaver/idle_activation_enabled false

# Increase screensaver idle time (max 2h, we set to 10h)
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-screensaver/idle_delay 600

# Disable DPMS screen blank on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t string /apps/gnome-power-manager/ac_dpms_sleep_method off 

gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t string /apps/gnome-power-manager/battery_dpms_sleep_method off

# Disable Computer sleep when on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/ac_sleep_computer 0 

gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/battery_sleep_computer 0

# Disable Display sleep when on AC and battery
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/ac_sleep_display 0 

gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t integer /apps/gnome-power-manager/battery_sleep_display 0

# Disable Dim-on-Idle
gconftool-2 --direct --config-source=xml:readwrite:/etc/gconf/gconf.xml.defaults -s -t bool /apps/gnome-power-manager/dim_on_idle false

# Setterm
setterm -powersave off -blank 0

# xset stuff
xset -dpms
xset dpms 0 0 0
xset s noblank
xset s off

```Regards,
Effenberg

---

### Post by hcon on 2011-10-02
> **paul_in_london said:**
> I did this too - also installed and ran **dconf-editor** and went to 'org --> gnome --> desktop --> screensaver and unchecked the box next to 'idle-activation-enabled'.

See this thread:

[http://ubuntuforums.org/showthread.php?t=1796888&page=2&highlight=screensaver](http://ubuntuforums.org/showthread.php?t=1796888&page=2&highlight=screensaver)


Thanks that worked for me! 

Strange that "Applications -> System Settings -> Display->Dim screen to save power" had no effect though.

---

