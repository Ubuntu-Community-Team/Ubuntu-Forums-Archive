---
title: "Getting started with gstreamer or MLT"
date: 2009-08-06
forum: Programming Talk
---

### Post by wkulecz on 2009-08-06
I'm using Ubuntu 8.04 with all the gstreamer-0.10 packages installed.  I've managed to compile the Hello World sample program from the Gstreamer Application Programmer Manual and it seems to work fine playing back a sample ogg audio file.

My next step is to try and get the samples and template files mentioned in the Plug-in Programming Guide.  All I see at the gstreamer site is a current tarball.  My concern is I don't want to break my current gstreamer setup and would prefer to develop for the verison of gstreamer used on 8.04 at present.

Can I just extract the samples and templates from the current tarball and expect to use them or be full of wrong version headaches?

I'm not committed to gstreamer at present, and I see a lot to dislike about it, but it seems to be the multimedia future for Linux. 

MLT is a potential alternate, but so far I've found less documentation and samples for it than for gstreamer.

--wally.

Edit.  It appears MLT is out as it appears to lack a video4linux or video4linux2 "producer" module.

---

### Post by wkulecz on 2009-08-06
Oh well, looks like gstreamer is no good for me either.  If I launch two sample video capture streams:

gst-launch v4l2src ! xvimagesink
gst-launch v4l2src device=/dev/video1 ! xvimagesink

Whichever one is launched last randomly dies after a few minutes, the first one usually seems to run OK.  The video sources are genlocked.

Showstopper problem.

--wally.


Edit:

gst-launch v4l2src ! gueue ! xvimagesink
gst-launch v4l2src device=/dev/video1 ! gueue ! xvimagesink

seems to fix the issue.

While Googling about gstreamer programming, I keep finding comments to the effect "gstreamer has good documentation", well not by my definition of good based on what I've found at the gstreamer web site.  I was able to download the gstreamer source from there for the 0.10-18 version used in Ubuntu 8.04.

---

### Post by mcphargus on 2009-08-08
Some of the documentation might be on the lousy side, but when you start using the gst-inspect tool (comes down the apt as gstreamer-tools-0.10) and the gobject-query tool, the tunnel gets a little brighter.

The more you tinker with it the more it starts to feel like Lego's for masochists.

---

### Post by wkulecz on 2009-08-11
Playing with gst-launch I'm a bit concerned about its performance.

I captured an mjpeg video clip with a gst-launch pipeline, quite impressively easy.  But playing it back in a gst-launch pipeline or a gstreamer based player like "Totem", it consumes 20-30% cpu.  Playing the same file back in "Mplayer" (non-gstreamer based) consumes only 10-15%


Here is what I've had to do to get the "helloworld.c" gstreamer sample file to compile on Ubuntu 8.04, perhaps these are fixed on newer versions, but the gstreamer-dev packages did not set up the symlinks needed for #include <gst.h> and all its sub-includes to work.


I'm posting it here so perhaps some other poor soul trying to get started with gstreamer can find it via Google. I found precious little, except for one final key piece of information.

```

sudo -i
cd /usr/include
ln -s /usr/include/glib-2.0/gio gio
ln -s /usr/include/libxml2/libxml libxml
ln -s /usr/include/glib-2.0/gmodule.h gmodule.h
ln -s /usr/include/glib-2.0/gobject gobject
ln -s /usr/include/glib-2.0/glib-object.h glib-object.h
ln -s /usr/lib/glib-2.0/include/glibconfig.h glibconfig.h
ln -s glib-2.0/glib.h glib.h
ln -s gstreamer-0.10/gst gst

```
All the above may only be needed for Ubuntu 8.04, I'd hope.


Compile the sample program with:
```

gcc -Wall $(pkg-config --cflags --libs gstreamer-0.10) HelloGstreamer.c -o HelloGstreamer

```

This is fine if all you need to do is manipulate media streams as in a media player application, but if you want to actually touch the media data you will need to write a plug-in.  If there is an easier way, please let me know!


The first problem is finding the template files mentioned in the Plugin Writers Guide (found in the top level "Documentation" tab at the gstreamer site, good start, but its downhill quickly after this).  These are only available from the gstreamer git repository so after installing git:
```

git clone git://anongit.freedesktop.org/gstreamer/gst-template.git

```

But this didn't work for me.  I filed a Bugzilla report and got an answer reasonably quickly that a firewall was likely blocking telnet access on port 9418.  At that point I was dead in the water, but fortunately the Bugzilla responder made *.gz file of the tree the git command would produce and Emailed me a link to download it.

