---
title: "Help to run elisa multimedia center on edgy"
date: 2006-11-13
forum: Programming Talk
---

### Post by nicky.7 on 2006-11-13
I've just downloaded the 0.1 version of Elisa Media Center.
I tried to follow the instruction i found at [https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy](https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy)
but i have an error.
After installing the "python-setuptools" package the error changed. Now it says:
Any ideas?

keke@luduspro-desktop:~/apps/elisa-0.1.0$ python elisa.py 
Traceback (most recent call last):
  File "elisa.py", line 6, in ?
    from core import application
  File "/home/keke/apps/elisa-0.1.0/core/application.py", line 24, in ?
    from core import config, log, menu, common
  File "/home/keke/apps/elisa-0.1.0/core/menu.py", line 19, in ?
    from core.signals.misc import state_changed
  File "/home/keke/apps/elisa-0.1.0/core/signals/__init__.py", line 2, in ?
    from pgm.message import signal
ImportError: No module named pgm.message

---

### Post by SamheG on 2006-11-14
This won't help you but I got a problem while launching Elisa too.

I got these errors :
```

samheg@KubuntuPowaaa:~$ elisa
14/11/2006 11:31:19.764  INFO     Using config file : /home/samheg/.elisa/./elisa.conf
14/11/2006 11:31:19.895  INFO     Loaded the plugin 'services'
14/11/2006 11:31:19.896  INFO     Loaded the plugin 'pictures'
14/11/2006 11:31:19.970  INFO     Loaded the plugin 'dvd'
14/11/2006 11:31:19.971  INFO     Loaded the plugin 'music'
14/11/2006 11:31:19.971  INFO     Loaded the plugin 'movies'
14/11/2006 11:31:20.71   INFO     MetaFS plugin won't work without the cache manager
14/11/2006 11:31:20.71   INFO     Un-loading meta_fs
14/11/2006 11:31:20.72   INFO     Loaded the plugin 'meta_fs'
14/11/2006 11:31:20.169  INFO     Loaded the plugin 'local_fs'
14/11/2006 11:31:20.170  INFO     Not found: core.plugins.vfs
14/11/2006 11:31:20.170  INFO     Error was No module named gnomevfs
Traceback (most recent call last):
  File "/usr/bin/elisa", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/application.py", line 241, in start
    app = Application()
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/application.py", line 74, in __init__
    plugin_manager.load_plugins()
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/plugin_manager.py", line 133, in load_plugins
    self.load_plugins_for_entry_point('elisa.%s' % entry_point)
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/plugin_manager.py", line 172, in load_plugins_for_entry_point
    plugin_class = entrypoint.load()
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 1830, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/plugins/vfs.py", line 12, in ?
    import gnomevfs
ImportError: No module named gnomevfs

```

Does anyone know which package I have to install to get this gnomevfs module ?

---

### Post by nicky.7 on 2006-11-14
Try to install gstreamer0.10-gnomevfs or libgnomevfs2-* (search for them in synaptic). Let me know

---

### Post by llonesmiz on 2006-11-14
The gnomevfs module should be in python-gnome2-extras or python-gnome2-desktop.

sudo apt-get install python-gnome2-extras python-gnome2-desktop

---

### Post by FuzZy2006 on 2006-11-14
i'm trying to install this program too, but the error i get is: 
```
Traceback (most recent call last):
  File "elisa.py", line 6, in ?
    from core import application
  File "/home/fuzzy/elisa/core/application.py", line 25, in ?
    from core import config, log, menu, common
  File "/home/fuzzy/elisa/core/menu.py", line 20, in ?
    from core.signals.misc import state_changed
  File "/home/fuzzy/elisa/core/signals/__init__.py", line 17, in ?
    from pgm.message import signal
ImportError: No module named pgm.message

```
I guess it is pigment 1.0 and I tried to install it. It seems I don't have gstreamer0.10 installed(says this during the configure):
```
checking for GSTREAMER... configure: error: Package requirements (gstreamer-0.10 >= 0.10.0) were not met:

No package 'gstreamer-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GSTREAMER_CFLAGS
and GSTREAMER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```The point is than when I look in Synaptic i see that I have a couple of gstreamer packages installed. Is there one that I missed?

