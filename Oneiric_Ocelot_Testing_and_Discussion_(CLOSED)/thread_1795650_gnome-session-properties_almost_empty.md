---
title: "gnome-session-properties almost empty"
date: 2011-07-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-07-03
Anyone else noticed that gnome-session-properties is almost empty?
also after a clean installation from a livecd there are no more startup launcher for network-manager, canberra login-sound, gnome-keyring and others.

is it a known bug or are they moving these things some where else?

---

### Post by dino99 on 2011-07-03
mine is different but have not reconfiguring it

---

### Post by vhaarr on 2011-07-03
Apparently they are removing lots of things from the "Startup Applications" as you can see here;
[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/803917](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/803917)

I do not agree with them.

---

### Post by mc4man on 2011-07-03
It somewhat started here when it was decided to hide "Startup Applications" from 'normal' users
[http://bazaar.launchpad.net/~vcs-imports/gnome-session/master/revision/4698](http://bazaar.launchpad.net/~vcs-imports/gnome-session/master/revision/4698)

Had a bug on that which was eventually marked invalid, though it was asked what could be considered optional (ie.  - remain in S.A.
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/802218](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/802218)

It now appears they've gone ahead and started removing some of what was in S.A., even things that are clearly 'non-core'

It should be noted that the first link suggests that some options will show up elsewhere at some point maybe.

---

### Post by lucazade on 2011-07-03
:-k

going to read the blueprint to understand why it was decided to hide these.
thanks for feedbacks and for pointing this out.

---

### Post by MacUntu on 2011-07-03
IMO most of that stuff really doesn't belong to an user accessible startup application manager. Alone all that keyring stuff.

I'd only be mad if we get no place else to disable things like Bluetooth Manager, Printer Queue Applet, Remote Desktop et al., because they all slow down session start.

---

### Post by lucazade on 2011-07-03
yep, it is a strange decision.

these are all the startup application launchers
```
$ ls /etc/xdg/autostart/

bluetooth-applet.desktop
bluetooth-applet-unity.desktop
gnome-keyring-gpg.desktop
gnome-keyring-pkcs11.desktop
gnome-keyring-secrets.desktop
gnome-keyring-ssh.desktop
gnome-settings-daemon.desktop
gnome-sound-applet.desktop
gsettings-data-convert.desktop
jockey-gtk.desktop
nautilus-autostart.desktop
nm-applet.desktop
polkit-gnome-authentication-agent-1.desktop
print-applet.desktop
pulseaudio.desktop
pulseaudio-kde.desktop
user-dirs-update-gtk.desktop

```

to show them back in gnome-session-properties
```
$ cat /etc/xdg/autostart/print-applet.desktop

[Desktop Entry]
Encoding=UTF-8
Name=Print Queue Applet
Comment=System tray icon for managing print jobs
Exec=system-config-printer-applet
Terminal=false
Type=Application
Icon=printer
NotShowIn=KDE;LXDE;
StartupNotify=false
X-GNOME-Autostart-Delay=30
X-Ubuntu-Gettext-Domain=system-config-printer
NoDisplay=true
X-Desktop-File-Install-Version=0.18
Categories=GTK;Monitor;System;

```

change NoDisplay=true to false and reopen gnome-session-properties ;)

hope a saner way will be available !

---

### Post by MacUntu on 2011-07-03
Sweet.

---

### Post by lucazade on 2011-07-03
> **MacUntu said:**
> Sweet.

Sweeter:

```

cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

```

---

### Post by dino99 on 2011-07-03
Thanks Luca

---

### Post by lucazade on 2011-07-03
> **dino99 said:**
> Thanks Luca

;)

---

### Post by mc4man on 2011-07-03
Does anyone know where per user changes to gnome-session-properties (add, remove, edit) are written to?