At that point following the instructions in the Plugin Writers Guide got me nowhere, that's when I found this with Google:
[http://www.nabble.com/Novice-td24209412.html](http://www.nabble.com/Novice-td24209412.html)

Which had the key piece of info, You have to modify the Makefile.am, good luck if you don't understand automake.  But since it is a generated template, for a single plugin its not too hard.  Every place the substring "plugin" occurs in a non-commented line in the Makefile.am you need to replace it with the name you gave in the ../tools/make_element command.

For example:

```

cd gst-template/gst-plugin/src
../tools/make_element wally
gedit Makefile.am
./autogen.sh
make

```
will build the generated gstwally.c produced by the make_element tool from the template.

My edited Makefile.am
```

# plugindir is set in configure

##############################################################################
# change libgstplugin.la to something more suitable, e.g. libmysomething.la  #
##############################################################################
plugin_LTLIBRARIES = libgstwally.la

##############################################################################
# for the next set of variables, rename the prefix if you renamed the .la,   #
#  e.g. libgstplugin_la_SOURCES => libmysomething_la_SOURCES                 #
#       libgstplugin_la_CFLAGS  => libmysomething_la_CFLAGS                  #
#       libgstplugin_la_LIBADD  => libmysomething_la_LIBADD                  #
#       libgstplugin_la_LDFLAGS => libmysomething_la_LDFLAGS                 #
##############################################################################

# sources used to compile this plug-in
libgstwally_la_SOURCES = gstwally.c

# flags used to compile this plugin
# add other _CFLAGS and _LIBS as needed
libgstwally_la_CFLAGS = $(GST_CFLAGS)
libgstwally_la_LIBADD = $(GST_LIBS) $(GST_BASE_LIBS) $(GSTCTRL_LIBS)
libgstwally_la_LDFLAGS = $(GST_PLUGIN_LDFLAGS)
libgstwally_la_LIBTOOLFLAGS = --tag=disable-static

# headers we need but don't want installed
noinst_HEADERS = gstwally.h

```
Note everywhere a line was XYZZYpluginFOOBAR I made it XYZZYwallyFOOBAR.


Now you have to tell gstreamer where to find your custom plugin:

```

export GST_PLUGIN_PATH=/home/wally/gst-template/gst-plugin/src/.libs

```

After this you can test your plugin with:

```

gst-launch -v -m fakesrc ! wally ! fakesink silent=TRUE

```

Now you've got the build mechanics correct and can finally get to work with your development by learning the gstreamer objects and editing your gstXXXXX.c file to use them to accomplish your task.

HTH,
--wally.

---

### Post by wkulecz on 2009-08-14
Another of the gstreamer developers got back to me about not being able to get the templates, and offered a couple more possibilities.

The details are here:
[http://bugzilla.gnome.org/show_bug.cgi?id=591069](http://bugzilla.gnome.org/show_bug.cgi?id=591069)

I have verified on another system here that the "git over http" works through our firewall:
git clone [http://anongit.freedesktop.org/git/gstreamer/gst-template.git](http://anongit.freedesktop.org/git/gstreamer/gst-template.git)


So far I'm finding the graphical Gstreamer Pipeline Editor and Gstreamer Plugin Inspector tools to be pretty much useless.


I'm close to giving up on the idea of using gstreamer for this project as the v4lsrc and v4l2src plugins seem flaky and unable to properly initialize the video card after a boot or reset or most any error condition (like no signal).  If I run TVtime on the card first, then the v4l2src usually seems to work. 

There also doesn't seem to be a usable gstreamer based TV viewer, so at this point its not looking like the gstreamer infrastructure is really very good for live video.  I will say that based on Amarock 1.4 gstreamer must be very good for audio.


TVtime is the only Linux TV viewer that has so far "just worked" for me.  It looks like my next best step might be to study its source code for its video4linux2 capture and X display techniques.

My current version of the project uses a mishmash of v4l and v4l2 along with some low level shared memory Xwindows operations.  I got it working quickly in 2005/06 and have refined it, but for simplicity I punted complexity and only run it on systems where the X server is set to 16-bit color depth beforehand. I'd like to use more modern techniques that seem to handle 16 vs. 24/32 bit X sever color depth "automatically" for the next version, which TVtime seems to do. 


Attached is a screenshot from the Plugin Inspector:
How any of this is supposed to be helpful or useful is beyond me!

Reading the Gnome and Gstreamer docs, all I can say is if you really want an object oriented design (which always seems to promise far more than it can deliver in my experience) and C compatibility, its better to just use C++ than to reinvent it badly with M4 and C preprocessor macros!

--wally.

---

