---
title: "Including from GStreamer Base plugin"
date: 2010-02-07
forum: Programming Talk
---

### Post by PaulM1985 on 2010-02-07
Hi

I want to make a program which uses some of the classes from the GStreamer base plugin.  The problem is, I can't find anywhere in the documentation what I am supposed to include in the top of the file to use the classes I would like to use and if I need to add anything on the compilation line.  In the example below, I want to use the GstTCPServerSink class.  Here is my test.cpp and my make file:

```

#include <gst/gst.h>
#include <glib.h>

static gboolean
bus_call (GstBus     *bus,
          GstMessage *msg,
          gpointer    data)
{
  GMainLoop *loop = (GMainLoop *) data;

  switch (GST_MESSAGE_TYPE (msg)) {

    case GST_MESSAGE_EOS:
      g_print ("End of stream\n");
      g_main_loop_quit (loop);
      break;

    case GST_MESSAGE_ERROR: {
      gchar  *debug;
      GError *error;

      gst_message_parse_error (msg, &error, &debug);
      g_free (debug);

      g_printerr ("Error: %s\n", error->message);
      g_error_free (error);

      g_main_loop_quit (loop);
      break;
    }
    default:
      break;
  }

  return TRUE;
}


static void
on_pad_added (GstElement *element,
              GstPad     *pad,
              gpointer    data)
{
  GstPad *sinkpad;
  GstElement *decoder = (GstElement *) data;

  /* We can now link this pad with the vorbis-decoder sink pad */
  g_print ("Dynamic pad created, linking demuxer/decoder\n");

  sinkpad = gst_element_get_static_pad (decoder, "sink");

  gst_pad_link (pad, sinkpad);

  gst_object_unref (sinkpad);
}



int
main (int   argc,
      char *argv[])
{
  GMainLoop *loop;

  GstElement *pipeline, *source, *demuxer, *decoder, *conv;
	GstTCPServerSink *sink;
  GstBus *bus;

  /* Initialisation */
  gst_init (&argc, &argv);

  loop = g_main_loop_new (NULL, FALSE);


  /* Check input arguments */
  if (argc != 2) {
    g_printerr ("Usage: %s <Ogg/Vorbis filename>\n", argv[0]);
    return -1;
  }


  /* Create gstreamer elements */
  pipeline = gst_pipeline_new ("audio-player");
  source   = gst_element_factory_make ("filesrc",       "file-source");
  demuxer  = gst_element_factory_make ("oggdemux",      "ogg-demuxer");
  decoder  = gst_element_factory_make ("vorbisdec",     "vorbis-decoder");
  conv     = gst_element_factory_make ("audioconvert",  "converter");
  sink     = gst_element_factory_make ("tcpserversink", "audio-output");

  if (!pipeline || !source || !demuxer || !decoder || !conv || !sink) {
    g_printerr ("One element could not be created. Exiting.\n");
    return -1;
  }

  /* Set up the pipeline */

  /* we set the input filename to the source element */
  g_object_set (G_OBJECT (source), "location", argv[1], NULL);

  /* we add a message handler */
  bus = gst_pipeline_get_bus (GST_PIPELINE (pipeline));
  gst_bus_add_watch (bus, bus_call, loop);
  gst_object_unref (bus);

  /* we add all elements into the pipeline */
  /* file-source | ogg-demuxer | vorbis-decoder | converter | alsa-output */
  gst_bin_add_many (GST_BIN (pipeline),
                    source, demuxer, decoder, conv, sink, NULL);

  /* we link the elements together */
  /* file-source -> ogg-demuxer ~> vorbis-decoder -> converter -> alsa-output */
  gst_element_link (source, demuxer);
  gst_element_link_many (decoder, conv, sink, NULL);
  g_signal_connect (demuxer, "pad-added", G_CALLBACK (on_pad_added), decoder);

  /* note that the demuxer will be linked to the decoder dynamically.
     The reason is that Ogg may contain various streams (for example
     audio and video). The source pad(s) will be created at run time,
     by the demuxer when it detects the amount and nature of streams.
     Therefore we connect a callback function which will be executed
     when the "pad-added" is emitted.*/


  /* Set the pipeline to "playing" state*/
  g_print ("Now playing: %s\n", argv[1]);
  gst_element_set_state (pipeline, GST_STATE_PLAYING);


  /* Iterate */
  g_print ("Running...\n");
  g_main_loop_run (loop);


  /* Out of the main loop, clean up nicely */
  g_print ("Returned, stopping playback\n");
  gst_element_set_state (pipeline, GST_STATE_NULL);

  g_print ("Deleting pipeline\n");
  gst_object_unref (GST_OBJECT (pipeline));

  return 0;
}

```

