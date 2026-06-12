---
title: "[SOLVED] Deluge error"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by flOOi!ghenTM on 2008-08-02
Ok so i've been using deluge for some time now with no issues whatsoever until today. When i opened the program it would just stale. This is how it looks:
[[IMG]http://c.imagehost.org/t/0018/Screenshot.jpg[/IMG]](http://c.imagehost.org/view/0018/Screenshot.png)
 I tried purging the program and do a fresh install but still no joy.

---

### Post by collinp on 2008-08-02
Try running Deluge in terminal and post the output here.

---

### Post by Elfy on 2008-08-02
It could be something in the hidden files did you delete them before reinstalling.

> /home/_user_/.config/deluge

You can remove it either with nautilus - show hidden files or from a terminal - replace user with your username

> rm -r /home/user/.config/deluge

---

### Post by flOOi!ghenTM on 2008-08-02
This id what i get when i run it in the terminal:

```
 [INFO    ] 11:08:07 main:84 Deluge ui 0.9.04
[DEBUG   ] 11:08:07 main:85 options: {'config': None, 'logfile': None, 'ui': None}
[DEBUG   ] 11:08:07 main:86 args: []
[DEBUG   ] 11:08:07 configmanager:44 ConfigManager started..
[INFO    ] 11:08:07 main:89 Starting ui..
[DEBUG   ] 11:08:07 ui:44 UI init..
[DEBUG   ] 11:08:07 configmanager:88 Getting config 'ui.conf'
[DEBUG   ] 11:08:07 config:47 Config created with filename: ui.conf
[DEBUG   ] 11:08:07 config:48 Config defaults: {'default_ui': 'gtk'}
[INFO    ] 11:08:07 ui:60 Starting GtkUI..
[DEBUG   ] 11:08:08 client:54 CoreProxy init..
[DEBUG   ] 11:08:08 configmanager:69 get_config_dir: /home/flooighen/.config/deluge
[DEBUG   ] 11:08:09 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:09 config:47 Config created with filename: gtkui.conf
[DEBUG   ] 11:08:09 config:48 Config defaults: {'autoadd_queued': False, 'close_to_tray': True, 'window_width': 640, 'default_load_path': None, 'window_y_pos': 0, 'classic_mode': True, 'window_pane_position': -1, 'enabled_plugins': [], 'show_connection_manager_on_start': True, 'show_statusbar': True, 'autoadd_enable': False, 'tray_download_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'autoconnect_host_uri': None, 'window_maximized': False, 'enable_system_tray': True, 'show_sidebar': True, 'window_x_pos': 0, 'window_height': 480, 'lock_tray': False, 'connection_limit_list': [50, 100, 200, 300, 500], 'tray_password': '', 'focus_add_dialog': True, 'show_new_releases': True, 'start_in_tray': False, 'autoconnect': False, 'choose_directory_dialog_path': '/home/flooighen', 'check_new_releases': True, 'autostart_localhost': False, 'show_toolbar': True, 'autoadd_location': '', 'config_location': '/home/flooighen/.config/deluge', 'tray_upload_speed_list': [5.0, 10.0, 30.0, 80.0, 300.0], 'interactive_add': True, 'signal_port': 40000}
0.9.04
[DEBUG   ] 11:08:09 gtkui:163 retcode: 0
[DEBUG   ] 11:08:09 component:102 Registered QueuedTorrents with ComponentRegistry..
[DEBUG   ] 11:08:09 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:10 component:102 Registered IPCInterface with ComponentRegistry..
[DEBUG   ] 11:08:10 component:102 Registered DbusInterface with ComponentRegistry..
[DEBUG   ] 11:08:10 ipcinterface:83 Processing args from other process: []
[DEBUG   ] 11:08:10 ipcinterface:86 Not connected to host.. Adding to queue.
[INFO    ] 11:08:10 dbusinterface:82 Registering with DBUS..
[DEBUG   ] 11:08:10 component:102 Registered MainWindow with ComponentRegistry..
[DEBUG   ] 11:08:10 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:11 mainwindow:84 Showing window
[DEBUG   ] 11:08:11 menubar:49 MenuBar init..
[DEBUG   ] 11:08:11 component:102 Registered MenuBar with ComponentRegistry..
[DEBUG   ] 11:08:11 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:12 component:102 Registered ToolBar with ComponentRegistry..
[DEBUG   ] 11:08:12 toolbar:48 ToolBar Init..
[DEBUG   ] 11:08:12 configmanager:88 Getting config 'gtkui.conf'
/var/lib/python-support/python2.5/deluge/ui/gtkui/toolbar.py:77: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem
  component.get("MenuBar").torrentmenu_glade.get_widget("remove_torrent_menu"))
[DEBUG   ] 11:08:12 component:102 Registered TorrentView with ComponentRegistry..
[DEBUG   ] 11:08:12 listview:124 ListView initialized..
[DEBUG   ] 11:08:12 torrentview:110 TorrentView Init..
[DEBUG   ] 11:08:12 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:12 listview:188 Loading ListView state file: torrentview.state
[DEBUG   ] 11:08:13 component:102 Registered TorrentDetails with ComponentRegistry..
[DEBUG   ] 11:08:13 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:13 torrentdetails:380 Loading TorrentDetails state file: tabs.state
[DEBUG   ] 11:08:13 torrentdetails:117 Old tabs.state, using default..
[DEBUG   ] 11:08:13 torrentdetails:65 parent: None
[DEBUG   ] 11:08:13 torrentdetails:65 parent: None
[DEBUG   ] 11:08:13 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:13 files_tab:216 Loading FilesTab state file: files_tab.state
[DEBUG   ] 11:08:13 torrentdetails:65 parent: None
[DEBUG   ] 11:08:13 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:13 peers_tab:176 Loading PeersTab state file: peers_tab.state
[DEBUG   ] 11:08:13 torrentdetails:65 parent: None
[DEBUG   ] 11:08:13 torrentdetails:65 parent: None
[DEBUG   ] 11:08:13 component:102 Registered SideBar with ComponentRegistry..
[DEBUG   ] 11:08:13 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:13 component:102 Registered Preferences with ComponentRegistry..
[DEBUG   ] 11:08:15 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:15 component:102 Registered SystemTray with ComponentRegistry..
[DEBUG   ] 11:08:15 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:15 config:158 Registering function for enable_system_tray key..
[DEBUG   ] 11:08:15 systemtray:76 Enabling the system tray icon..
[DEBUG   ] 11:08:16 component:102 Registered StatusBar with ComponentRegistry..
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:16 component:102 Registered AddTorrentDialog with ComponentRegistry..
[DEBUG   ] 11:08:16 component:102 Registered Signals with ComponentRegistry..
[DEBUG   ] 11:08:16 signalreceiver:52 SignalReceiver init..
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:16 config:117 Setting 'signal_port' to 65025 of <type 'int'>
[DEBUG   ] 11:08:16 coreconfig:40 CoreConfig init..
[DEBUG   ] 11:08:16 component:102 Registered CoreConfig with ComponentRegistry..
[DEBUG   ] 11:08:16 component:102 Registered PluginManager with ComponentRegistry..
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:16 pluginmanagerbase:48 Plugin manager init..
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'gtkui.conf'
[DEBUG   ] 11:08:16 configmanager:69 get_config_dir: /home/flooighen/.config/deluge
[DEBUG   ] 11:08:16 pluginmanagerbase:95 Found plugin: Test Plugin 1.0
[DEBUG   ] 11:08:16 pluginmanagerbase:95 Found plugin: Blocklist 1.0
[DEBUG   ] 11:08:16 pluginmanagerbase:95 Found plugin: Label 0.1
[DEBUG   ] 11:08:16 component:102 Registered ConnectionManager with ComponentRegistry..
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'hostlist.conf'
[DEBUG   ] 11:08:16 config:47 Config created with filename: hostlist.conf
[DEBUG   ] 11:08:16 config:48 Config defaults: {'hosts': ['localhost:58846']}
[DEBUG   ] 11:08:16 configmanager:88 Getting config 'gtkui.conf'



```

---

### Post by collinp on 2008-08-02
Hmm, its not outputting a obvious error. If you havent already, run 
```
sudo apt-get purge deluge
```
then run
```
sudo apt-get install deluge
```.

Maybe then it will work.

---

### Post by flOOi!ghenTM on 2008-08-02
i think it's ok now i manualy deleted the configuration files in the .config folder and reinstalled it. Now it seems to be working fine.
I really apreciate the help 10x a lot

---

### Post by Elfy on 2008-08-02
can you mark it solved please

---

### Post by flOOi!ghenTM on 2008-08-02
And how do you do that?

---

### Post by Elfy on 2008-08-02
Use thread tools at the top of the page there will be an option for you to mark the thread solved.

This thread has a lot of info which could be useful to you [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

---

### Post by flOOi!ghenTM on 2008-08-02
Done and thanx again

---

