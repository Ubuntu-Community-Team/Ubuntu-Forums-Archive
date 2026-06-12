---
title: "PyGST: File coming up empty"
date: 2010-11-01
forum: Programming Talk
---

### Post by Tahakki on 2010-11-01
The following code is supposed to mux sound and video into a .mp4 file, the file appears but shows up empty. No error messages are given.

```
                filmPipe = gst.Pipeline("filmPipe")
                filmSrc = gst.element_factory_make("multifilesrc", "filmSrc")
                filmSrc.set_property("location", "pictures/%d.png")
                filmFilt1 = gst.element_factory_make("capsfilter", "filmFilt1")
                filmCap1 = gst.Caps("image/png,framerate=5/1,pixel-aspect-ratio=1/1")
                filmFilt1.set_property("caps", filmCap1)
                filmPngDec = gst.element_factory_make("pngdec", "filmPngDec")
                filmff = gst.element_factory_make("ffmpegcolorspace", "filmff")
                filmFilt2 = gst.element_factory_make("capsfilter", "filmFilt2")
                filmCap2 = gst.Caps("video/x-raw-yuv")
                filmFilt2.set_property("caps", filmCap2)
                filmTheora = gst.element_factory_make("xvidenc", "filmTheora")
                filmQue = gst.element_factory_make("queue", "filmQue")
                filmOggmux = gst.element_factory_make("ffmux_mp4", "filmOggmux")
                filmFilesink = gst.element_factory_make("filesink", "filmFilesink")
                filmFilesink.set_property("location", self.movPath)
                musicSrc = gst.element_factory_make("filesrc", "musicSrc")
                musicSrc.set_property("location", self.musicPath)
                musicDec = gst.element_factory_make("ffdec_mp3", "musicDec")
                musicEnc = gst.element_factory_make("lame", "musicEnc")
                musicQue = gst.element_factory_make("queue", "musicQue")

                filmPipe.add(filmSrc, filmFilt1, filmPngDec, filmff, filmFilt2, filmTheora, filmQue, filmOggmux, filmFilesink)
                filmPipe.add(musicSrc, musicDec, musicEnc, musicQue)
                gst.element_link_many(filmSrc, filmFilt1, filmPngDec, filmff, filmFilt2, filmTheora, filmQue, filmOggmux, filmFilesink)
                gst.element_link_many(musicSrc, musicDec, musicEnc, musicQue, filmOggmux)
                filmPipe.set_state(gst.STATE_PLAYING)
```

Does anyone know what's wrong?

---

### Post by Tahakki on 2010-11-02
Bump?

---

### Post by worksofcraft on 2010-11-02
IDK but here is a very simple python gst base class.

First try it to see if it plays the "drip.ogg" system sound.

Then edit the file name to identify your video and see if that works... it does play them on my computer.
[php]
#!/usr/bin/python
import gst # gstreamer
import glib

class Playbin2:
	def __init__(self):
		self.idle = True # not playing at the moment
		# create a playbin2 pipe
		self.player = gst.element_factory_make("playbin2", "player")
		# connect a signal handler to it's bus
		bus = self.player.get_bus()
		bus.add_signal_watch()
		bus.connect("message", self.on_message)

	def on_message(self, bus, message):
		t = message.type
		if t == gst.MESSAGE_EOS:
			self.player.set_state(gst.STATE_NULL)
			self.idle = True
		elif t == gst.MESSAGE_ERROR:
			err, debug = message.parse_error()
			print >> sys.stderr, "Error: {0} {1}".format(err, debug)
			self.player.set_state(gst.STATE_NULL)
			self.idle = True
		return self.idle

	def play(self, stream):
		# abort previous play if still busy
		if not self.idle:
			print >> sys.stderr, 'audio truncated'
			self.player.set_state(gst.STATE_NULL)
		self.player.set_property("uri", stream)
		self.player.set_state(gst.STATE_PLAYING)
		self.idle = False # now playing

# a test program for our basic gstreamer class
# plays a standard system sound than hangs in message pump loop
# use Ctrl-C to get out
if __name__ == "__main__":
	Playbin2().play("File:///usr/share/sounds/gnome/default/alerts/drip.ogg")
	glib.MainLoop().run()
[/php]

---

### Post by Tahakki on 2010-11-02
I know the file's empty - it shows up as having zero bytes. The issue must be with my code.

---

