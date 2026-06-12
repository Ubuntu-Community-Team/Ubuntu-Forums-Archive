---
title: "Gnome-Tweak-Tool .... not working"
date: 2011-07-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2011-07-23
I have a problem Gnome-Tweak-Tool is not working ...... for me ...... is anyone else having this problem
if so is there a fix ..... maybe something simple like a .json file being the wrong version .

although it does appear that something is missing ...
[[COLOR=Red]_**Screenshot**_[/COLOR]]("http://img819.imageshack.us/img819/1958/snapshot15z.jpg")

`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

Here is the output when I try to run it ....

```

keithg@keith-Aspire-7730ZG:~$ gnome-tweak-tool
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.interface>
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--long-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.plugins.xsettings>
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)

INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.clock>
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.calendar>
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--short-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--long-docs)
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)

INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.extensions.user-theme>
INFO    : Shell user-theme extension v3.1.3
`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': python: undefined symbol: menu_proxy_module_load

(gnome-tweak-tool:4524): Gtk-WARNING **: Failed to load type module: (null)


GLib-GIO-ERROR **: Settings schema 'org.gtk.Settings.FileChooser' does not contain a key named 'last-folder-uri'
Trace/breakpoint trap
keithg@keith-Aspire-7730ZG:~$ 


```Any help would be appreciated ....

ok loaded 

aptitude install appmenu-gtk3

got rid of one error

```

keithg@keith-Aspire-7730ZG:~$ gnome-tweak-tool
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.desktop.interface>
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--long-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /apps/metacity/general/titlebar_font> (--short-docs)
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.settings-daemon.plugins.xsettings>
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.clock>
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.calendar>
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--short-docs)
INFO    : Caching gconf: <gtweak.gconf.GConfSetting: /desktop/gnome/shell/windows/button_layout> (--long-docs)
INFO    : Caching gsettings: <gtweak.gsettings._GSettingsSchema: org.gnome.shell.extensions.user-theme>
INFO    : Shell user-theme extension v3.1.3

GLib-GIO-ERROR **: Settings schema 'org.gtk.Settings.FileChooser' does not contain a key named 'last-folder-uri'
Trace/breakpoint trap
keithg@keith-Aspire-7730ZG:~$ 


```So we are left with this then

GLib-GIO-ERROR **: Settings schema 'org.gtk.Settings.FileChooser' does not contain a key named 'last-folder-uri'


ok so see what is there

