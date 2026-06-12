---
title: "firefox crashes when using flash"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by nemodot on 2008-06-07
Hi, my problem is this, sometimes when I open a website with flash content like youtube firefox crashes and closes itself, its very frustrating when that happens and i couldn't find a solution.

I use firefox 3 beta 5, Ubuntu Hardy and PulseAudio as sound server.

---

### Post by quelx on 2008-06-07
**Applications** > **Accessories** > **Terminal** then type **firefox** *<enter>*

Browse to a problematic site and if it crashes see if any messages show up in the Terminal.  Post those.

---

### Post by Fedz on 2008-06-07
It used to happen to me quite often when using FF3 b5 ..

I went to System > admin > Software Services > Updates (tab) > enabled pre-release (option) > close.

The put on FF3.

Then maybe go back and uncheck enable pre-release.

Close any open browser windows.

I also un-installed flash-nonfree from SPM and deleted libflashplayer.so from:
Home > View > show hidden files (option) > **.**mozilla > plugins.

Goto adobe labs > [download flash 10](http://labs.adobe.com/downloads/flashplayer10.html) > unpack and then double click file flashplayer-installer > run in terminal and answer yes ...

Sounds hard work andlong winded but, in reality only takes a few minutes :-)

---

### Post by nemodot on 2008-06-07
Okey, this is all i get until it crashed:

```
esteban@esteban-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7207): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: NP_Initialize
** Message: NP_Initialize succeeded
** Message: totemPlugin ctor [0x8d7eb58]
** Message: Init mimetype 'video/x-ms-wmv' mode 2
** Message: Base URI is 'http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv'
** Message: Real mimetype for 'video/x-ms-wmv' is 'video/x-ms-wmv'
argv[0] type video/x-ms-wmv
argv[1] src http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv
argv[2] name plugin
argv[3] width 100%
argv[4] height 100%
** Message: mSrc: http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv
** Message: mCache: 0
** Message: mControllerHidden: 0
** Message: mShowStatusbar: 0
** Message: mHidden: 0
** Message: mAudioOnly: 0
** Message: mAutostart: 1, mRepeat: 0
** Message: Launching: /usr/lib/totem/gstreamer/totem-plugin-viewer --plugin-type gmp --user-agent Mozilla/5.0 (X11; U; Linux i686; es-AR; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5 --mimetype video/x-ms-wmv 
** Message: Viewer spawned, PID 7269
** Message: GetValue variable 14 (e)
** Message: Initial window set, XID 1e084a5 size 1280x799
** Message: No viewer proxy yet, deferring SetWindow
** Message: NewStream mimetype 'video/x-ms-wmv' URL 'http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv'
** Message: Viewer not ready, aborting stream
** Message: Viewer DBus interface name is 'org.gnome.totem.PluginViewer_7269'
** Message: NameOwnerChanged old-owner '' new-owner ':1.40'
** Message: Viewer now connected to the bus
** Message: ViewerSetup
** Message: Calling SetWindow
Viewer: SetWindow XID 31491237 size 1280:799
** Message: NameOwnerChanged old-owner '' new-owner ':1.40'
** Message: Already have owner, why are we notified again?
TotemEmbedded-Message: Viewer state: STOPPED
** Message: SetWindow reply
** Message: ViewerReady
** Message: IsSchemeSupported scheme 'http': yes
TotemEmbedded-Message: totem_embedded_open_stream called: uri http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv, base_uri: http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv
TotemEmbedded-Message: totem_embedded_open_internal 'fd://0' is-browser-stream 1 start-play 1
TotemEmbedded-Message: BEFORE _open
TotemEmbedded-Message: AFTER _open (ret: 1)
TotemEmbedded-Message: Viewer state: PLAYING
** Message: OpenStream reply
** Message: NewStream mimetype 'video/x-ms-wmv' URL 'http://www.hartford.gov/Police/Video/35%20Park%20St.%205-30-08.wmv'
** Message: Should be dual type 'video/x-ms-asf', making sure now
** Message: Is not dual type 'video/x-ms-asf'
** Message: Is not playlist: totem_pl_parser_can_parse_from_data failed (len 1697)
Fallo de segmentación
TotemEmbedded-Message: Viewer state: STOPPED
esteban@esteban-desktop:~$ 
(totem-plugin-viewer:7269): GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

```

---

### Post by Fedz on 2008-06-07
The above isn't specifically flash from youtube it's your totem plugin for watching wmv asf files ...etc

I'd just install [VLC](http://www.videolan.org) and use that as your browser plugin for viewing streaming media online :-)

```

apt-get update
apt-get install mozilla-plugin-vlc
```

---

### Post by quelx on 2008-06-07
**totem** is missing restricted plugins in the terminal again along with another repository for the windows codecs the video that particular page was trying to load.

```
sudo apt-get install totem-gstreamer totem-mozilla gstreamer0.10-pitfdll ubuntu-restricted-extras
```

For the rest follow the instructions **Install libdvdcss2 and w32 video codecs in Ubuntu 8.04 (Hardy Heron)**:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

---

