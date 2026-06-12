---
title: "Not sure whats wrong"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by kzyswd on 2013-04-03
Hi,

I just started using ubuntu today so bear with my newbieness.:|

I have a vps with ubuntu 12.04 64bit installed. (can be changed to 32bits, earlier versions, or centos, etc. too)
Following directions on websites, I installed ubuntu desktop and vnc4server through Putty.
When I use some vnc viewer(tried ultravnc and tightvnc java) and connect the desktop will show up (i think its called Unity)

The problem is, when I click any programs on the left bar(firefox and such), nothing happens... the icon will flash for about 4 times and thats it.
I can click on the menu bar and the dropdown list shows up, but clicking anything on the list does nothing.
I can create new folder on the desktop by right-clicking and I can also delete it.

I haven't get to setup users yet. All done in root access.

I want to at least use firefox with flash player on this vps. 
What could be the problem?:confused:

edit:libre office doesnt flash when clicked.
       right click and "change background" will show a window (something like explorer) but it automatically close the window after a second.

---

### Post by katanacb on 2013-04-03
is there anything in $HOME/.xsession-errors after you click on something in the left menubar (such as error messages, etc).  you can look at this file from a terminal, assuming that you can get it to pull up.

The other option that you might try is xrdp ... personally I use that instead of vnc, and it allows any windows machine with Remote Desktop to view a Linux desktop without installing anything additional on the windows side.   try:

sudo apt-get install xrdp ... then reboot your Linux machine and try to remote desktop in and see if that works any better.   Might also help narrow down the problem some too.

---

### Post by kzyswd on 2013-04-03
Sorry, how do I read $HOME/.xsession-errors ?

I tried xrdp. nothing changes other than it took longer to load. though I do like rdp better if the loading gets faster.

what can I try next?

---

### Post by slickymaster on 2013-04-03
Run the following command a terminal window:
```
geany .xsession-errors
```
Note that you have to use the text pad installed on your system. In my case it's Geany.

In case you don't have any textpad installed you can use the '**cat'** command:
```
cat .xsession-errors
```
and content of the file will be printed to the terminal window.

---

### Post by steeldriver on 2013-04-03
Last time I tried it, VNC didn't play too well with compiz / 3d stuff - I'd recommend trying it with a 2d session - here's a ~/.vnc/xstartup file which worked for me

```
$ cat ~/.vnc/xstartup 
#!/bin/sh

# Change "GNOME" to "KDE" for a KDE desktop, or "" for a generic desktop
MODE="GNOME"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
if [ -e "$HOME/.Xresources" ]
then
        xrdb "$HOME/.Xresources"
fi

# Try a GNOME session, or fall back to KDE
if [ "GNOME" = "$MODE" ]
then
        if which gnome-session >/dev/null
        then
                gnome-session --session=ubuntu-2d &
        else
                MODE="KDE"
        fi
fi

# Try a KDE session, or fall back to generic
if [ "KDE" = "$MODE" ]
then
        if which startkde >/dev/null
        then
                startkde &
        else
                MODE=""
        fi
fi

# Run a generic session
if [ -z "$MODE" ]
then
        xsetroot -solid "#DAB082"
        x-terminal-emulator -geometry "80x24+10+10" -ls -title "$VNCDESKTOP Desktop" &
        x-window-manager &
fi
```