```

keithg@keith-Aspire-7730ZG:~$ gsettings list-schemas
org.gnome.nautilus.desktop
org.gnome.settings-daemon.plugins.gconf
com.canonical.Unity
org.gnome.settings-daemon.plugins.keyboard
org.gnome.gedit.plugins.filebrowser.nautilus
org.gnome.settings-daemon.peripherals.wacom
org.gnome.settings-daemon.peripherals.touchpad
org.gnome.Empathy.hints
org.gnome.Nautilus.Sendto
org.freedesktop.Telepathy.Logger
org.gnome.yelp
org.gnome.settings-daemon.plugins.a11y-keyboard
org.gnome.gedit.plugins.filebrowser
org.gnome.system.proxy.http
org.gnome.desktop.screensaver
org.gnome.nautilus.window-state
org.gnome.settings-daemon.plugins.xrandr
org.gnome.settings-daemon.peripherals.input-devices
org.gnome.settings-daemon.plugins.color
org.gnome.gnome-panel.general
org.gnome.eog.view
org.gnome.libgnomekbd.indicator
org.gnome.gedit.plugins.externaltools
org.gwibber
com.canonical.indicators.sound
org.a11y.atspi
org.gnome.gedit.preferences.ui
org.gnome.gedit.state.file-filter
org.gnome.Empathy.conversation
org.gnome.settings-daemon.plugins.cursor
org.gnome.nautilus.sidebar-panels
org.gnome.Empathy
org.gnome.desktop.default-applications.office.tasks
org.gnome.brasero.filter
org.gnome.gnome-panel.layout
org.gnome.nautilus.icon-view
org.gnome.settings-daemon.peripherals.mouse
org.gnome.desktop.a11y.applications
org.gnome.settings-daemon.plugins.clipboard
org.gnome.settings-daemon.peripherals.smartcard
org.gnome.gedit.state.window
org.gnome.shell.clock
org.gnome.shell.extensions.auto-move-windows
org.gnome.desktop.background
org.gnome.desktop.a11y.magnifier
org.gnome.desktop.a11y.mouse
org.gnome.desktop.session
org.gnome.brasero.config
org.gnome.nautilus.compact-view
org.gnome.Empathy.ui
org.gnome.desktop.media-handling
org.gnome.gedit.preferences
org.gnome.Empathy.contacts
org.gnome.brasero.display
org.gnome.nautilus.sidebar-panels.tree
org.gnome.eog
org.gnome.gnome-panel
com.canonical.Unity.Launcher
org.gnome.settings-daemon.plugins.wacom
org.gnome.settings-daemon.plugins.font
org.gnome.desktop.default-applications
org.gnome.Evince.Default
org.gnome.system.locale
org.gnome.Empathy.location
org.gnome.settings-daemon.peripherals
org.gnome.desktop.sound
org.gnome.system.dns_sd
org.gnome.system.proxy.https
org.gnome.gnome-nettool
com.canonical.indicator.datetime
org.gnome.settings-daemon.peripherals.keyboard
org.gnome.settings-daemon.plugins.keybindings
org.gnome.power-manager
org.gnome.nautilus.list-view
org.gnome.settings-daemon.plugins.background
org.gnome.gedit.preferences.editor
org.gnome.SessionManager
org.gnome.settings-daemon.peripherals.wacom.pad
org.gnome.gedit.preferences.print
org.gnome.settings-daemon.plugins.xsettings
org.gnome.gedit.plugins.pythonconsole
org.gnome.desktop.default-applications.terminal
org.gnome.shell.recorder
org.gnome.mousetweaks
org.gnome.brasero
org.gnome.baobab.preferences
org.gnome.settings-daemon.plugins.mouse
com.canonical.Unity.Devices
org.gnome.gedit
org.gnome.settings-daemon.plugins.smartcard
org.gnome.shell
org.gwibber.state
org.gnome.baobab
org.gnome.system.proxy.socks
org.gnome.settings-daemon.plugins.media-keys
org.gnome.settings-daemon.plugins.sound
org.gnome.desktop.default-applications.office.calendar
org.gnome.settings-daemon.plugins.automount
org.gnome.settings-daemon.plugins.print-notifications
org.gnome.gedit.plugins.time
org.gnome.desktop.default-applications.office
org.gnome.libgnomekbd.desktop
com.canonical.Unity.Panel
org.gnome.shell.extensions.native-window-placement
org.gnome.nautilus.preferences
org.gnome.gedit.state.history-entry
org.gnome.system.proxy.ftp
org.gnome.libgnomekbd
org.gnome.shell.calendar
org.gnome.desktop.thumbnail-cache
org.gnome.shell.extensions.dock
org.gnome.settings-daemon.peripherals.wacom.cursor
org.gnome.nautilus
org.gnome.Evince
org.gnome.gedit.plugins
org.gnome.gnome-panel.run-dialog
org.gnome.baobab.ui
org.gnome.system-tools.users
org.gnome.crypto.pgp
org.gnome.system.smb
org.gnome.settings-daemon.plugins.a11y-settings
org.gnome.desktop.interface
org.gnome.Empathy.notifications
org.gnome.settings-daemon.plugins.power
org.gnome.gcalctool
org.gnome.settings-daemon.peripherals.wacom.eraser
org.gnome.libgnomekbd.preview
org.gnome.gnome-system-log
org.gnome.libgnomekbd.keyboard
org.gnome.gedit.state
org.gnome.system.proxy
ca.desrt.dconf-editor.Settings
org.gnome.gedit.preferences.encodings
org.gnome.gnome-screenshot
org.gnome.settings-daemon.plugins
org.gnome.eog.ui
org.gnome.Bluetooth.nst
org.gnome.desktop.lockdown
org.gnome.crypto.cache
org.gnome.settings-daemon.plugins.housekeeping
org.gnome.settings-daemon.peripherals.wacom.stylus
org.gnome.eog.plugins
org.gnome.eog.fullscreen
org.gnome.gnome-panel.lockdown
org.gnome.shell.extensions.user-theme
org.gnome.settings-daemon.peripherals.touchscreen
org.gnome.desktop.thumbnailers
org.gnome.Empathy.sounds
org.gnome.desktop.a11y.keyboard
org.gwibber.preferences
keithg@keith-Aspire-7730ZG:~$ 


```ok I do not  see