( another NoDisplay=true that's a small issue is the one in gdebi.desktop, because of one can't directly set it as the default .deb handler
though that has been acknowledged as incorrect and should be fixed at some point

---

### Post by MacUntu on 2011-07-03
~/.config/autostart

---

### Post by mc4man on 2011-07-03
> **MacUntu said:**
> ~/.config/autostart
Thanks - I think I may be  getting it, maybe not- 
It seems any .desktop in ~/.config/autostart/ is disabled unless it was a user created one.
Edit: - I now see - all .desktops that end up there have an autostart line

I'd then assume any .desktop in /etc/xdg/autostart/ is default enabled unless in the above?

The new default list of 'optional' ones here is seen in screen, a bit less than prior 
( in natty I usually had 20-21 default enabled out of which I'd disable 10-11

---

### Post by Harry33 on 2011-07-04
> **mc4man said:**
> Thanks - I think I may be  getting it, maybe not- 
It seems any .desktop in ~/.config/autostart/ is disabled unless it was a user created one.
Edit: - I now see - all .desktops that end up there have an autostart line

I'd then assume any .desktop in /etc/xdg/autostart/ is default enabled unless in the above?

The new default list of 'optional' ones here is seen in screen, a bit less than prior 
( in natty I usually had 20-21 default enabled out of which I'd disable 10-11

Note that all .config/autostart/*.desktop files do have this line in the end:
X-GNOME-Autostart-enabled=false

So, this determines that they are not automatically started (per user session).
You may of course add that line to the files in
/etc/xdg/autostart/*.desktop
Then they are not autostarted by any user session.
Obviously an update will remove this line, however.

---

### Post by mc4man on 2011-07-04
> You may of course add that line to the files in
/etc/xdg/autostart/*.desktop
Then they are not autostarted by any user session.

Possibly you're confusing visible with autostarted. In any install I've done, (ever), all apps shown in gnome-session-properties are enabled by default (& optional
So in natty I'd have 20 or so default enabled after install, likely reflecting **all** the .desktops in /urs/xdg/autostart

Currently I think if you go thru the .desktops in /etc/xdg/autostart most **are** autostarted
Out of this group some should be optional, ie.,  show up in gnome-session-properties.
For myself I do see some that aren't available that should be.

---

### Post by Harry33 on 2011-07-04
> **mc4man said:**
> Possibly you're confusing visible with autostarted. In any install I've done, (ever), all apps shown in gnome-session-properties are enabled by default (& optional
So in natty I'd have 20 or so default enabled after install, likely reflecting **all** the .desktops in /urs/xdg/autostart

Currently I think if you go thru the .desktops in /etc/xdg/autostart most **are** autostarted
Out of this group some should be optional, ie.,  show up in gnome-session-properties.
For myself I do see some that aren't available that should be.

Nope.
I was talking about autostarting, not the visibility in the application gnome-session-properties.

If the line (X-GNOME-Autostart-enabled=false) is added into those .desktop files, they do not autostart.
This is why you see this line in the files in the user folder .config/autostart/

---

### Post by jbicha on 2011-07-05
Yes, those are hidden in Oneiric because there is no reason for normal users to be turning those services off. If any particular service is slowing down login, please report that as a bug.

---

### Post by Harry33 on 2011-07-05
> **jbicha said:**
> Yes, those are hidden in Oneiric because there is no reason for normal users to be turning those services off. If any particular service is slowing down login, please report that as a bug.

Most of us here in this Forum are not normal users, however.

---

### Post by seeker5528 on 2011-07-06
> **mc4man said:**
> Thanks - I think I may be  getting it, maybe not- 
It seems any .desktop in ~/.config/autostart/ is disabled unless it was a user created one.

There are some that are set to no show up. What shows up as an optional service as a user depends on what you have installed.

If you look at some of the different .desktop files you will see some control lines that can affect things in different ways....


```
NotShowIn=KDE;LXDE;

AutostartCondition=GNOME /desktop/gnome/remote_access/enabled
X-GNOME-Autostart-enabled=false

OnlyShowIn=LXDE

Hidden=true
```

Later, Seeker

---

### Post by drs305 on 2011-07-08
> **lucazade said:**
> 
change NoDisplay=true to false and reopen gnome-session-properties ;)

hope a saner way will be available !

For now, on the ones with "NoDisplay=true",  I've just settled on running this command to display them all in gnome-session-properties (globally changes NoDisplay from 'true' to 'false')

```
for i in $( ls /etc/xdg/autostart ); do sudo sed 's/NoDisplay=true/NoDisplay=false/g' -i /etc/xdg/autostart/$i; done
```

---

### Post by mc4man on 2011-07-09
It would appear that it's been decided to not hide  gnome-session-properties anymore, we'll see.
As far as what is considered 'optional' - 
Many of the 'non-core' ones make no real difference whether enabled or not, they are just a run and check with several delayed up to 60 sec.'s so not really affecting the boot time.
Ones i think should be optional and currently aren't - 
update-notifier, disk notif., backup monitor, network

Under better circumstances having all the optional ones and above 4 enabled don't matter much in terms of mem. use
With the current state of cairo-gl and nvidia it does make a big difference when disabled, up to around 150MB+ here which is considerable on a 1GB machine, somewhat irrelevant on more modern hardware 
(with the default settings I'm currently showing 720MB used 90 sec's after login to unity

---

### Post by lucazade on 2011-07-09
> **mc4man said:**
> It would appear that it's been decided to not hide  gnome-session-properties anymore, we'll see.
As far as what is considered 'optional' - 
Many of the 'non-core' ones make no real difference whether enabled or not, they are just a run and check with several delayed up to 60 sec.'s so not really affecting the boot time.
Ones i think should be optional and currently aren't - 
update-notifier, disk notif., backup monitor, network

Under better circumstances having all the optional ones and above 4 enabled don't matter much in terms of mem. use
With the current state of cairo-gl and nvidia it does make a big difference when disabled, up to around 150MB+ here which is considerable on a 1GB machine, somewhat irrelevant on more modern hardware 
(with the default settings I'm currently showing 720MB used 90 sec's after login to unity

Thanks mc4man for updates, interesting.
And yes I agree about memory consuption of autostart core and optional parts.

absolutely right about nvidia and cairo-gl and thanks for tracking down this issue on lp

---

### Post by Mr. Picklesworth on 2011-07-11
It would be nice if we just had a separation between user-defined and system-defined startup applications, since the two are plainly different things. Oh well, making Startup Applications do the one is a start.

---

### Post by lucazade on 2011-07-11
if i'm not wrong gnome-session-properties has been added to control-center as capplet.
(unfortunately with latest udev updates my oneiric in virtualbox freezes at login, so i can't check this new applet)

gnome-session (3.1.3-0ubuntu2) oneiric; urgency=low

  * 03_display_session_capplet.patch: display the** session properties capplet**,
    the list is cleaned from the system services now and it can be useful
    for users who want to start softwares with the session (lp: #802218)
  * series: comment 80_new_upstream_session_dialog, the modified version never
    went in upstream git and has issues with gtk3, if the upstream dialog is
    not working fine in our desktop we should discuss how to maintain a custom
    session dialog in a better way (lp:807503)

Date: Mon, 11 Jul 2011 16:39:56 +0200
[http://www.mail-archive.com/oneiric-changes@lists.ubuntu.com/msg01868.html](http://www.mail-archive.com/oneiric-changes@lists.ubuntu.com/msg01868.html)

---

### Post by mc4man on 2011-07-11
> **lucazade said:**
> if i'm not wrong gnome-session-properties has been added to control-center as capplet.
(unfortunately with latest udev updates my oneiric in virtualbox freezes at login, so i can't check this new applet)

gnome-session (3.1.3-0ubuntu2) oneiric; urgency=low

  * 03_display_session_capplet.patch: display the** session properties capplet**,
    the list is cleaned from the system services now and it can be useful
    for users who want to start softwares with the session 

Now that the group of visible apps or whatever has been adjusted to suit Startup Applications has again been made visible to menus and or a search in dash.
They simply removed the NoDisplay=true line from session-properties.desktop
(NoDisplay=true seems to be a convenient 'tool' for adjusting  the 'user experience'

---

### Post by seeker5528 on 2011-07-11
> **lucazade said:**
> if i'm not wrong gnome-session-properties has been added to control-center as capplet.
>   * 03_display_session_capplet.patch: display the** session properties capplet**,

Seems to be broken at the moment.

I think it was always a capplet, must just not be fully ported to current control center, but I could have sworn it was working in earlier gnome control center 3.X.X.

Hmmm, 'Preferences' doesn't show as it's own thing, preferences stuff doesn't show in 'System' or 'Accessories' either. WTF?!?!?! I guess the Ubuntu powers that be thought more people would find 'Preferences' if they renamed it 'Themes & Tweaks'. :P 

Later, Seeker

---

### Post by lucazade on 2011-07-11
> **seeker5528 said:**
> Seems to be broken at the moment.

I think it was always a capplet, must just not be fully ported to current control center, but I could have sworn it was working in earlier gnome control center 3.X.X.

Hmmm, 'Preferences' doesn't show as it's own thing, preferences stuff doesn't show in 'System' or 'Accessories' either. WTF?!?!?! I guess the Ubuntu powers that be thought more people would find 'Preferences' if they renamed it 'Themes & Tweaks'. :P 

Later, Seeker

Do we want to bet on the next tool that will be hidden? Background? :)

---

### Post by seeker5528 on 2011-07-11
****> **lucazade said:**
> Do we want to bet on the next tool that will be hidden? Background? :)

There's multiple things going on there.

The old control panel stuff, even if they were considered 'applets', were really more individual things that were independent from each other, so it was really easy for anything to get an icon into the 'control center'.

With Gnome 3 the Gnome devs decided it was more important to have a control center that felt like you were never leaving it to run some other configuration app that it was to have centralized configuration, so things actually do have to be applets.

Don't know what's up exactly with 'Desktop', I think removing the 'Desktop' menu from gnome-menu was something to bring gnome-panel more in line with what you get in gnome-shell.  But in removing it, 'Administration' and 'Preferences' were not moved to the 'Applications' menu. 

Don't know how much of that is because of the Gnome devs and how much is distribution stuff in the way Debian and Ubuntu were handling these menus. Or in other words, I don't know if stock Gnome 2.x.x showed non Gnome stuff on these 'Desktop --> *' menus or if Debian and Ubuntu devs hacked the Gnome XDG menu to get non Gnome stuff to show at the 'Desktop --> *' locations, whatever showed there seemed to automatically show in gnome-control-center 2.x.x. 

Doesn't seem quite as clean as the Desktop menu used to be, but now seems like in Unity, what ever used to show in 'Desktop --> System' should show in ' Applications --> System' and whatever showed in 'Desktop --> Preferences' should show in 'Applications --> 'Themes and Tweaks'.

The menu editor still shows a separate 'Desktop' menu, so I'm guessing the stuff that shows there still doesn't show on the Application menu in the Gnome fallback session. 

Later, Seeker

---

### Post by lucazade on 2011-07-11
I share the same doubts about xdg menu, but I haven't investigated this thing too much.
I have seen they added also software-sources to control center but it is just an icon that opens an external window, so it seems not well integrated :S

---

### Post by seeker5528 on 2011-07-11
> **lucazade said:**
> I have seen they added also software-sources to control center but it is just an icon that opens an external window, so it seems not well integrated :S

This is all I've seen in Control Center for a while.....

[img]http://home.comcast.net/~seeker5528/Screenshot-GnomeCC.png[/img]

It would be nice if they just called it 'Gnome Contol Center' on the menu, or at least didn't have 'System Settings' show up twice with no way to tell which belongs to Gnome and which belongs to KDE. :P

Later, Seeker

---

### Post by lucazade on 2011-07-11
> **seeker5528 said:**
> This is all I've seen in Control Center for a while.....

It would be nice if they just called it 'Gnome Contol Center' on the menu, or at least didn't have 'System Settings' show up twice with no way to tell which belongs to Gnome and which belongs to KDE. :P

Later, Seeker

You don't have software-sources icon..well nice, maybe it is a refuse here :)
About the name, yep, gnome-control-center sounds better than system settings.

I'm sure that half of the next 100 papercuts will be about changing name to apps!

---

### Post by seeker5528 on 2011-07-11
> **lucazade said:**
> About the name, yep, gnome-control-center sounds better than system settings.

I don't know who's brilliant idea it was to call things by a name on the menu that has no similarity to the application name. Is that a 'here's your sign' offense?:P

Just logged in to a fallback session [gnome classic (no fx)] or some words to that effect at the login screen. There is a 'Applications --> System Tools' that shows some of the stuff that would have previously been in 'Desktop --> System', doesn't seem to be a place on the 'Applications' menu for any of the 'Desktop --> Preferences' stuff to show, so gnome-session-properties seems to be out in the cold on the Gnome menu at the moment.

Later, Seeker

---

### Post by mc4man on 2011-07-11
> **lucazade said:**
> I share the same doubts about xdg menu, but I haven't investigated this thing too much.
I have seen they added also software-sources to control center but it is just an icon that opens an external window, so it seems not well integrated :S
I don't think 'they' added software sources, maybe just is slipping thru the cracks.
If you enable it in alacarte then it will show up in g-c-c
(seems to be in both pref and admin.
It has an  line in it's .desktop that may be a factor though not the only reason it shows

(the xdg menu still has those issues we saw before, can't remember if i filed a bug on. xdg-open has an obsure one I did file on sorta, - part of an issue in /gnome/defaults.list using a non-existent nautilus-folder-handler.desktop

---

### Post by seeker5528 on 2011-07-13
> **mc4man said:**
> If you enable it in alacarte then it will show up in g-c-c

So it *can* show other stuff.

> (seems to be in both pref and admin.

That seems to be the normal thing, to reduce duplicates.  

> It has an  line in it's .desktop that may be a factor though not the only reason it shows

The categories line might be enough I see things there 'X-GNOME-SystemSettings;X-GNOME-Settings-Panel;', 'HardwareSettings;X-GNOME-Settings-Panel;', 'X-GNOME-Settings-Panel;X-GNOME-PersonalSettings'. But looking around at some of the other .desktop files they all seem to have a line simliar to this one from deja-dup-ccpanel.desktop, 'X-GNOME-Settings-Panel=deja-dup'.

Later, Seeker

---

### Post by mc4man on 2011-07-13
Again seeing diff's from a couple of week old install and a new one yesterday
In the new install software sources shows up in g-c-c by default, in the old one only if enabled in main menu - pref.'s, if disabled it then disappears, ect.

---

### Post by jbicha on 2011-07-13
> **lucazade said:**
> I share the same doubts about xdg menu, but I haven't investigated this thing too much.
I have seen they added also software-sources to control center but it is just an icon that opens an external window, so it seems not well integrated :S

I believe it was decided to be a simpler solution to have the non-upstream control panel applets just be links in System Settings.

To integrate them fully would be a lot of work and the patch would probably take a bunch of refactoring to keep it working for new releases. And GNOME is not interested in incorporating the patch. Further, most of the Ubuntu-specific applets are python-based but System Settings doesn't support python applets.

---

### Post by lucazade on 2011-07-13
> **jbicha said:**
> I believe it was decided to be a simpler solution to have the non-upstream control panel applets just be links in System Settings.

To integrate them fully would be a lot of work and the patch would probably take a bunch of refactoring to keep it working for new releases. And GNOME is not interested in incorporating the patch. Further, most of the Ubuntu-specific applets are python-based but System Settings doesn't support python applets.

ahh, thanks!
I imagined that was the reason.

---

### Post by mc4man on 2011-08-23
Now that this has shaken out - by default there is no longer anything available to be disabled in S-A
(the exception would be nvidia-settings though can't see why anyone would want to disable.

While I find several things I want to disable that's irrelevant and doesn't matter
The one I do think should be available to disable for various reasons  is the bluetooth applet
Did re-file on that specifically though the odds are it will be ignored or invalidated

[https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/832007](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/832007)

---

### Post by lucazade on 2011-08-23
I'm still not happy about the almost empty autostart applet,
this is what I apply after a new install:

```
# Fix autostart components
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/at-spi-dbus-bus.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/bluetooth-applet-unity.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/deja-dup-monitor.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/gdu-notification-daemon.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/gnome-sound-applet.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/gnome-user-share.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/gwibber.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/jockey-gtk.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/nautilus-autostart.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/onboard-autostart.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/orca-autostart.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/print-applet.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/ubuntuone-launch.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/update-notifier.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/user-dirs-update-gtk.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /etc/xdg/autostart/vino-server.desktop
echo "X-GNOME-Autostart-enabled=false" | sudo tee -a /usr/share/gnome/autostart/libcanberra-login-sound.desktop
```

I'd like also to tune system services like in old ubu releases. So again with a little script I disable some other stuff:

```
# Disable services
sudo update-rc.d kerneloops disable
sudo update-rc.d rsync disable
sudo update-rc.d speech-dispatcher disable
sudo update-rc.d unattended-upgrades disable

# Disable apport
sudo sed -i 's/enabled=1/enabled=0/g' /etc/default/apport

# Disable avahi-daemon
sudo sed -i 's/AVAHI_DAEMON_DETECT_LOCAL=1/AVAHI_DAEMON_DETECT_LOCAL=0/g' /etc/default/avahi-daemon

# Disable auto-updates
sudo sed -i 's/APT::Periodic::Update-Package-Lists "1";/APT::Periodic::Update-Package-Lists "0";/g' /etc/apt/apt.conf.d/10periodic
```

this way my netbook can boot-up with Unity2D and only 150mb (on 1gb) of memory used :)

---

### Post by aeronutt on 2011-08-28
Am I missing something? When I bring up 'startup applications', it's empty. I'm sure there are apps that get started that I should have control over (eg bluetooth, etc).

Where else can I check for what programs get started at boot/login?

[IMG]http://i.imgur.com/mgIWQ.png[/IMG]

---

### Post by lucazade on 2011-08-28
known thing, it is by design.

check last page for some hints:
[http://ubuntuforums.org/showthread.php?t=1795650](http://ubuntuforums.org/showthread.php?t=1795650)

---

### Post by aeronutt on 2011-08-28
ahhh...thanks.  I had searched around, but didn't find that particular thread.

---

### Post by aeronutt on 2011-08-28
I've tried adding "X-GNOME-Autostart-enabled=false" to /etc/xdg/autostart/bluetooth-applet.desktop, but no avail. Bluetooth still starts automagically. Any ideas?

```
[Desktop Entry]
Name=Bluetooth Manager
Comment=Bluetooth Manager applet
Icon=bluetooth
Exec=bluetooth-applet
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-bluetooth
X-GNOME-Bugzilla-Component=applet
X-GNOME-Bugzilla-Version=3.1.4
AutostartCondition=GNOME3 if-session gnome-fallback
NoDisplay=false
X-Ubuntu-Gettext-Domain=gnome-bluetooth2
X-GNOME-Autostart-enabled=false

```

---

### Post by lucazade on 2011-08-28
> **aeronutt said:**
> I've tried adding "X-GNOME-Autostart-enabled=false" to /etc/xdg/autostart/bluetooth-applet.desktop, but no avail. Bluetooth still starts automagically. Any ideas?

```
[Desktop Entry]
Name=Bluetooth Manager
Comment=Bluetooth Manager applet
Icon=bluetooth
Exec=bluetooth-applet
Terminal=false
Type=Application
Categories=
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-bluetooth
X-GNOME-Bugzilla-Component=applet
X-GNOME-Bugzilla-Version=3.1.4
AutostartCondition=GNOME3 if-session gnome-fallback
NoDisplay=false
X-Ubuntu-Gettext-Domain=gnome-bluetooth2
X-GNOME-Autostart-enabled=false

```

strange, here doesn't start if I add it.
try to copy this .desktop file in /usr/share/gnome/autostart/ as root or in /home/username/.config/autostart as normal user

---

### Post by cariboo on 2011-08-28
Merged two threads on the same subject.

---

### Post by aeronutt on 2011-08-28
> **lucazade said:**
> strange, here doesn't start if I add it.
try to copy this .desktop file in /usr/share/gnome/autostart/ as root or in /home/username/.config/autostart as normal user

Tried this...no change. Confirmed that bluetooth is running with the hciconfig command.

Any other ideas?

---

### Post by mc4man on 2011-08-29
> **aeronutt said:**
> Tried this...no change. Confirmed that bluetooth is running with the hciconfig command.

Any other ideas?
Did you go into 'Startup Applications' and disable bluetooth? 
(there are 2 .desktops, unity one should be disabled if using unityshell, - bluetooth-applet-unity.desktop

---

### Post by sonicb00m on 2011-08-30
> **lucazade said:**
> Sweeter:

```

cd /etc/xdg/autostart/
sudo sed --in-place 's/NoDisplay=true/NoDisplay=false/g' *.desktop

```

perfect , thanks!

---

### Post by aeronutt on 2011-08-30
> **mc4man said:**
> Did you go into 'Startup Applications' and disable bluetooth? 
(there are 2 .desktops, unity one should be disabled if using unityshell, - bluetooth-applet-unity.desktop

Yep, disabled both. Still no joy. Darn bluetooth starts up no matter.

---

### Post by lucazade on 2011-08-30
> **aeronutt said:**
> Yep, disabled both. Still no joy. Darn bluetooth starts up no matter.

is maybe the bluetooth service and not the session applet?

```
$ sudo service bluetooth stop
 * Stopping bluetooth                                                    [ OK ]
```

```
$ sudo update-rc.d bluetooth disable
update-rc.d: warning: bluetooth start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: bluetooth stop runlevel arguments (none) do not match LSB Default-Stop values (0 1 6)
 Disabling system startup links for /etc/init.d/bluetooth ...
 Removing any system startup links for /etc/init.d/bluetooth ...
   /etc/rc0.d/K74bluetooth
   /etc/rc1.d/K74bluetooth
   /etc/rc2.d/S25bluetooth
   /etc/rc3.d/S25bluetooth
   /etc/rc4.d/S25bluetooth
   /etc/rc5.d/S25bluetooth
   /etc/rc6.d/K74bluetooth
 Adding system startup for /etc/init.d/bluetooth ...
   /etc/rc0.d/K74bluetooth -> ../init.d/bluetooth
   /etc/rc1.d/K74bluetooth -> ../init.d/bluetooth
   /etc/rc6.d/K74bluetooth -> ../init.d/bluetooth
   /etc/rc2.d/K75bluetooth -> ../init.d/bluetooth
   /etc/rc3.d/K75bluetooth -> ../init.d/bluetooth
   /etc/rc4.d/K75bluetooth -> ../init.d/bluetooth
   /etc/rc5.d/K75bluetooth -> ../init.d/bluetooth

```

---

### Post by aeronutt on 2011-08-30
I run 
```
sudo service bluetooth stop

```

And then run
```
hciconfig
```

Which shows bluetooth still running!

---

### Post by mc4man on 2011-08-30
This thread was more about startup apps (applets, ect. ) than services

If you want to not have the service running then the command posted above should work  
(i'd simply ck. w/ service --status-all, bluetooth should show a - 

If you don't want to have the service start ever then removing these 2 packages should prevent (really the 1st. one
bluez 
gnome-bluetooth 
This will however prevent gnome-shell & gnome-share from installing, though building GS without bluetooth support/dependency is quite simple, maybe 5-10 min. at most (have no use for gnome-share here

---

### Post by aeronutt on 2011-08-30
This is confusing. In previous versions, all I had to do was uncheck bluetooth in the 'startup applications' window, and it wouldn't start. But it was easily available if I needed it.

Now, it's all or nothing? I either have to build GS with no bluetooth dependency, or bluetooth always starts? Just doesn't make sense. Put another way, the user has no control over what services start?

---

### Post by cariboo on 2011-08-30
Wouldn't removing the executable bit from /etc/init.d/bluetooth, stop the service from starting on boot?

---

### Post by mc4man on 2011-08-30
> **aeronutt said:**
> This is confusing. In previous versions, all I had to do was uncheck bluetooth in the 'startup applications' window, and it wouldn't start. But it was easily available if I needed it.

Now, it's all or nothing? I either have to build GS with no bluetooth dependency, or bluetooth always starts? Just doesn't make sense. Put another way, the user has no control over what services start?

Personally while this laptop has bluetooth I'll never use it, and for some reason it can make it run hotter so I do remove completely.
Even so not too sure it makes any diff if the service is running - you can turn off bluetooth in g-c-c, if you don't want the applet running then turn off in Startup Apps
As mentioned above the service is started by a file in the bluez package (/etc/init.d/bluetooth), does having the service run really matter?

---

### Post by aeronutt on 2011-08-31
> **mc4man said:**
> ... you can turn off bluetooth in g-c-c...
Sorry, what is g-c-c?

> **mc4man said:**
> ... if you don't want the applet running then turn off in Startup Apps...
This does not work for me. I've turned it off in Startup Apps, and it still starts when I reboot. I've also edited files in several autostart directories, and it still starts.

---

### Post by aeronutt on 2011-08-31
> **cariboo907 said:**
> Wouldn't removing the executable bit from /etc/init.d/bluetooth, stop the service from starting on boot?

This seems to have worked, thanks. But seems like the wrong way to address this. I'll use this, hoping that this gets fixed so it works like previous versions.

---

### Post by jbicha on 2011-08-31
> **aeronutt said:**
> Sorry, what is g-c-c?


g-c-c is an abbreviation for gnome-control-center which is "System Settings" as found in the system "indicator" menu.

---

### Post by aeronutt on 2011-08-31
> **jbicha said:**
> g-c-c is an abbreviation for gnome-control-center which is "System Settings" as found in the system "indicator" menu.

Ahhh..gotcha. And no, unfortunately that setting is not persistent. I set it, log out, and back in, and bluetooth is on.

---

### Post by jbicha on 2011-08-31
Have you reported this as a bug yet against bluez or something? I don't use bluetooth so I can't provide much assistance but it does seem that the on/off switch is not doing the Right Thing.

---

### Post by mc4man on 2011-08-31
Never noticed before because I always used to just get rid of most of the *blue* libs, -  but in 11.10 the service will run unless stopped or bluez removed.

So here  bluetooth is disabled in bios and cannot be turned on, either thru the applet or g-c-c
But the service is running as seen in service --status-all and ps aux

Previously, (11.04 and earlier), when disabled in bios, bluetooth also can't be turned on and the service would  never be running   (even if the applet was 'on'

So definitely seems to be an issue as of 11.10, though not sure if it running matters that much

---

### Post by Harry33 on 2011-08-31
In my desktop setup I have also unchecked the applet from running.
The service starts on each boot, which is the same as people here have noticed.
This is still funny regarding my desktop, because I do not even have any bluetooth hardware here.
And if I open System Settings - Bluetooth, it says "No bluetooth adapters found".
So, the manager side of this software is running.
I think this is not a problem nor a bug. It merely means the system is ready if I add a bluetooth adapter into it.

---

### Post by skibler on 2011-09-02
edit: wrong thread.

---