```

CC = g++
CFLAGS = -Wall
PROG = MyProgram

#Source files
SRCS = test.cpp

#Compiler flags
CFLAGS=-Wall

#libraries
GStream_LIBS=`pkg-config --cflags --libs gstreamer-0.10`

all: $(PROG)

$(PROG):	$(SRCS)
	$(CC) $(CFLAGS) -o $(PROG) $(SRCS) $(GStream_LIBS)

clean:
	rm -f $(PROG)

```

I keep getting a message saying that GstTCPServerSink is not declared.  Is there any documentation on this?  What do I need to include for this and is there anything I need to include for compilation?

I have downloaded all GStreamer plugins from the repository.

Paul

---

### Post by PaulM1985 on 2010-02-07
I think I have found the shared object that I need for this class.

It is in the path:

/usr/lib/gstreamer-0.10/libgsttcp.so.

How would I change my makefile to link to this shared object.  I am quite new with make files and not exactly sure how they work.

Paul

---

### Post by SledgeHammer_999 on 2010-02-07
Since you're using something from gstreamer base you need to pass these args as well:
```
`pkg-config --cflags --libs gstreamer-base-0.10`
```

I am not familiar with shell scripting but if you change your makefile to this it should work:
```
GStream_LIBS=`pkg-config --cflags --libs gstreamer-0.10 gstreamer-base-0.10`
```

PS: remember to download the gstreamer-base-dev files since it contains the appropriate header files.

PS2: You don't actually need any of this. As I see it GstTCPServerSink is just another GstElement. Why don't you do a **GstElement *sink;** instead of a **GstTCPServerSink *sink;**?

---

### Post by PaulM1985 on 2010-02-07
Thanks for the advice with the make file.  I think I need to declare it as a GstTCPServerSink element because I want to define the port for it. How would I be able to find out which headers I need to include?

Paul

---

### Post by SledgeHammer_999 on 2010-02-07
No you don't need to declare it that way. Actually you can't, that's why you can't find which header to include.

This element has "properties" like every other gstelement. You can get and set these properties. To see what properties each element has you can read the docs or do in the command line a "gst-inspect-0.10 elementname". (ie elementname=filerc). Read more about this in the gobject docs.

tcpserversink has a property named "port"-->[link](http://www.gstreamer.net/data/doc/gstreamer/devel/gst-plugins-base-plugins/html/gst-plugins-base-plugins-tcpserversink.html#GstTCPServerSink--port)
You can set it the exact same way you set filesrc's "location" property.
Eg: g_object_set (G_OBJECT (sink), "port", 100, NULL);

(I used 100 for port number)

If I didn't explain it well, please ask me to clarify.

---

### Post by PaulM1985 on 2010-02-09
Thanks SledgeHammer_999

That seemed to allow it to compile.

I have made a second program, Prog2, with only a source and a sink, "tcpclientsrc" and "autoaudiosink" respectively.  I have set this to have the same port as the tcpserversrc.  I have left the "host"s to be default as I think this should be localhost.

My plan was to start Prog1, the server, and then start Prog2, the client.  Both of the files compile ok, but I don't get any sound when they are running.

Is there a special way that things have to be linked for streaming via a network as I thought this would probably do it.  I was thinking maybe I needed to add a "queue" in Prog1?  Do you/anyone else know of any other documentation regarding this area?  I have had a good look on the net and there seems to be quite little.

If all else fails I would probably run files from a webserver on one machine to another, but I would prefer to keep the webserver free for hosting.

Any info on solving my problem would be greatly appreciated.

Paul

---

### Post by SledgeHammer_999 on 2010-02-09
I have no experience regarding this area. I don't even know if your pipeline should work the way you won't. Here's a tip to discover if the pipeline is "correct". Open 2 terminal windows. In the first type ```
gst-launch-0.10 filesrc location="path to ogg gile" ! oggdemux ! queue ! vorbisdec ! audioconvert ! tcpserversink
``` and in the second one type ```
gst-launch-0.10 tcpclientsrc ! autoaudiosink
```

If the pipeline is correct, you should hear the sound playing.

---

### Post by PaulM1985 on 2010-02-12
Thanks for the help.  Going to go with the webserver idea and use URIs.

Paul

---