org.gtk.Settings.FileChooser

should it be there .... and if so how do I add it  ?

Is there a link other than this with more information on what to do - [Link]("http://developer.gnome.org/gtk/2.24/GtkFileChooser.html")

Is it related to this [Link]("http://osdir.com/ml/commits.gnome/2011-04/msg07013.html")

Will add this[ link too]("http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html") ..... as it gives a lot of useful information .... looking at the dconf-editor at the moment

---

### Post by ranch hand on 2011-07-23
All I know about it is that, under Debian, I am unable to install GS do to a dependency of gnome-settings-deamon not being the right version (version wanted is not in any repo I can find).

That may be the problem you are having.  Next time I am over there I will get the package name and version if you haven't solved this.

Should be there again tomorrow.

---

### Post by mc4man on 2011-07-23
Works fine here - are you using any non ubuntu packages, ppa's ect, is your install fully updated and how old is it.

You should see that key in dconf-editor under org/gtk/settings
though not too sure it does anything at this point

Do you have a /usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschemas.xml

---

### Post by jbicha on 2011-07-24
A magic command I use in this situation is dpkg -S will tell you what is the source package that installs a file with ___ as part of the file name.

$ dpkg -S org.gtk.Settings
libgtk-3-common: /usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschemas.xml

That command doesn't help if you don't have the particular file you need installed. I'm sure there's a command line tool for that too.

So the real question is how in the world do you not have gtk3 installed? Or if you do, what version do you have? The current Oneiric version is 3.1.8-0ubuntu5

---

### Post by 23dornot23d on 2011-07-24
@Ranchhand - I tried too in debian a while back now and had problems .... but was trying to install gnome-shell in knoppix using jhbuild ....

@jbicha
Mine returns the same as yours
keithg@keith-Aspire-7730ZG:~$ dpkg -S org.gtk.Settings
libgtk-3-common: /usr/share/glib-2.0/schemas/org.gtk.Settings.FileChooser.gschema.xml



@mcman
I have Ricotz testing ppa installed thats how I have Gnome Shell 3.1.3
this may be the problem as the tweak tool is 3.1.0 ( from his ppa )


