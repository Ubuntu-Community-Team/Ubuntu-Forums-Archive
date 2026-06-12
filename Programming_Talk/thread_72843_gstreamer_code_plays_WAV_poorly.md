---
title: "gstreamer code plays WAV poorly"
date: 2005-10-07
forum: Programming Talk
---

### Post by SickTwist on 2005-10-07
I'm running Breezy Badger and developing a small voicemail retrieval program in C that will use [GTK+]("http://www.gtk.org/") and [gstreamer]("http://gstreamer.freedesktop.org/").

I'm in the process of learning gstreamer so I copied the following code from the [gstreamer development manual]("http://gstreamer.freedesktop.org/data/doc/gstreamer/stable/manual/html/index.html") to test it:
```
#include <gst/gst.h>

static void
cb_eos (GstElement *play,
	gpointer    data)
{
  gst_main_quit ();
}

static void
cb_error (GstElement *play,
	  GstElement *src,
	  GError     *err,
	  gchar      *debug,
	  gpointer    data)
{
  g_print ("Error: %s\n", err->message);
}

gint
main (gint   argc,
      gchar *argv[])
{
  GstElement *play;

  /* init GStreamer */
  gst_init (&argc, &argv);

  /* make sure we have a URI */
  if (argc != 2) {
    g_print ("Usage: %s <URI>\n", argv[0]);
    return -1;
  }

  /* set up */
  play = gst_element_factory_make ("playbin", "play");
  g_object_set (G_OBJECT (play), "uri", argv[1], NULL);
  g_signal_connect (play, "eos", G_CALLBACK (cb_eos), NULL);
  g_signal_connect (play, "error", G_CALLBACK (cb_error), NULL);
  if (gst_element_set_state (play, GST_STATE_PLAYING) != GST_STATE_SUCCESS) {
    g_print ("Failed to play\n");
    return -1;
  }

  /* now run */
  gst_main ();

  /* also clean up */
  gst_element_set_state (play, GST_STATE_NULL);
  gst_object_unref (GST_OBJECT (play));

  return 0;
}
```

I compiled it with this command:
**[INDENT]gcc -Wall `pkg-config --cflags --libs gstreamer-0.8` gplayer.c -o gplayer[/INDENT]**
The problem is that this simple program cannot play the voicemail wav clearly. The audio is choppy and sounds terrible (when playing from a local file). When I try to play the wav in other programs (like [Beep Media Player]("http://www.sosdg.org/~larne/w/BMP_Homepage")) it plays fine so I know that there is no problem with the file itself.

I've tried [Ogg Vorbis]("http://www.vorbis.com/") and [FLAC]("http://flac.sourceforge.net/") files with this gstreamer code and they both play perfectly so the problem appears to be only with wav files. Here are the specifics about the format of the voicemail wav:
[INDENT][B]
test.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, mono 8000 Hz[/B][/INDENT]

I'm wondering the following:
[LIST]
[*]Is something lacking in the gstreamer code like some sort of element to buffer the file?
[*]Am I missing a gstreamer plug-in? The file does open but perhaps the wrong plug-in is trying to play it.
[*]Is this even feasible--how mature is WAVE/PCM support in gstreamer?
[/LIST]
Thanks in advance for any feedback. :)

---

### Post by SickTwist on 2005-10-07
I just discovered that the gstreamer code from the above example will play *some* wav files:

**RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz** - files of this type play perfectly
**RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, mono 8000 Hz** - files of this type sound choppy and distorted

I thought that this would be important to clarify.

---

