---
title: "Spotify-notify python notifications problems in Lubuntu 12.04"
date: 2012-07-17
forum: Programming Talk
---

### Post by Lyfang on 2012-07-17
Hi, I tried to install Spotify-notify. However I get: "org.gnome.SettingsDaemon.MediaKeys" from the Terminal. Spotify for Linux (preview release) is installed correctly & working:

Installation summary:
gksudo leafpad /etc/apt/sources.list &#8658; Add line &#8658; deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free &#8658; Save &#8658; sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59 &#8658; sudo apt-get update &#8658; installed spotify-client from Synaptic.

Downloaded spotify-notify-v0.6c.zip from [http://code.google.com/p/spotify-notify/downloads/list](http://code.google.com/p/spotify-notify/downloads/list) & used File Roller unpack zip-file with right-click "Extract here".

Installed from Terminal: 
```
sudo apt-get install python-indicate gnome-settings-daemon
```

Opened from the Terminal:
```
cd Hämtningar/spotify-notify/

python spotify-notify.py
```

It gives me the following error message:

```
Spotify-notify v0.6
Traceback (most recent call last):
  File "spotify-notify.py", line 468, in <module>
    MH = MediaKeyHandler(SN, Debug)
  File "spotify-notify.py", line 367, in __init__
    dbus_interface='org.gnome.SettingsDaemon.MediaKeys'
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Inget sådant gränssnitt "org.gnome.SettingsDaemon.MediaKeys" på objekt med sökvägen /org/gnome/SettingsDaemon/MediaKeys
```

I have also tried to install Notify OSD (notify-osd) with no result.

See also: [http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/)

---

### Post by Lyfang on 2012-07-18
Purging gnome-settings-daemon to be able to observ changes:
```
sudo apt-get purge gnome-settings-daemon
```

After purging gnome-settings-daemon, I get the following error message from the Terminal:
```
python spotify-notify.py
Spotify-notify v0.6
Traceback (most recent call last):
  File "spotify-notify.py", line 468, in <module>
    MH = MediaKeyHandler(SN, Debug)
  File "spotify-notify.py", line 362, in __init__
    '/org/gnome/SettingsDaemon/MediaKeys'
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files
```

---

### Post by Lyfang on 2012-07-28
Debugging the tracebacks could tell me more of what's actually wrong?

---

### Post by Lyfang on 2012-09-21
Has anyone solved the problem? Any help is greatly appreciated!

---

### Post by DJazZ on 2012-09-30
Hey!
I just installed Lubuntu 12.04, and Spotify. I have been using spotify-notify for media key support on Ubuntu, so I thought I could try use it. But it didn't work, only the notifications work.

Here is how I did:

Get the spotify-notify script from [http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/) and install the dependency:
sudo apt-get install python-indicate

Put it somewhere, like in the Hämtningar (Downloads) folder.


Then edit the openbox settings file, for example with leafpad, like this:

leafpad ~/.config/openbox/lubuntu-rc.xml

(replace lubuntu with lxde if you're not using lubuntu)


Then scroll down until you see <keyboard> and lots of <keybind> tags. I chose to put the new bindings below the volume control, so below the lines with <keybind key="XF86Audio...>, put this:

```

    <!-- Keybinding for spotify-notify and media keys -->

    <keybind key="XF86AudioPlay">
      <action name="Execute">
        <command>python ~/Downloads/spotify-notify/spotify-notify.py -a playPause -n -m -s</command>
      </action>
    </keybind>
    <keybind key="XF86AudioStop">
      <action name="Execute">
        <command>python ~/Downloads/spotify-notify/spotify-notify.py -a pause -n -m -s</command>
      </action>
    </keybind>
    <keybind key="XF86AudioNext">
      <action name="Execute">
        <command>python ~/Downloads/spotify-notify/spotify-notify.py -a next -n -m -s</command>
      </action>
    </keybind>
    <keybind key="XF86AudioPrev">
      <action name="Execute">
        <command>python ~/Downloads/spotify-notify/spotify-notify.py -a previous -n -m -s</command>
      </action>
    </keybind>

```

Then run this command to make openbox reload the settings file:

openbox --reconfigure

You can, if you want run spotify-notify with the -m option, if you want the notifications too.

NOTE: This will probably interfer with other programs that uses the global media keys. I don't know what will happen, probably both starts playing music :)

Enjoy!


Sources:
[http://code.google.com/p/spotify-notify/](http://code.google.com/p/spotify-notify/)
[http://wiki.lxde.org/en/LXDE:Questions#What_about_the_Play.2C_Stop.2C_Previous_and_Next_buttons.3F](http://wiki.lxde.org/en/LXDE:Questions#What_about_the_Play.2C_Stop.2C_Previous_and_Next_buttons.3F)
[http://crunchbanglinux.org/wiki/configuring_the_openbox_menu](http://crunchbanglinux.org/wiki/configuring_the_openbox_menu)

---

### Post by Lyfang on 2013-04-04
Thanks DJazZ for responding. I'm starting Spotify-notify python notifications without problems in Ubuntu 13.04 "Raring Ringtail" (with latest update as of today) and Spotify-notify works. But I have also received the following error message and crash with strace (debugging utility):

> strace ./spotify-notify.py

read(5, 0xbfd7416c, 16) = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {4940, 593188992}) = 0
waitpid(4420, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG) = 4420
waitpid(4423, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG) = 4423
close(10) = 0
pipe([10, 14]) = 0
fcntl64(10, F_GETFD) = 0
fcntl64(10, F_SETFD, FD_CLOEXEC) = 0
fcntl64(14, F_GETFD) = 0
fcntl64(14, F_SETFD, FD_CLOEXEC) = 0
pipe([15, 16]) = 0
fcntl64(15, F_GETFD) = 0
fcntl64(15, F_SETFD, FD_CLOEXEC) = 0
fcntl64(16, F_GETFD) = 0
fcntl64(16, F_SETFD, FD_CLOEXEC) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7574728) = 4443
close(16) = 0
close(14) = 0
mmap2(NULL, 1052672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb28ff000
read(15, "", 1048576) = 0
mremap(0xb28ff000, 1052672, 4096, MREMAP_MAYMOVE) = 0xb28ff000
close(15) = 0
munmap(0xb28ff000, 4096) = 0
fcntl64(10, F_GETFL) = 0 (flags O_RDONLY)
fstat64(10, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb40b8000
_llseek(10, 0, 0xbfd73788, SEEK_CUR) = -1 ESPIPE (Illegal seek)
fstat64(10, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
munmap(0xb40b8000, 4096) = 0
waitpid(4443, 0xbfd7376c, WNOHANG) = 0
read(10, "", 8192) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
close(13) = 0
munmap(0xb6cd5000, 4096) = 0
unlink("/tmp/tmpECU63Y") = 0
rt_sigaction(SIGINT, {SIG_DFL, [], 0}, {0x809ad1d, [], 0}, 8) = 0
exit_group(0) = ?

---

