---
title: "GStreamer - connecting dynamic pads"
date: 2011-11-05
forum: Programming Talk
---

### Post by dwalker0044 on 2011-11-05
Hi I'm trying to write a program using GStreamer which opens and plays an mp4 file. 

From the command line it would look like:

```

gst-launch filesrc location=file.mp4 ! decodebin2 ! autovideosink

```

I have been unable to get this to work using code. The problem I expect is somehow related to the fact that decodebin2 has a dynamic src pad. I've attempted to attach a callback which would allow me to connect the pad appropriately, however the callback is never called and the main loop appears to do nothing (program exits immediately).

I'd really appreciate it if someone could point out what I'm doing wrong! I can post more code if required.

Thanks,

```

pipeline  = gst_pipeline_new ("pipeline");
source    = gst_element_factory_make("filesrc",       "source");
decodebin = gst_element_factory_make("decodebin2",   "decodebin");
videosink = gst_element_factory_make("autovideosink", "videosink");

/* check elements were created successfully */
if (!pipeline || !source || !decodebin || !videosink) {
    // Failed to create element. Exit Program
    return -1;
}
    
/* apply properties to elements before adding to pipeline */
gchar * filename = "bbb.mp4";
g_object_set(G_OBJECT(source), "location", filename, NULL);

    /* add a message handler */
    bus = gst_pipeline_get_bus (GST_PIPELINE (pipeline));
    gst_bus_add_watch (bus, bus_call, loop);
    gst_object_unref (bus);

/* add elements to pipeline (and bin if necessary) before linking them */
gst_bin_add_many(GST_BIN (pipeline),
                     source,
                     decodebin,
                     videosink,
                     NULL);

gst_element_link_pads(source, "src", decodebin, "sink");

/* decodebins src pad is a sometimes pad - it gets created dynamically */
g_signal_connect(decodebin, "new-decoded-pad", G_CALLBACK(on_new_decoded_pad),   videosink);

/* run pipeline */
gst_element_set_state(GST_ELEMENT(pipeline), GST_STATE_PLAYING);


```

---

