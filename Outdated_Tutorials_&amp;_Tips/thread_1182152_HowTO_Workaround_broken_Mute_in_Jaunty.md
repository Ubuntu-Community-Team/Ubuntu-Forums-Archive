---
title: "HowTO Workaround broken Mute in Jaunty"
date: 2009-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2009-06-08
[SIZE="4"]**Summary**[/SIZE]
Ever since the upgrade to Jaunty, I've noticed that "Mute" no longer works as expected in ALSA, as first noticed when I pressed the "Mute" button on my Laptop LED panel.

Since I'm presuming that this is no isolated incident, I'll post my workaround script for anyone else who is experiencing this problem.
[SIZE="4"]
**Script**[/SIZE]
This is the script, save as the filename: **panel-mute**
[PHP]
#!/bin/sh
#
# Layout of the script:
#
# If sound has been muted and volume == 0
#   Restore alsa settings and remove temp data
# else
#   Store current alsa settings and mute
# fi
#

# executables
alsactl="/sbin/alsactl"
amixer="/usr/bin/amixer"
notify="/usr/bin/notify-send"
# config files
alsaconfig="$HOME/.saved_state"
volconfig="$HOME/.saved_state.vol"
dummycfg="/tmp/.dummycfg_state"
# icons/hints
mute_icon="notification-audio-volume-muted"
snd_icon="notification-audio-volume-high"
sync="string:x-canonical-private-synchronous:volume"
vol="int:value"
# Regexp, woot! :D
regexp='/Master\sPlayback\sVolume/{n;s/^\s*value.0\s*//;p;}'
# Get current volume
$alsactl store -f $dummycfg
testvol=`sed -n $regexp $dummycfg`
# Set/Unset Mute
if [ -e $alsaconfig ] && [ $testvol -eq 0 ]
then
    volume=`cat $volconfig`
    volume=`echo "scale=1; $volume/74*100" | bc`
    $notify " " -i $snd_icon -h $vol:$volume -h $sync
    $alsactl restore -f $alsaconfig
    rm $alsaconfig $volconfig
else
    $notify " " -i $mute_icon -h $vol:0 -h $sync
    $alsactl store -f $alsaconfig
    $amixer -q set Master 0% mute
    sed -n $regexp $alsaconfig > $volconfig
fi
[/PHP]
Save, then install it in the local/bin directory.
```
sudo install panel-mute /usr/local/bin/
```
[SIZE="4"]
**Implement it into Gnome/Compiz**[/SIZE]
This way uses Compiz, although it should be doable with Metacity's keybindings too.

Press **Alt+F2**, and type in:
```
gconf-editor
```
Then go into **/apps/gnome_settings_daemon/keybindings** and locate the key "**volume_mute**" and delete the value inside the key so that the field is blank, then close gconf-editor.

Next, go to **System->Preferences->CompizConfig Settings Manager** and click on the plugin "**Commands**".
In the *Command line 0* textbox, type in:
```
/usr/local/bin/panel-mute
```
then click on the key bindings tab, and click on the "Disabled" button adjacent to *Run Command 0*.
Click "**Grab Key Combination**", and press the "Mute" LED button on your Laptop Panel, and the key should show itself as "**XF86AudioMute**".

Ensure that the "**Commands**" plugin is enabled, then close the CompizConfig Settings Manager, now try out the mute button, and all should now work as expected.

If anyone has any questions, feel free to ask.

Regards
Iain

---

