---
title: "dual ubuntu usage stack in standby mode"
date: 2018-01-08
forum: New to Ubuntu
---

### Post by grandmix on 2018-01-08
Hello everyone! As I am a new to Ubuntu I'd like to know what causes thus problem. Recently I installed 16.04 LTS version on the hard drive where there was already one ubuntu 14.04 with a swap part. I however needed a new one as I was going to use it for personal reasons. Previous systems was installed as lvm and is now stored at the beginning of the hard drive. New one I installed to the end of hard drive with some swap memory (perhaps it wasn't needed). The problem is that now system is stack every time in standby mode. Can anyone help me to figure out why. I am confused because I'm also using teamviewer and I have a feeling that it can cause the problem as well. I am attaching logs:

```
Jan  8 19:17:56 gr-MS-7850 systemd[1]: Starting Locale Service...Jan  8 19:17:56 gr-MS-7850 gnome-session-binary[1757]: Entering running state
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (process:2142): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (process:2142): indicator-application-service-WARNING **: Name Lost
Jan  8 19:17:56 gr-MS-7850 dbus[924]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (nautilus:2140): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (nautilus:2140): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (nautilus:2140): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (nautilus:2140): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Jan  8 19:17:56 gr-MS-7850 gnome-session[1757]: (nautilus:2140): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,326][INFO ][node                     ] [Molten Man] version[2.3.1], pid[2010], build[bd98092/2016-04-04T12:25:05Z]
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,327][INFO ][node                     ] [Molten Man] initializing ...
Jan  8 19:17:56 gr-MS-7850 dbus[924]: [system] Successfully activated service 'org.freedesktop.locale1'
Jan  8 19:17:56 gr-MS-7850 systemd[1]: Started Locale Service.
Jan  8 19:17:56 gr-MS-7850 kernel: [   17.488547] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
Jan  8 19:17:56 gr-MS-7850 kernel: [   17.497160] EXT4-fs (sda2): warning: mounting unchecked fs, running e2fsck is recommended
Jan  8 19:17:56 gr-MS-7850 kernel: [   17.498114] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
Jan  8 19:17:56 gr-MS-7850 udisksd[1952]: Mounted /dev/sda2 at /media/gr/eeeb616a-6acd-4ffa-804c-424ed8e38d1a on behalf of uid 1000
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,648][INFO ][plugins                  ] [Molten Man] modules [reindex, lang-expression, lang-groovy], plugins [], sites []
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,660][INFO ][env                      ] [Molten Man] using [1] data paths, mounts [[/ (/dev/sda5)]], net usable_space [30gb], net total_space [47.9gb], spins? [no], types [ext4]
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,660][INFO ][env                      ] [Molten Man] heap size [989.8mb], compressed ordinary object pointers [true]
Jan  8 19:17:56 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:56,660][WARN ][env                      ] [Molten Man] max file descriptors [65535] for elasticsearch process likely too low, consider increasing to at least [65536]
Jan  8 19:17:56 gr-MS-7850 dbus[924]: [system] Successfully activated service 'org.freedesktop.fwupd'
Jan  8 19:17:57 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:57,557][INFO ][node                     ] [Molten Man] initialized
Jan  8 19:17:57 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:57,557][INFO ][node                     ] [Molten Man] starting ...
Jan  8 19:17:57 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:57,613][INFO ][transport                ] [Molten Man] publish_address {127.0.0.1:9300}, bound_addresses {[::1]:9300}, {127.0.0.1:9300}
Jan  8 19:17:57 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:17:57,615][INFO ][discovery                ] [Molten Man] elasticsearch/QRwgP7VsTIS7bvAmCurhCA
Jan  8 19:17:57 gr-MS-7850 org.gtk.vfs.Daemon[1602]: ** (process:2252): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jan  8 19:17:57 gr-MS-7850 NetworkManager[976]: <info>  [1515435477.8825] manager: WiFi hardware radio set enabled
Jan  8 19:17:57 gr-MS-7850 NetworkManager[976]: <info>  [1515435477.8826] manager: WWAN hardware radio set enabled
Jan  8 19:17:57 gr-MS-7850 org.gtk.vfs.Daemon[1602]: ** (process:2243): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jan  8 19:17:57 gr-MS-7850 org.freedesktop.FileManager1[1602]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Jan  8 19:17:58 gr-MS-7850 org.gtk.vfs.Daemon[1602]: ** (process:2252): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jan  8 19:17:59 gr-MS-7850 org.gtk.vfs.Daemon[1602]: message repeated 23 times: [ ** (process:2252): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend]
Jan  8 19:18:00 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:18:00,632][INFO ][cluster.service          ] [Molten Man] new_master {Molten Man}{QRwgP7VsTIS7bvAmCurhCA}{127.0.0.1}{127.0.0.1:9300}, reason: zen-disco-join(elected_as_master, [0] joins received)
Jan  8 19:18:00 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:18:00,640][INFO ][http                     ] [Molten Man] publish_address {127.0.0.1:9200}, bound_addresses {[::1]:9200}, {127.0.0.1:9200}
Jan  8 19:18:00 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:18:00,640][INFO ][node                     ] [Molten Man] started
Jan  8 19:18:00 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:18:00,667][INFO ][gateway                  ] [Molten Man] recovered [1] indices into cluster_state
Jan  8 19:18:00 gr-MS-7850 elasticsearch[2010]: [2018-01-08 19:18:00,870][INFO ][cluster.routing.allocation] [Molten Man] Cluster health status changed from [RED] to [YELLOW] (reason: [shards started [[tutorial][1]] ...]).
Jan  8 19:18:04 gr-MS-7850 org.gtk.vfs.Daemon[1602]: ** (process:2252): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jan  8 19:18:06 gr-MS-7850 com.canonical.Unity.Scope.Applications[1602]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Jan  8 19:18:06 gr-MS-7850 com.canonical.Unity.Scope.Applications[1602]: (unity-scope-loader:2326): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Jan  8 19:18:12 gr-MS-7850 pulseaudio[1856]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Jan  8 19:18:16 gr-MS-7850 gnome-session[1757]: ** (zeitgeist-datahub:2412): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Jan  8 19:18:17 gr-MS-7850 systemd-timesyncd[804]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
Jan  8 19:18:41 gr-MS-7850 systemd[1]: Starting Stop ureadahead data collection...
Jan  8 19:18:41 gr-MS-7850 systemd[1]: Stopped Read required files in advance.
Jan  8 19:18:41 gr-MS-7850 systemd[1]: Started Stop ureadahead data collection.
Jan  8 19:19:47 gr-MS-7850 systemd[1]: Stopping User Manager for UID 108...
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Reached target Shutdown.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Starting Exit the Session...
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Stopped target Default.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Stopped target Basic System.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Stopped target Paths.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Stopped target Timers.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Stopped target Sockets.
Jan  8 19:19:47 gr-MS-7850 systemd[1167]: Received SIGRTMIN+24 from PID 2538 (kill).
Jan  8 19:19:47 gr-MS-7850 systemd[1]: Stopped User Manager for UID 108.
Jan  8 19:19:47 gr-MS-7850 systemd[1]: Removed slice User Slice of lightdm.
```

Thanks in advance!

---