---

### Post by nicky.7 on 2006-11-14
I'm at the same point! now i try to post the problem to the "Elisa" mailing list.

---

### Post by llonesmiz on 2006-11-14
> The point is than when I look in Synaptic i see that I have a couple of gstreamer packages installed. Is there one that I missed?

You need to install libgstreamer0.10-dev.

---

### Post by SamheG on 2006-11-14
Thank you llonesmiz !

Indeed it was in python-gnome2-extras
Now Elisa works ... and it ROCKS !

---

### Post by MetalMusicAddict on 2006-11-14
For anyone who didnt know about this project [HERE]("http://www.fluendo.com/elisa/screenshots.php") are some screenshots.

Im kinda at the same point as nicky.7 with SVN and the 0.1.0 release.

0.1.0
```
user@pc:~$ python /home/atm/elisa-0.1.0/elisa.py
Traceback (most recent call last):
  File "/home/user/elisa-0.1.0/elisa.py", line 6, in ?
    from core import application
  File "/home/user/elisa-0.1.0/core/application.py", line 24, in ?
    from core import config, log, menu, common
  File "/home/user/elisa-0.1.0/core/menu.py", line 19, in ?
    from core.signals.misc import state_changed
  File "/home/user/elisa-0.1.0/core/signals/__init__.py", line 2, in ?
    from pgm.message import signal
ImportError: No module named pgm.message
```

SVN
```
user@pc:~$ python /home/atm/.elisa/elisa.py
Traceback (most recent call last):
  File "/home/user/.elisa/elisa.py", line 6, in ?
    from core import application
  File "/home/user/.elisa/core/application.py", line 25, in ?
    from core import config, log, menu, common
  File "/home/user/.elisa/core/menu.py", line 20, in ?
    from core.signals.misc import state_changed
  File "/home/user/.elisa/core/signals/__init__.py", line 17, in ?
    from pgm.message import signal
ImportError: No module named pgm.message
```

---

