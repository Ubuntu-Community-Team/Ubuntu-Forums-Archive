---
title: "Enabling pcmanfm-0.9.9 desktop manager in ubuntu 11.10"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by blade4 on 2012-01-08
Hi all . This has been bugging me for a while now . I've successfully replaced nautilus with pcmanfm but I can't seem to enable its desktop management feature on login . It appears as if the command " pcmanfm --desktop " only works when pcmanfm is actually running . I'm thinking bash scripts here but I am still a bit of a noob . How do I do this ? Any help is appreciated :)

---

### Post by SteveDee on 2012-01-08
> **blade4 said:**
> ...Any help is appreciated :)

Not sure if this helps, but when Lubuntu boots, the autostart file contains this line:-
```

pcmanfm --desktop --profile lubuntu

```

...and there is a file called: /etc/xdg/lxsession/Lubuntu/main.lubuntu that looks like this:-
```

[General]
terminal=lxterminal

[Desktop]
show_wallpaper=1
wallpaper=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
show_wm_menu=1

```

---

### Post by blade4 on 2012-01-09
> Not sure if this helps, but when Lubuntu boots, the autostart file contains this line:-
Code:
pcmanfm --desktop --profile lubuntu



Hi Steve , thanks for the advice . Unfortunately it didn't work for me . ( I assume by autostart you mean /etc/xdg/autostart ) I'm still getting a blank screen on login .

---

### Post by SteveDee on 2012-01-09
> **blade4 said:**
> ...I assume by autostart you mean /etc/xdg/autostart.. .

No, I refer to /etc/xdg/lxsession/Lubuntu/autostart which looks like this:-
```

@nm-applet
@lxpanel --profile Lubuntu
@xscreensaver -no-splash
@gnome-power-manager
@pcmanfm --desktop --profile lubuntu
@/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

```
According to information here: [http://wiki.lxde.org/en/PCManFM_build_and_setup_guide](http://wiki.lxde.org/en/PCManFM_build_and_setup_guide)
...the "lubuntu" in "--profile lubuntu" is the profile name, but this does not seem to refer to a file. Also it does not seem to be case sensitive (see lxpanel ref above). So its probably a recognised (reserved) word. Maybe you need to replace it with "ubuntu".

I couldn't see anything useful in the config files, but I'll gladly post anything you are interested in. Or you could try installing an LXDE Linux (like Lubuntu) to search for anything useful. (maybe install in VirtualBox).

But do let me know if I can be of any help. This looks like an interesting challenge!

------
Edit: OK did a web search for: lxpanel+profile

This shows that (for lxpanel) the profile is stored in ~/.config/lxpanel/<Profile Name>
...which is actually a folder: ~/.config/lxpanel/Lubuntu
...and for pcmanfm: ~/.config/pcmanfm/lubuntu
...which explains the difference in case.

Again, not sure if this helps you.

---

### Post by blade4 on 2012-01-10
Hi Steve , thanks again for the help . I guess Lubuntu config is a bit different from ubuntu . Anyway , I'm gonna keep trying and see if I can't get this to work . 

Cheers :D

---

### Post by ohnonot on 2012-01-11
hello, sorry for jumping in but i was just searching for a very similar thing and this thread is still fresh, so:

i'm trying to get pcmanfm take care of my desktop, too. while still running gnome on ubuntu.
i replaced nautilus with pcmanfm in gconf, desktop/gnome/session/required_components, but no difference on reboot.
with gtweakui or ubuntu-tweak i can tell nautilus to not manage the desktop, that works. i guess i could just add an entry "pcmanfm -d" to autostart, but it *annoys* me (this forum blanks out anything that goes below the waist) that i still have a nautilus process running that takes quite some memory while doing exactly nothing.

it doesn't seem to be possible to uninstall nautilus without uninstalling gnome.

oh btw, is it possible to arrange the desktop icons? move them about?

---

### Post by blade4 on 2012-01-11
Hi ohnonot , I can actually help you here . If you're running ubuntu 11.10 use 

```
sudo gedit /usr/share/applications/nautilus.desktop
``` 

and change the line exec = nautilus to exec = pcmanfm , and reboot. 

Nautilus won't run anymore unless you invoke it from the terminal . 

Oh and by the way, about the problem I was having , I simply went and installed pcmanfm-mod from [ignorantguru's]("http://igurublog.wordpress.com/downloads/mod-pcmanfm/") site . You can also try it if you like - its much better than 0.9.9 . But I don't think either of these allow moving icons on the desktop .  

Cheers :D

---

### Post by ohnonot on 2012-01-11
i used a different solution:
i placed a link in both /bin and /usr/sbin; the link is named nautilus and points to pcmanfm.
i have the feeling that that was a naughty thing to do, but it works fine so far, no more nautilus processes, desktop is all pcmanfm's and everything.

i'm rather having issues with mounting (external) drives now, which happens only manually, not automatically on startup. if anybody knows anything, please let me know.

back to the desktop icons, there must be *some* way to customize them, like horizontal or vertical alignment, restrict to a certain area of the desktop...?
but of course it was my choice to use an explicitely basic desktop manager; just asking.

anyway i've been eyeing the pcmanfm-mod for a while, i guess i'll give it a try right now.

thanks.

---

### Post by ohnonot on 2012-01-11
can't get the key for the ppa, plus there's some unresolvable dependencies...
:-(

---

