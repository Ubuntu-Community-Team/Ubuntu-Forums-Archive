---
title: "Miro crashes"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-21
I installed miro: sudo apt-get install miro.

Then when I try to launch it from the terminal it opens up and then in a few seconds closes.

This is the terminal output:

```

abhiroop@Vanimo:~$ miro
/var/lib/python-support/python2.5/dbus_bindings.py:1: DeprecationWarning: The dbus_bindings module is not public API and will go away soon.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  from dbus.dbus_bindings import *
INFO     Starting up Miro
INFO     Version:  0.9.8.1
INFO     Revision: unknown
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/abhiroop/.miro/sqlitedb
INFO     Recomputing filters...
INFO     Spawning global feed dtv:manualFeed
INFO     Spawning global feed dtv:singleFeed
INFO     Spawning global feed dtv:search
INFO     Spawning global feed dtv:searchDownloads
INFO     Creating channel tab order
INFO     Creating playlist tab order
INFO     Spawning Miro Guide...
(u'News and Tech', [u'http://jetset.blip.tv/?skin=rss', u'http://revision3.com/diggnation/feed/quicktime-large', u'http://www.democracynow.org/podcast-video.xml', u'http://downloads.bbc.co.uk/rmhttp/downloadtrial/bbc2/newsnightvideopodcast/rss.xml', u'http://podcast.msnbc.com/audio/podcast/MSNBC-NN-NETCAST-M4V.xml', u'http://feeds.feedburner.com/TEDTalks_video'])
(u'Entertainment', [u'http://feeds.feedburner.com/Terravideos', u'http://feeds.feedburner.com/AskANinja', u'http://feeds.feedburner.com/Theburg/', u'http://feeds.theonion.com/OnionNewsNetwork'])
(u'High-Def', [u'http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml', u'http://www.telemusicvision.com/videos/rss.php', u'http://www.onnetworks.com/videos/shows/25/podcast/hd', u'http://www.kqed.org/.pod/questvideo'])
INFO     Spawning global feed dtv:directoryfeed
INFO     Spawning auto downloader...
INFO     Displaying main frame...
INFO     *** Launching Downloader Daemon ****
WARNING  Menu item action "CheckVersion" not implemented
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
alsa
oss
pulseaudio
none
file
INFO     loaded renderer 'xinerenderer'
TIMING   gtkAsyncMethod: <function initRenderers at 0x8a06e64> took too long: 1.483

** (miro.real:12844): WARNING **: Invalid borders specified for theme pixmap:
        /home/abhiroop/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Range/null.png,
borders don't fit within the image

** (miro.real:12844): WARNING **: Invalid borders specified for theme pixmap:
        /home/abhiroop/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image
TIMING   gtkSyncMethod: <function getDisplay at 0x8a93f44> took too long: 2.006
TIMING   Icon clear: 0.001
INFO     Finished startup sequence
TIMING   idle (Finishing startup) too slow (2.743 secs)
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpCqzjix.html
INFO     got file:///tmp/tmp6lfUW1.html
INFO     got https://www.miroguide.com/
TIMING   feed update for: http://feeds.theonion.com/OnionNewsNetwork too slow (0.542 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://feeds.theonion.com/OnionNewsNetwork)) too slow (0.542 secs)
TIMING   feed update for: http://www.onnetworks.com/videos/shows/25/podcast/hd too slow (0.259 secs)
TIMING   feed update for: http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml too slow (0.682 secs)
TIMING   idle (Thread Pool Callback (Feedparser callback - http://www.washingtonpost.com/wp-srv/mmedia/hd_podcast.xml)) too slow (0.683 secs)
TIMING   feed update for: http://www.democracynow.org/podcast-video.xml too slow (0.239 secs)
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
abhiroop@Vanimo:~$ WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...



```

---

