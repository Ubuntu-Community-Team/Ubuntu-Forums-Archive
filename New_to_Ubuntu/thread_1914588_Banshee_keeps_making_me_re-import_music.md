---
title: "Banshee keeps making me re-import music"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by djdonte on 2012-01-24
Running 11.10 64 bit

When I open banshee it has all my music there but when I double click it nothing happens. If I right click on a song and select open containing folder it gives me an error saying it cant locate file, make sure it is accessible by the system or something to that effect. If I re-import my whole music folder it fixes it for a while then it goes back to the previous state after a few reboots.

When I run banshee -1 in console this is what I get

```
[Info  15:08:09.175] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-12-19 14:58:04 UTC]

(Banshee:3456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:3456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:3456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:3456): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[Info  15:08:10.658] Updating web proxy from GConf
[Info  15:08:10.810] All services are started 1.310443
[Info  15:08:11.827] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
** (Banshee:3456): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3456): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

(Banshee:3456): Gtk-CRITICAL **: IA__gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
** (Banshee:3456): DEBUG: Loading the real store page
[Info  15:08:13.903] nereid Client Started
[Info  15:08:14.071] GStreamer version 0.10.35.0, gapless: True, replaygain: False

```

---