```

keithg@keith-Aspire-7730ZG:/usr/share/glib-2.0/schemas$ ls
10_empathy.gschema.override
10_eog.gschema.override
10_gnome-power-manager.gschema.override
10_gnome-settings-daemon.gschema.override
10_gsettings-desktop-schemas.gschema.override
10_nautilus.gschema.override
apps.gecko-mediaplayer.preferences.gschema.xml
apps.gnome-mplayer.preferences.enums.xml
apps.gnome-mplayer.preferences.gschema.xml
ca.desrt.dconf-editor.gschema.xml
com.canonical.indicator.datetime.gschema.xml
com.canonical.indicators.sound.gschema.xml
com.canonical.Unity.gschema.xml
gschema.dtd
gschemas.compiled
org.a11y.atspi.gschema.xml
org.freedesktop.gstreamer-0.10.default-elements.gschema.xml
org.freedesktop.Telepathy.Logger.gschema.xml
org.gnome.baobab.gschema.xml
org.gnome.Bluetooth.nst.gschema.xml
org.gnome.brasero.gschema.xml
org.gnome.crypto.cache.gschema.xml
org.gnome.crypto.pgp.gschema.xml
org.gnome.desktop.a11y.applications.gschema.xml
org.gnome.desktop.a11y.keyboard.gschema.xml
org.gnome.desktop.a11y.magnifier.gschema.xml
org.gnome.desktop.a11y.mouse.gschema.xml
org.gnome.desktop.background.gschema.xml
org.gnome.desktop.default-applications.gschema.xml
org.gnome.desktop.enums.xml
org.gnome.desktop.interface.gschema.xml
org.gnome.desktop.lockdown.gschema.xml
org.gnome.desktop.media-handling.gschema.xml
org.gnome.desktop.screensaver.gschema.xml
org.gnome.desktop.session.gschema.xml
org.gnome.desktop.sound.gschema.xml
org.gnome.desktop.thumbnail-cache.gschema.xml
org.gnome.desktop.thumbnailers.gschema.xml
org.gnome.Empathy.gschema.xml
org.gnome.eog.enums.xml
org.gnome.eog.gschema.xml
org.gnome.Evince.gschema.xml
org.gnome.gcalctool.gschema.xml
org.gnome.gedit.enums.xml
org.gnome.gedit.gschema.xml
org.gnome.gedit.plugins.externaltools.gschema.xml
org.gnome.gedit.plugins.filebrowser.enums.xml
org.gnome.gedit.plugins.filebrowser.gschema.xml
org.gnome.gedit.plugins.pythonconsole.gschema.xml
org.gnome.gedit.plugins.time.enums.xml
org.gnome.gedit.plugins.time.gschema.xml
org.gnome.gnome-nettool.gschema.xml
org.gnome.gnome-panel.applet.fish.gschema.xml
org.gnome.gnome-panel.applet.window-list.gschema.xml
org.gnome.gnome-panel.applet.workspace-switcher.gschema.xml
org.gnome.gnome-panel.enums.xml
org.gnome.gnome-panel.gschema.xml
org.gnome.gnome-panel.launcher.gschema.xml
org.gnome.gnome-panel.menu-button.gschema.xml
org.gnome.gnome-panel.object.gschema.xml
org.gnome.gnome-panel.toplevel.gschema.xml
org.gnome.gnome-screenshot.gschema.xml
org.gnome.gnome-system-log.gschema.xml
org.gnome.libgnomekbd.desktop.gschema.xml
org.gnome.libgnomekbd.gschema.xml
org.gnome.libgnomekbd.keyboard.gschema.xml
org.gnome.mousetweaks.enums.xml
org.gnome.mousetweaks.gschema.xml
org.gnome.nautilus.gschema.xml
org.gnome.Nautilus.Sendto.gschema.xml
org.gnome.power-manager.gschema.xml
org.gnome.SessionManager.gschema.xml
org.gnome.settings-daemon.enums.xml
org.gnome.settings-daemon.peripherals.gschema.xml
org.gnome.settings-daemon.peripherals.wacom.gschema.xml
org.gnome.settings-daemon.plugins.color.gschema.xml
org.gnome.settings-daemon.plugins.gschema.xml
org.gnome.settings-daemon.plugins.housekeeping.gschema.xml
org.gnome.settings-daemon.plugins.keyboard.gschema.xml
org.gnome.settings-daemon.plugins.media-keys.gschema.xml
org.gnome.settings-daemon.plugins.power.gschema.xml
org.gnome.settings-daemon.plugins.print-notifications.gschema.xml
org.gnome.settings-daemon.plugins.xrandr.gschema.xml
org.gnome.settings-daemon.plugins.xsettings.gschema.xml
org.gnome.shell.extensions.auto-move-windows.gschema.xml
org.gnome.shell.extensions.dock.gschema.xml
org.gnome.shell.extensions.native-window-placement.gschema.xml
org.gnome.shell.extensions.user-theme.gschema.xml
org.gnome.shell.gschema.xml
org.gnome.system.dns_sd.gschema.xml
org.gnome.system.gvfs.enums.xml
org.gnome.system.locale.gschema.xml
org.gnome.system.proxy.gschema.xml
org.gnome.system.smb.gschema.xml
org.gnome.system-tools.gschema.xml
org.gnome.totem.enums.xml
org.gnome.totem.gschema.xml
org.gnome.totem.plugins.jamendo.gschema.xml
org.gnome.totem.plugins.opensubtitles.gschema.xml
org.gnome.totem.plugins.pythonconsole.gschema.xml
org.gnome.yelp.gschema.xml
[COLOR=Red]**org.gtk.Settings.FileChooser.gschema.xml**[/COLOR]
org.gwibber.gschema.xml
ubuntu-artwork.gschema.override


```Thanks for the help ..... seems the file is there ..... so now I will look at it .....