which I got from here iirc (the page isn't loading for me right now) --> [https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by kzyswd on 2013-04-03
Tried cat .xsession-errors

```
file '': No such file or directory
unity-2d-shell: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
** Message: moving back from GtkStatusIcon to indicator
WARN  2013-04-03 20:00:40 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/unity-lens-video/unity-lens-video exited with status 1
Bus error
x-session-manager[1171]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1171]: WARNING: Could not launch application 'telepathy-indicator.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 

(gnome-screensaver:1448): GLib-ERROR **: creating thread 'dconf worker': Error creating thread: Resource temporarily unavailable
x-session-manager[1171]: WARNING: Could not launch application 'ubuntuone-launch.desktop': Unable to start application: Failed to fork (Cannot allocate memory)

(nautilus:1231): Gdk-WARNING **: nautilus: Fatal IO error 12 (Cannot allocate memory) on X server :1.


** (update-notifier:1460): WARNING **: not starting for system user

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 417, in <module>
    u = GtkUI()
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 85, in __init__
    target_kernel=self.argv_options.kernel)
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 60, in __init__
    self._get_os_version()
  File "/usr/lib/python2.7/dist-packages/jockey/oslib.py", line 717, in _get_os_version
    stderr=subprocess.PIPE, close_fds=True)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1143, in _execute_child
    self.pid = os.fork()
OSError: [Errno 12] Cannot allocate memory
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 

(gnome-settings-daemon:1189): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':1'.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
unity-2d-panel: [WARNING] unity-2d-panel: Fatal IO error: client killed
unity-2d-shell: [WARNING] unity-2d-shell: Fatal IO error: client killed
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(gnome-fallback-mount-helper:1235): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gdu-notification-daemon:1445): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
** Message: PID 1228 (we are 1228) sent signal 15, shutting down...

(bluetooth-applet:1232): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(nm-applet:1228): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(deja-dup-monitor:1476): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.42 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:1476): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.43 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:1476): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.45 of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts
Xsession: X session started for root at Wed Apr  3 20:08:58 MSK 2013
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:root being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=all_ALL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[1036]: WARNING: GSIdleMonitor: IDLETIME counter not found
x-session-manager[1036]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
GNOME_KEYRING_CONTROL=/tmp/keyring-Y5dYrg
GPG_AGENT_INFO=/tmp/keyring-Y5dYrg/gpg:0:1
GNOME_KEYRING_PID=1048
GNOME_KEYRING_CONTROL=/tmp/keyring-Y5dYrg
GPG_AGENT_INFO=/tmp/keyring-Y5dYrg/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-Y5dYrg
GPG_AGENT_INFO=/tmp/keyring-Y5dYrg/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-Y5dYrg
GPG_AGENT_INFO=/tmp/keyring-Y5dYrg/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-Y5dYrg/ssh

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_name: Failed to open file '/sys/class/dmi/id/product_name': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_name: Failed to open file '/sys/class/dmi/id/board_name': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_version: Failed to open file '/sys/class/dmi/id/product_version': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_version: Failed to open file '/sys/class/dmi/id/chassis_version': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_version: Failed to open file '/sys/class/dmi/id/board_version': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/sys_vendor: Failed to open file '/sys/class/dmi/id/sys_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_vendor: Failed to open file '/sys/class/dmi/id/chassis_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_vendor: Failed to open file '/sys/class/dmi/id/board_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: Unable to start color manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): power-plugin-WARNING **: Unable to start power manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): xrandr-plugin-WARNING **: Unable to start xrandr manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: XKB extension not available

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "XInputExtension" missing on display ":1".
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-shell: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server doesn't support the Composite extension. 
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-2d-shell: [WARNING] GestureHandler::GestureHandler(QObject*): GEIS initialization failed: multitouch support disabled 
Initializing nautilus-gdu extension
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-panel: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
** Message: applet now removed from the notification area
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-panel: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600007
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x260000a
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
** Message: moving back from GtkStatusIcon to indicator
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Music: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-music/unity-music-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/unity-lens-video/unity-lens-video exited with status 1
Bus error
x-session-manager[1036]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'telepathy-indicator.desktop': Unable to start application: Failed to fork (Cannot allocate memory)

(gnome-screensaver:1316): GLib-ERROR **: creating thread 'gdbus': Error creating thread: Resource temporarily unavailable
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
x-session-manager[1036]: WARNING: Could not launch application 'ubuntuone-launch.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
x-session-manager[1036]: WARNING: Could not launch application 'jockey-gtk.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'update-notifier.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'deja-dup-monitor.desktop': Unable to start application: Failed to fork (Cannot allocate memory)


```


rebooted and tried it fresh


```
(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/sys_vendor: Failed to open file '/sys/class/dmi/id/sys_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_vendor: Failed to open file '/sys/class/dmi/id/chassis_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_vendor: Failed to open file '/sys/class/dmi/id/board_vendor': No such file or directory

(gnome-settings-daemon:1054): color-plugin-WARNING **: Unable to start color manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): power-plugin-WARNING **: Unable to start power manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): xrandr-plugin-WARNING **: Unable to start xrandr manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: XKB extension not available

(gnome-settings-daemon:1054): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "XInputExtension" missing on display ":1".
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-shell: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server doesn't support the Composite extension. 
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
unity-2d-shell: [WARNING] GestureHandler::GestureHandler(QObject*): GEIS initialization failed: multitouch support disabled 
Initializing nautilus-gdu extension
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-panel: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
** Message: applet now removed from the notification area
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-panel: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600007
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x260000a
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
** Message: moving back from GtkStatusIcon to indicator
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Music: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-music/unity-music-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Applications: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-applications/unity-applications-daemon received signal 5
WARN  2013-04-03 20:09:02 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/unity-lens-video/unity-lens-video exited with status 1
Bus error
x-session-manager[1036]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'telepathy-indicator.desktop': Unable to start application: Failed to fork (Cannot allocate memory)

(gnome-screensaver:1316): GLib-ERROR **: creating thread 'gdbus': Error creating thread: Resource temporarily unavailable
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
x-session-manager[1036]: WARNING: Could not launch application 'ubuntuone-launch.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
x-session-manager[1036]: WARNING: Could not launch application 'jockey-gtk.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'update-notifier.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1036]: WARNING: Could not launch application 'deja-dup-monitor.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
** Message: PID 1606 (we are 1095) sent signal 15, shutting down...
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':1'.

(gnome-settings-daemon:1054): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(nm-applet:1095): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

Xsession: X session started for root at Wed Apr  3 20:20:26 MSK 2013
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
localuser:root being added to access control list
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5
  Serial number of failed request:  6
  Current serial number in output stream:  8
Setting IM through im-switch for locale=all_ALL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
x-session-manager[1042]: WARNING: GSIdleMonitor: IDLETIME counter not found
x-session-manager[1042]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
GNOME_KEYRING_CONTROL=/tmp/keyring-HywP31
GNOME_KEYRING_PID=1053
GNOME_KEYRING_CONTROL=/tmp/keyring-HywP31
GPG_AGENT_INFO=/tmp/keyring-HywP31/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HywP31
GPG_AGENT_INFO=/tmp/keyring-HywP31/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-HywP31
GPG_AGENT_INFO=/tmp/keyring-HywP31/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-HywP31/ssh

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_name: Failed to open file '/sys/class/dmi/id/product_name': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_name: Failed to open file '/sys/class/dmi/id/board_name': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/product_version: Failed to open file '/sys/class/dmi/id/product_version': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_version: Failed to open file '/sys/class/dmi/id/chassis_version': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_version: Failed to open file '/sys/class/dmi/id/board_version': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/sys_vendor: Failed to open file '/sys/class/dmi/id/sys_vendor': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/chassis_vendor: Failed to open file '/sys/class/dmi/id/chassis_vendor': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: failed to get contents of /sys/class/dmi/id/board_vendor: Failed to open file '/sys/class/dmi/id/board_vendor': No such file or directory

(gnome-settings-daemon:1060): color-plugin-WARNING **: Unable to start color manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1060): power-plugin-WARNING **: Unable to start power manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1060): xrandr-plugin-WARNING **: Unable to start xrandr manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:1060): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

(gnome-settings-daemon:1060): keyboard-plugin-WARNING **: XKB extension not available

(gnome-settings-daemon:1060): keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings
Window manager warning: Log level 32: could not find XKB extension.
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
Xlib:  extension "XInputExtension" missing on display ":1".
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-shell: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server doesn't support the Composite extension. 
unity-2d-shell: [WARNING] GestureHandler::GestureHandler(QObject*): GEIS initialization failed: multitouch support disabled 
Xlib:  extension "XInputExtension" missing on display ":1".
unity-2d-panel: [WARNING] bool KeyMonitor::registerEvents(): No input devices found. 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
Initializing nautilus-gdu extension
** Message: applet now removed from the notification area
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2400007
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x240000a
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell** Message: using fallback from indicator to GtkStatusIcon
: [WARNING] HotkeyMonitor::HotkeyMonitor(QObject*): Failed to initialize Xkb extension. CapsLock and NumLockactive will prevent shortcuts from working. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [WARNING] int _x_grabkey_errhandler(Display*, XErrorEvent*): Call to XGrabKey failed, this usually means some other client already reserved the hotkey. 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
** Message: moving back from GtkStatusIcon to indicator
WARN  2013-04-03 20:20:30 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.hud: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/indicator-appmenu/hud-service received signal 5
WARN  2013-04-03 20:20:30 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for com.canonical.Unity.Lens.Files: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-files/unity-files-daemon received signal 5
WARN  2013-04-03 20:20:30 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/unity-lens-video/unity-lens-video received signal 5
x-session-manager[1042]: WARNING: Could not launch application 'pulseaudio.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1042]: WARNING: Could not launch application 'gdu-notification-daemon.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
unity-2d-shell: [WARNING] bool Application::launch(): Failed to launch application: Failed to fork (Cannot allocate memory) 
x-session-manager[1042]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1042]: WARNING: Could not launch application 'telepathy-indicator.desktop': Unable to start application: Failed to fork (Cannot allocate memory)
x-session-manager[1042]: WARNING: Could not launch application 'ubuntuone-launch.desktop': Unable to start application: Failed to fork (Cannot allocate memory)


```

---

### Post by katanacb on 2013-04-04
tons of 'cannot allocate memory' messages ... I'm sure that's telling but I'd have to look up and see what that's all about.  Does everything work OK if you login to the machine on a console?

---

### Post by kzyswd on 2013-04-04
You mean ssh?

---