### Post by FuzZy2006 on 2006-11-14
The program needed to solve that pgm.message problem is called pigment and can be found on the fluendo website. The problem that I encounter is that during the make it says: ```
In file included from pgmrendersink.c:19:
pgmrendersink.h:25:29: error: gst/video/video.h: No such file or directory
pgmrendersink.h:26:36: error: gst/video/gstvideosink.h: No such file or directory
In file included from pgmrendersink.c:19:
pgmrendersink.h:40: error: expected specifier-qualifier-list before 'GstVideoSink'
pgmrendersink.h:54: error: expected specifier-qualifier-list before 'GstVideoSinkClass'
pgmrendersink.c:28: error: 'GST_VIDEO_CAPS_RGB' undeclared here (not in a function)
pgmrendersink.c:41: error: expected ')' before '*' token
pgmrendersink.c:42: error: expected ')' before '*' token
pgmrendersink.c:47: error: expected ')' before '*' token
pgmrendersink.c:48: error: expected ')' before '*' token
pgmrendersink.c:50: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
pgmrendersink.c: In function 'pgm_render_sink_set_property':
pgmrendersink.c:64: error: 'PgmRenderSink' has no member named 'drawable'
pgmrendersink.c: In function 'pgm_render_sink_get_property':
pgmrendersink.c:84: error: 'PgmRenderSink' has no member named 'drawable'
pgmrendersink.c: In function 'pgm_render_sink_class_init':
pgmrendersink.c:108: error: 'GstBaseSinkClass' undeclared (first use in this function)
pgmrendersink.c:108: error: (Each undeclared identifier is reported only once
pgmrendersink.c:108: error: for each function it appears in.)
pgmrendersink.c:108: error: 'gstbasesink_class' undeclared (first use in this function)
pgmrendersink.c:112: error: expected expression before ')' token
pgmrendersink.c:114: error: 'parent_class' undeclared (first use in this function)
pgmrendersink.c:131: error: 'pgm_render_sink_getcaps' undeclared (first use in this function)
pgmrendersink.c:132: error: 'pgm_render_sink_setcaps' undeclared (first use in this function)
pgmrendersink.c:133: error: 'pgm_render_sink_get_times' undeclared (first use in this function)
pgmrendersink.c:134: error: 'pgm_render_sink_show' undeclared (first use in this function)
pgmrendersink.c: In function 'pgm_render_sink_init':
pgmrendersink.c:141: error: 'PgmRenderSink' has no member named 'time'
pgmrendersink.c:142: error: 'PgmRenderSink' has no member named 'framerate_n'
pgmrendersink.c:143: error: 'PgmRenderSink' has no member named 'framerate_d'
pgmrendersink.c:144: error: 'PgmRenderSink' has no member named 'width'
pgmrendersink.c:145: error: 'PgmRenderSink' has no member named 'height'
pgmrendersink.c:146: error: 'PgmRenderSink' has no member named 'mutex'
pgmrendersink.c:147: error: 'PgmRenderSink' has no member named 'drawable'
pgmrendersink.c: In function 'pgm_render_sink_finalize':
pgmrendersink.c:161: error: 'PgmRenderSink' has no member named 'mutex'
pgmrendersink.c: At top level:
pgmrendersink.c:165: error: expected ')' before '*' token
pgmrendersink.c:185: error: expected ')' before '*' token
pgmrendersink.c:210: error: expected ')' before '*' token
pgmrendersink.c:222: error: expected ')' before '*' token
pgmrendersink.c: In function 'pgm_render_sink_change_state':
pgmrendersink.c:250: error: 'PgmRenderSink' has no member named 'time'
pgmrendersink.c:256: error: 'parent_class' undeclared (first use in this function)
pgmrendersink.c: In function 'pgm_render_sink_get_type':
pgmrendersink.c:279: error: 'GST_TYPE_VIDEO_SINK' undeclared (first use in this function)
make[6]: *** [libpgmrendersink_la-pgmrendersink.lo] Error 1
make[6]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment/libs/pgm/render/render'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment/libs/pgm/render/render'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment/libs/pgm/render'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment/libs/pgm'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment/libs'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/fuzzy/Desktop/pigment-0.1.0/pigment'
make: *** [all] Error 2

```
I tried make install, but still got errors. Now, when I try to open elisa it says: ```
Traceback (most recent call last):
  File "/usr/bin/elisa", line 7, in ?
    sys.exit(
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 236, in load_entry_point
    return get_distribution(dist).load_entry_point(group, name)
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 2097, in load_entry_point
    return ep.load()
  File "/usr/lib/python2.4/site-packages/pkg_resources.py", line 1830, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/application.py", line 25, in ?
    from core import config, log, menu, common
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/menu.py", line 20, in ?
    from core.signals.misc import state_changed
  File "/usr/lib/python2.4/site-packages/elisa-0.1.0-py2.4.egg/core/signals/__init__.py", line 17, in ?
    from pgm.message import signal
ImportError: No module named pgm.message

```

---

### Post by MetalMusicAddict on 2006-11-14
I can't get pigment from the website.