```

<?xml version="1.0" encoding="UTF-8"?>
<!--
  Copyright © 2010 Christian Persch

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU Lesser General Public License as published by
  the Free Software Foundation; either version 2.1, or (at your option)
  any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU Lesser General Public License
  along with this program; if not, write to the Free Software
  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
-->
<schemalist>

  <enum id='org.gtk.Settings.FileChooser.LocationMode'>
    <value nick='path-bar' value='0'/>
    <value nick='filename-entry' value='1'/>
  </enum>

  <enum id='org.gtk.Settings.FileChooser.SortColumn'>
    <value nick='name' value='0'/>
    <value nick='size' value='1'/>
    <value nick='modified' value='2'/>
  </enum>

  <enum id='org.gtk.Settings.FileChooser.SortOrder'>
    <value nick='ascending' value='0'/>
    <value nick='descending' value='1'/>
  </enum>

  <schema id='org.gtk.Settings.FileChooser'>
    <key name='location-mode' enum='org.gtk.Settings.FileChooser.LocationMode'>
      <default>'path-bar'</default>
    </key>
    <key name='show-hidden' type='b'>
      <default>false</default>
    </key>
    <key name='expand-folders' type='b'>
      <default>false</default>
    </key>
    <key name='show-size-column' type='b'>
      <default>true</default>
    </key>
    <key name='sort-column' enum='org.gtk.Settings.FileChooser.SortColumn'>
      <default>'name'</default>
    </key>
    <key name='sort-order' enum='org.gtk.Settings.FileChooser.SortOrder'>
      <default>'ascending'</default>
    </key>
    <key name='window-position' type='(ii)'>
      <default>(-1, -1)</default>
    </key>
    <key name='window-size' type='(ii)'>
      <default>(-1, -1)</default>
    </key>
  </schema>

</schemalist>

```

Can someone show me if theirs is the same or different to this one ........ please ....... or where can I go for the latest
if this is old ..... ?

---

### Post by jbicha on 2011-07-24
We can't really provide support for you using a testing PPA. I mean, did you even read the warning on his PPA page? Numerous people have confirmed that it works just fine in Oneiric.

By the way, Gnome Shell 3.1.3 is in Oneiric; gnome-tweak-tool 3.1 is not, but that hasn't even been released as a development snapshot yet so I wouldn't worry about that. In other words, Oneiric already has the latest good stuff.

Are you having this problem with Knoppix or Ubuntu Oneiric or something else?

Please revert your gtk+3.0 to 3.1.8-0ubuntu5

---

### Post by mc4man on 2011-07-24
The error is saying -  "does not contain a key named 'last-folder-uri'"
Did you look in dconf-editor to see?
screen shows

Here's mine, noted in blue

