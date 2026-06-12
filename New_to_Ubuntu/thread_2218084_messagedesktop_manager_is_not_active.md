---
title: "message:desktop manager is not active"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-04-19
running 14.04 when i log into any session except lubuntu (eg. gnome,ubuntu,xubuntu) i get the message:desktop manger is not active. any ideas how to correct. tks

---

### Post by bapoumba on 2014-04-19
No real idea, sorry. All I could find related to 14.04 was this : [https://bugs.launchpad.net/variety/+bug/1301651](https://bugs.launchpad.net/variety/+bug/1301651)
Has it always been that way or is this recent ? May be you need to broaden the search to other release and see if you find anything related to events that you might have been doing.

---

### Post by rburkartjo on 2014-04-19
bap tks. i always google first but sometimes i miss. if i google now get link to this thread displayed in search results. will keep on looking.

---

### Post by bapoumba on 2014-04-19
You're welcome, although I understand this is not of much help.
Looked again, found this one which is close to the previous one : [https://bugs.launchpad.net/variety/+bug/1296560](https://bugs.launchpad.net/variety/+bug/1296560)

---

### Post by UbuntAlec on 2014-04-20
This just happened to me, hence my finding this thread. Running 14.04 LTS in a Gnome desktop.
The cause in my case was using the Ubuntu Software Center and noticing a new tweak program called "Desktop Preferences" to "Change desktop wallpapers and behavior of desktop manager". Clicked "install" and went to a different window. While in the other window the "Desktop Manager" error started popping up. It turned out "Desktop Preferences was actually the pcmanfm file manager... Rather mis-labelled thinks I.  Uninstalled it and the Desktop Manager error went away.....

---

### Post by kondratievkirill on 2014-04-23
Problem:
I login with "Lubuntu" option (during Lubuntu's initial password authentication --> choosing "Lubuntu" in upper right corner's drop down menu). System logs in and:
"Desktop manager not active!" error message @ startup  - was bothering me as well,  
....so I played with a config file that was mentioned somwhere earlier this thread and that fixed an issue on my Lubuntu14 

Fix:
"Desktop manager not active!" error message @ startup  - DISAPEARED, once I updated my file located at:

~/.config/lxsession/Lubuntu/desktop.conf 
(..and restarted the machine afterwords to verify the fix)

Fix - Suggestions:
Your desktop.conf file for lxsession should look very similar to mine. Try editing it with vi or something (Only verify first 15 lines or so. Chances are your issue is somwhere within: [window_manager* OR file_manager* OR desktop_manager* ] parameters of desktop.conf. At least it was for me, because i did not modify any  other parameters ) 
This way you'll get to keep "pcmanfm". (Lubuntu's native file manager), but you'll lose "Desktop Setting" functionality while right-clicking on you desktop (right-click on DESKTOP --> System --> Desktop Setting (I believe that my nVidia driver took controll of that anyway, but I might be wrong. who cares..)

Fix - Details:
...so, in short: Try editing your "desktop.conf"  file to match mine. 
Here is mine:
...
[EMAIL="user@MACHINE:~/.config"]user@MACHINE:~/.config[/EMAIL]/lxsession/Lubuntu$ cat ~/.config/lxsession/Lubuntu/desktop.conf
[Session]
windows_manager=openbox
windows_manager/command=openbox
windows_manager/session=Lubuntu
windows_manager/extras=
panel/command=lxpanel
panel/session=Lubuntu
screensaver/command=
power_manager/command=auto
file_manager/command=pcmanfm
file_manager/session=Lubuntu
file_manager/extras=
desktop_manager/wallpaper=
polkit/command=lxpolkit
network_gui/command=nm-applet
audio_manager/command=alsamixer
quit_manager/command=lxsession-logout
quit_manager/image=/usr/share/lubuntu/images/logout-banner.png
quit_manager/layout=top
workspace_manager/command=obconf
launcher_manager/command=lxpanelctl
launcher_manager/autostart=true
terminal_manager/command=x-terminal-emulator
screenshot_manager/command=scrot
upgrade_manager/command=update-manager
clipboard/command=lxclipboard
composite_manager/command=
composite_manager/autostart=
disable_autostart=config-only
upstart_user_session=false
webbrowser/command=firefox
webbrowser/desktop=
xsettings_manager/command=build-in
proxy_manager/command=build-in
keyring/command=ssh-agent
email/command=sylpheed
pdf_reader/command=evince
video_player/command=gnome-mplayer
audio_player/command=audacious
images_display/command=gpicview
text_editor/command=leafpad
archive/command=file-roller
calculator/command=galculator
spreadsheet/command=gnumeric
bittorent/command=transmission-gtk
document/command=abiword
webcam/command=gucview
burn/command=xfburn
notes/command=xpad
disk_utility/command=gnome-disks
tasks/command=lxtask
lock_manager/command=lxlock
file_manager=Lubuntu

[State]
laptop_mode=no
guess_default=true

[Dbus]
lxde=true
gnome=false

[Keymap]
mode=system
model=
layout=
variant=
options=

[XRandr]
mode=
command=

[Security]
keyring=no

[a11y]
activate=no
type=

[Updates]
activate=true

[Environment]
type=lubuntu
menu_prefix=lxde-

[GTK]
sNet/ThemeName=Lubuntu-default
sNet/IconThemeName=lubuntu
sGtk/FontName=Ubuntu 11
iGtk/ToolbarStyle=3
iGtk/ButtonImages=1
iGtk/MenuImages=1
iGtk/CursorThemeSize=18
iXft/Antialias=1
iXft/Hinting=1
sXft/HintStyle=hintslight
sXft/RGBA=rgb
sGtk/CursorThemeName=DMZ-White
sGtk/ColorScheme=
iGtk/ToolbarIconSize=3
iNet/EnableEventSounds=1
iNet/EnableInputFeedbackSounds=1
iGtk/ColorScheme=

[Mouse]
AccFactor=20
AccThreshold=10
LeftHanded=0

[Keyboard]
Delay=500
Interval=30
Beep=1
[EMAIL="user@MACHINE:~/.config"]user@MACHINE:~/.config[/EMAIL]/lxsession/Lubuntu$ uname -a
Linux MACHINE 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
...

---

### Post by mlloyd on 2014-05-15
Thanks, that solved my problem.

Also, for Lubuntu 14.04 the GUI option "Preferences > Default applications for LXSession" works. It's the item on top.

---

### Post by afc888ny on 2014-08-03
I may not know what the core problem is, but I can tell how I overcame this problem.

Originally I am in Lubuntu 14.04 LTS and I noticed that my wallpaper and desktop icons (symbolic links) were missing.  I searched online and found the following small solution that worked for a while: from terminal enter:
pcmanfm --desktop-pref

I used this for a while but then after a routine update I reboot to encounter "Desktop Preferences not active" Dialog box.
I run pcmanfm --desktop-pref in Terminal and get the following:
** (pcmanfm:2693): WARNING **: terminal lxsession-default-terminal isn't known, consider report it to LibFM developers
** (pcmanfm:2693): WARNING **: modules directory is not accessible

I then reinstalled pcmanfm through synaptic, re-logged in and presto, everything back to normal.


______________________________________________________
a@a-NC210-NC110:~$ uname -a
Linux a-NC210-NC110 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

---

### Post by redbikemaster on 2014-09-03
I had this same problem. I just opened up "Default applications for LXSession", then went to the "Core Applications" tab, then clicked "Reload" next to Desktop Manager. Fixed it instantly.

---

