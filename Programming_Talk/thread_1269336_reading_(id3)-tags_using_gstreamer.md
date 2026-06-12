---
title: "reading (id3)-tags using gstreamer"
date: 2009-09-18
forum: Programming Talk
---

### Post by _winnetou_ on 2009-09-18
hey everyone,
i have a c-application and i like to read tags from any audio file. is there any way to this using gstreamer?
i tryed to google this but it was hopeless to me :/
would be kinda nice if anyone would show me an example...  or at least some link where everything is shown.
thanks^^

---

### Post by SledgeHammer_999 on 2009-09-18
You should read the [Application Development Manual](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html), which is available on the site.

For your question read this [section.](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-metadata.html#section-tags-read)

If you still have questions, feel free to ask.

---

### Post by _winnetou_ on 2009-09-18
thanks alot^^
.. so i'll be doing this
```

GstElement *source;
source = gst_element_factory_make ("filesrc", "file-source");
g_object_set (G_OBJECT (source), "location", "/path/to/some/audio/file", NULL);

GstCaps *caps;
caps = gst_caps_new_simple ("dunno-what-media-type", NULL);

const GstStructure *str;
str = gst_caps_get_structure (caps, 0); // here we have all the tags

```
so my question is, does this work and what media type should i specify if i would like to read any audio file... or do i need to check which media type the source is and then specify it in gst_caps_new_simple?

---

### Post by SledgeHammer_999 on 2009-09-18
ummm no...

If you want metadata like artist/album/track name etc pay attention to this:
>  Tag reading is done through a bus in GStreamer, which has been discussed previously in Chapter 7. You can listen for GST_MESSAGE_TAG messages and handle them as you wish.

Note, however, that the GST_MESSAGE_TAG message may be fired multiple times in the pipeline. It is the application's responsibility to put all those tags together and display them to the user in a nice, coherent way. Usually, using gst_tag_list_merge () is a good enough way of doing this; make sure to empty the cache when loading a new song, or after every few minutes when listening to internet radio. Also, make sure you use GST_TAG_MERGE_PREPEND as merging mode, so that a new title (which came in later) has a preference over the old one for display.

If you want metadata like bitrate/frequency etc(technical styff):
you must examine the GstCaps of every GstPad created in each element in your pipeline.(after you have fully decoded the stream).

I could give example code but I'll let you experiment and understand how gstreamer works(and not spoon feed you the answer).
However, if you still have questions, I will answer.

---

### Post by _winnetou_ on 2009-09-18
okay everything works... is it not too sucky if i just use playbin just for tag reading?

---

### Post by SledgeHammer_999 on 2009-09-19
I don't think so. I think it is the recommended way of decoding files...

---

### Post by _winnetou_ on 2009-09-19
okay here is what i tried.. and it works fine on mp3-files... but it doesnt work on ogg... :/ and well that file has definitly a tag (looked up with that property window in nautilus)
```


GMainLoop *loop;
GstElement *tagger_element;
gchar *artist;
gboolean got_message_tag;

void *run_gst_main_loop( void *data )
{
    g_main_loop_run (loop);
    return NULL;
}

static gboolean tagger_bus_call (GstBus *bus, GstMessage *msg, gpointer data)
{
    GstTagList *t;
    switch (GST_MESSAGE_TYPE (msg))
    {
        case GST_MESSAGE_TAG:
            t = gst_tag_list_new ();
            gst_message_parse_tag (msg, &t);        
            got_message_tag = TRUE;
            gst_tag_list_get_string (t, "artist", &artist);
            break;
        default:
            break;
    }
    return TRUE;
}

void init(int argc, char *argv[])
{
    gst_init (&argc, &argv);

    tagger_element = gst_element_factory_make ("playbin", "tagger");
    GstBus *bus = gst_pipeline_get_bus (GST_PIPELINE (tagger_element));
    gst_bus_add_watch (bus, tagger_bus_call, loop);
    gst_object_unref (bus);

    loop = g_main_loop_new (NULL, FALSE);
    g_thread_create((GThreadFunc)run_gst_main_loop, NULL, TRUE, NULL);
}

gchar *get_artist (gchar *location)
{
    GString *uri = g_string_new("");
    g_string_printf (uri, "file://%s", location);
    g_object_set (G_OBJECT (tagger_element), "uri", uri->str, NULL);
    got_message_tag = FALSE;
    gst_element_set_state (tagger_element, GST_STATE_PAUSED);
    while (!got_message_tag) {}
    gst_element_set_state (tagger_element, GST_STATE_NULL);
    return artist;
}

```
so i have no idea whats wrong with that :/

---

### Post by SledgeHammer_999 on 2009-09-19
You should use:
```
gst_tag_list_get_string (t, "artist", &artist);
```
insted of:
```
gst_tag_list_get_string (t, GST_TAG_ARTIST, &artist);
```

but I don't think this causes your problem. As I see it, your code should work!
Are you sure that you get a TAG message when you play the ogg file?(put a g_print() in 'case GST_MESSAGE_TAG').

---

### Post by _winnetou_ on 2009-09-19
well i figured out some sort of way to do it.. dunno why it works..

```

GMainLoop *tagger_loop;
GstElement *tagger_element;
GstTagList *tag_list;

static gboolean tagger_bus_call (GstBus *bus, GstMessage *msg, gpointer data)
{
    GMainLoop *loop = (GMainLoop *) data;
    switch (GST_MESSAGE_TYPE (msg))
    {
        case GST_MESSAGE_TAG:
            tag_list = gst_tag_list_new ();
            gst_message_parse_tag (msg, &tag_list);    
            g_main_loop_quit (loop);
            break;
        default:
            break;
    }
    return TRUE;
}

void init(int argc, char *argv[])
{
    gst_init (&argc, &argv);

    tagger_element = gst_element_factory_make ("playbin", "tagger");

    tagger_loop = g_main_loop_new (NULL, FALSE);
    
    GstBus *bus = gst_pipeline_get_bus (GST_PIPELINE (tagger_element));
    gst_bus_add_watch (bus, tagger_bus_call, tagger_loop);
    gst_object_unref (bus);

}

GstTagList *get_tag_list (gchar *location)
{
    GString *uri = g_string_new("");
    g_string_printf (uri, "file://%s", location);
    
    gst_element_set_state (tagger_element, GST_STATE_NULL);
    g_object_set (G_OBJECT (tagger_element), "uri", uri->str, NULL);
    gst_element_set_state (tagger_element, GST_STATE_PAUSED);
    g_main_loop_run (tagger_loop);
    return tag_list;
}

```

thanks alot :)