```
<?xml version="1.0" encoding="UTF-8"?>
<!--
  Copyright © 2010 Christian Persch

  This program is free software; you can redistribute it and/or modify
  it under the terms of the GNU Lesser General Public License as published by
  the Free Software Foundation; either version 2.1, or (at your option)
  any later version.

  This program is distributed in the hope that it will be useful,
  but WITHOUT ANY WARRANTY; without even the implied warranty of
  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
  GNU General Public License for more details.

  You should have received a copy of the GNU Lesser General Public License
  along with this program; if not, write to the Free Software
  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
-->
<schemalist>

  <enum id='org.gtk.Settings.FileChooser.LocationMode'>
    <value nick='path-bar' value='0'/>
    <value nick='filename-entry' value='1'/>
  </enum>

  <enum id='org.gtk.Settings.FileChooser.SortColumn'>
    <value nick='name' value='0'/>
    <value nick='size' value='1'/>
    <value nick='modified' value='2'/>
  </enum>

  <enum id='org.gtk.Settings.FileChooser.SortOrder'>
    <value nick='ascending' value='0'/>
    <value nick='descending' value='1'/>
  </enum>

 [COLOR="Blue"] <schema id='org.gtk.Settings.FileChooser'>
    <key name='last-folder-uri' type='s'>
      <default>""</default>
    </key>[/COLOR]
    <key name='location-mode' enum='org.gtk.Settings.FileChooser.LocationMode'>
      <default>'path-bar'</default>
    </key>
    <key name='show-hidden' type='b'>
      <default>false</default>
    </key>
    <key name='expand-folders' type='b'>
      <default>false</default>
    </key>
    <key name='show-size-column' type='b'>
      <default>true</default>
    </key>
    <key name='sort-column' enum='org.gtk.Settings.FileChooser.SortColumn'>
      <default>'name'</default>
    </key>
    <key name='sort-order' enum='org.gtk.Settings.FileChooser.SortOrder'>
      <default>'ascending'</default>
    </key>
    <key name='window-position' type='(ii)'>
      <default>(-1, -1)</default>
    </key>
    <key name='window-size' type='(ii)'>
      <default>(-1, -1)</default>
    </key>
  </schema>

</schemalist>
```

Edit: I don't think this is actually being used atm, it's set once and picks up on a uri that doesn't change
Though if I remember right gsettings will fail on missing even if not used or something like that..

---

### Post by ranch hand on 2011-07-24
Looks like you have plenty of advice, hopefully you will get it resolved.

The package  I am missing in this install is "libmozjs4d (>= 2.0~rc1) but it is not installable".  This is because it doesn't exist any longer.  I have "libmozjs5d" and the only things in the repos are that and "libmozjs2d".

They seem to be working on it.  This morning there are a couple of things off the depends list so that should help.

They all seem to have to do with gnome-control-center so they may actually have something to do with your problem.

---

### Post by 23dornot23d on 2011-07-24
@mc4man
The xml file you display that was different to mine I replaced it with the one you are using .... and fully expected ti to work but no such luck even did a full shutdown and re-logged in again . (but it may have been part of the solution to the full problem as I kept it)

@ranchahand 
You may be right as it could be something else .... as the xml file is ok now .....

@jbicha
I am running Ubuntu and as far as I know am up to date ... will give it a  go tonight to see if anything changes ......  with a upgrade .....

Please revert your [gtk+3.0 to 3.1.8-0ubuntu5]("https://launchpad.net/ubuntu/oneiric/+source/gtk+3.0/3.1.8-0ubuntu5")
will try this now ....

Ok it is working now .... removed the Ricotz testing PPA .... and the user-themes extension ..... last thing I did
and downgraded the Tweak tool too ..... gnome-tweak-tool is 3.0.4-1 now ..... 

[Screenshot - alls well]("http://img846.imageshack.us/img846/350/screenshotat20110724193.jpg")

Thank you all very much

---

### Post by jbicha on 2011-07-24
By the way, you can't just drop a schema in that folder and have it work. You would have to run glib-compile-schemas (done automatically when you install proper .deb packages).

I didn't mention that step because it was not your problem. All you needed was to go back to the regular Ubuntu packages. Glad that it's fixed for you now!

---

### Post by 23dornot23d on 2011-07-24
Cheers .... it maybe did that then when I did the gdebi ..... of the package you said to install then as I left it there ..... while running it ....
as you say alls well that ends well ..... ty for the advice and assistance too ... :KS

---

