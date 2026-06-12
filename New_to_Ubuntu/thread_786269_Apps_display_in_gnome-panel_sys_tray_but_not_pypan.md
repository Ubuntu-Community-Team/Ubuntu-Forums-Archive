---
title: "Apps display in gnome-panel sys tray but not pypanel"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-05-08
I use Openbox for its light resource usage as it makes my computer really fast. There's a problem, though. Some programs only appear on gnome-panel so it makes it tough to use them, especially if they're entirely dependent on the gnome-panel.

For example, the update-manager does not appear in my system tray. I can still access it by using the command, though.

I have a problem mostly with klipper and glipper. Apparently they use the system tray in KDE/GNOME respectively and they don't appear in pypanel, the panel I'm currently using. Which sucks, because they only run in the system tray. I'd rather not run gnome-panel just to get access to it... it's far too slow for my liking and I don't like it too much. 

If anyone can provide help, thanks.

---

### Post by angry_johnnie on 2008-05-08
Just add ```
update-notifier &
``` to your **autostart** file (something like /home/YOU/.config/openbox/autostart.sh

It should be the same for anything else.
Here's mine, for instance:

```
#!/bin/sh
gnome-volume-manager &
numlockx on &
eval `cat $HOME/.fehbg` &
pypanel &
nm-applet --sm-disable &
update-notifier &
tomboy &
```

So, nm-applet, update-notifier and tomboy all go automatically into pypanel's system tray.

---

### Post by -{Luther}- on 2009-02-06
I think that the correct path of the autostart file is /etc/xdg/openbox/autostart.sh, at least in openbox3.
So type:
```
sudo nano /etc/xdg/openbox/autostart.sh
```
to open the autostart.sh file.

---

### Post by Piraja on 2009-02-26
That's the path if you want system-wide settings (and settings that can be managed only with root privileges). However, in order to have user specific settings in Openbox, the configuration files should be located at ~/.config/openbox/, including ~/.config/openbox/autostart.sh. It is advisable to copy the config files to that location inasmuch as any editing is to be made, I think — and I guess most users want to customise their pypanel & other Openbox settings.

This is how my autostart.sh begins:

```
# This shell script is run before Openbox launches.
# Environment variables set here are passed to the Openbox session.

export OOO_FORCE_DESKTOP=gnome

nitrogen --restore & # comment this if you want Feh to set the background (see line 12)
pypanel &
nm-applet &
bluetooth-applet &
gnome-volume-manager &
update-notifier &
xcompmgr &
bruce-underwood &

#eval `cat $HOME/.fehbg` & # uncomment this to let Feh set the background (see line 6)
```

P.S. I added a screenshot. In case you wonder, "bruce-underwood" is a script (kudos to Bruce M.) that launches my Conkies (three separate windows, of which one is for weather and one for MPD).

---