```
[SIZE="4"]**Forbidden**[/SIZE]
You don't have permission to access /elisa/downloads/pigment/ on this server.
```
Ok. I found the Trac page for Pigment: [https://core.fluendo.com/pigment/trac/wiki/](https://core.fluendo.com/pigment/trac/wiki/)

I installed it from SNV but I have no clue what to do now.

---

### Post by SamheG on 2006-11-14
@Fuzzy : You need to install these packages :
- libgstreamer-plugins-base0.10-dev

Go [there](http://www.fluendo.com/elisa/developers.php) for a list of all the packages needed to compile Pigment.

@ MetalMusicAddict :
Go [there](https://core.fluendo.com/pigment/trac/)

@ everyone who wants to install Pigment + Elisa, [here](https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy) is an edgy howto with a list of a needed packages.

---

### Post by MetalMusicAddict on 2006-11-14
> **SamheG said:**
> @Fuzzy : You need to install these packages :
- libgstreamer-plugins-base0.10-dev

Go [there](http://www.fluendo.com/elisa/developers.php) for a list of all the packages needed to compile Pigment.

@ MetalMusicAddict :
Go [there](https://core.fluendo.com/pigment/trac/)

@ everyone who wants to install Pigment + Elisa, [here](https://core.fluendo.com/elisa/trac/wiki/ElisaEdgy) is an edgy howto with a list of a needed packages.

SamheG your last link doesnt mention getting pigment working. Its needed for Elisa.

---

### Post by MetalMusicAddict on 2006-11-14
Can someone write up a FAQ for the SVN version? The 2 Trac pages really dont let you know that they go together and the Read Me is a little off.

---

### Post by igknighted on 2006-11-14
> **FuzZy2006 said:**
> i'm trying to install this program too, but the error i get is: 
```
Traceback (most recent call last):
  File "elisa.py", line 6, in ?
    from core import application
  File "/home/fuzzy/elisa/core/application.py", line 25, in ?
    from core import config, log, menu, common
  File "/home/fuzzy/elisa/core/menu.py", line 20, in ?
    from core.signals.misc import state_changed
  File "/home/fuzzy/elisa/core/signals/__init__.py", line 17, in ?
    from pgm.message import signal
ImportError: No module named pgm.message

```
I guess it is pigment 1.0 and I tried to install it. It seems I don't have gstreamer0.10 installed(says this during the configure):
```
checking for GSTREAMER... configure: error: Package requirements (gstreamer-0.10 >= 0.10.0) were not met:

No package 'gstreamer-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GSTREAMER_CFLAGS
and GSTREAMER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```The point is than when I look in Synaptic i see that I have a couple of gstreamer packages installed. Is there one that I missed?

I have this exact same issue.  I ran "whereis gstreamer-0.10" and it found it, so I believe it is installed, the compiler just doesn't know where to find it perhaps?

---

### Post by FuzZy2006 on 2006-11-15
i've finally succeded to install elisa. if you want help for this I can help (as long as i know)

---

### Post by FuzZy2006 on 2006-11-15
for that pgm.message pb you have to download and install pigment from the same site where elisa can be found.

---

### Post by risbac on 2006-11-15
Can someone compile some Edgy packages? I tried to compile it, but it's clearly not the easiest software to compile... But the screenshots look promising. The July version was already quite nice.

---

### Post by nicky.7 on 2006-11-15
I managed to install it. Whan you have compiled Pigment (the dipendencies listed in [https://core.fluendo.com/pigment/trac/browser/trunk/README#L42](https://core.fluendo.com/pigment/trac/browser/trunk/README#L42) are ok) you have still to apt-get install python-celementtree.

Is it difficult to build a deb package? 
Is there some detailed instruction?
And where to host the file then?

---

### Post by Arless on 2006-11-17
i have all the dependencies and pigment compiled and installes but i still have the No module named pgm.message message!

---

### Post by visible on 2007-07-15
could someone please help me configure Elisa?  I cannot figure out what I am supposed to put in the elisa.conf file or where to put it.

---

### Post by Mr Al on 2007-08-01
Visible, if you've installed Elisa system wide (e.g. through a package, or by running python setup.py install), then elisa.conf should live in your .elisa directory, which is in your home directory (e.g. /home/visible/.elisa/elisa.conf).

The main thing to do with your elisa.conf is to provide the locations of the different media you have, i.e. where you store your photos, music, and videos. [This]("https://core.fluendo.com/elisa/trac/wiki/FirstRun") page from the Elisa wiki tells you how to do this.

---