---

### Post by SledgeHammer_999 on 2009-09-20
no problem.

---

### Post by SledgeHammer_999 on 2009-09-20
> **_winnetou_ said:**
> well i figured out some sort of way to do it.. dunno why it works..

```

GMainLoop *tagger_loop;
GstElement *tagger_element;
GstTagList *tag_list;

static gboolean tagger_bus_call (GstBus *bus, GstMessage *msg, gpointer data)
{
    GMainLoop *loop = (GMainLoop *) data;
    switch (GST_MESSAGE_TYPE (msg))
    {
        case GST_MESSAGE_TAG:
            tag_list = gst_tag_list_new ();
            gst_message_parse_tag (msg, &tag_list);    
            g_main_loop_quit (loop);
            break;
        default:
            break;
    }
    return TRUE;
}

void init(int argc, char *argv[])
{
    gst_init (&argc, &argv);

    tagger_element = gst_element_factory_make ("playbin", "tagger");

    tagger_loop = g_main_loop_new (NULL, FALSE);
    
    GstBus *bus = gst_pipeline_get_bus (GST_PIPELINE (tagger_element));
    gst_bus_add_watch (bus, tagger_bus_call, tagger_loop);
    gst_object_unref (bus);

}

GstTagList *get_tag_list (gchar *location)
{
    GString *uri = g_string_new("");
    g_string_printf (uri, "file://%s", location);
    
    gst_element_set_state (tagger_element, GST_STATE_NULL);
    g_object_set (G_OBJECT (tagger_element), "uri", uri->str, NULL);
    gst_element_set_state (tagger_element, GST_STATE_PAUSED);
    g_main_loop_run (tagger_loop);
    return tag_list;
}

```

thanks alot :)

I think I spotted a potential problem. You should create a pipeline with gst_pipeline_new(). Then create the playbin element and add it to the pipeline(with **gst_bin_add(GST_BIN(pipeline), playbin)**). Then add a watch to the **pipeline's** bus and not the playbin's bus. Then proceed to make the playbin to the PAUSED state and then the pipeline to the PAUSED state.

I think the way you do it now, you catch the TAG messages of the different elements playbin uses internally and not the TAG messages playbin emmits.

---

