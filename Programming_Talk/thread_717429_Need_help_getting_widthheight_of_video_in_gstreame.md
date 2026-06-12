---
title: "Need help getting width/height of video in gstreamer"
date: 2008-03-07
forum: Programming Talk
---

### Post by RJ8722 on 2008-03-07
I'm not having much luck in getting the width and height of a video so I can set my GtkDrawable widget to the correct size. Here are bits and pieces of the related code and I hope someone can help me figure this out.

The variables play and videoSink are of type GstElement * and declared as global variables.

```

void stream_foreach(gpointer data, gpointer user_data)
{
	gint streamtype;
	g_object_get(G_OBJECT(data), "type", &streamtype, NULL);
	if(streamtype == 2)
	{
		gint width = 0;
		gint height = 0;
		GstCaps *gcaps;
		const GstStructure *gstr;
		
		g_object_get(G_OBJECT(data), "caps", &gcaps, NULL);
		if(gcaps != NULL)
		{
			gstr = gst_caps_get_structure(gcaps, 0);

			gst_structure_get_int(gstr, "width", &width);
			gst_structure_get_int(gstr, "height", &height);

			gtk_widget_set_size_request(wc.videoDrawArea, width, height);
		}
	}
	g_object_unref(data);
}

gboolean playbin_bus_callback(GstBus *bus, GstMessage *message, gpointer data)
{
	switch (GST_MESSAGE_TYPE(message))
	{
		case GST_MESSAGE_STATE_CHANGED:
			{
				GstState oldstate, newstate;

				if(GST_MESSAGE_SRC(message) != GST_OBJECT(play))
					break;
					
				gst_message_parse_state_changed(message, &oldstate, &newstate, NULL);
				if(oldstate == GST_STATE_READY && newstate == GST_STATE_PAUSED)
				{
					/* Get stream info */
					GList *streaminfo = NULL;
					g_object_get(G_OBJECT(play), "stream-info", &streaminfo, NULL);
					g_list_foreach(streaminfo, stream_foreach, NULL);
					g_list_free(streaminfo);
				}
			}
			break;
		default:
			break;
	}
	return TRUE;
}

```

```

void m_init()
{
	videoSink = gst_element_factory_make("xvimagesink", "myXvSink");
	play = gst_element_factory_make("playbin", "play");
	g_object_set(G_OBJECT(play), "video-sink", videoSink, NULL);
	
	GstBus *bus = gst_pipeline_get_bus(GST_PIPELINE(play));
	gst_bus_add_watch(bus, playbin_bus_callback, NULL);
	gst_object_unref(bus);
}

```
```

void on_playButton_clicked(GtkWidget *widget, gpointer data)
{
	gst_x_overlay_set_xwindow_id(GST_X_OVERLAY(videoSink), GDK_WINDOW_XID(wc.videoDrawArea->window));
	GstState curState;
	gst_element_get_state(play, &curState, NULL, -1);
	if(curState == GST_STATE_PAUSED)
	{
		gst_element_set_state(play, GST_STATE_PLAYING);
		g_timeout_add(500, updatePlay_timeout_callback, NULL);
	}
	else
	{
		gst_element_set_state(play, GST_STATE_PAUSED);
	}
/*	g_timeout_add(250, initPlayback_timeout_callback, NULL);*/
}

```

On a sort of unrelated side note: I have tried putting the code of m_init() into a function for the videoDrawArea realize callback along with setting the gst_x_overlay_set_xwindow_id in there but for some reason, I just get a Gdk-Warning saying that it isn't a pixmap or window even though it should exist (I used g_signal_connect_after). If someone could help me with that too it would be greatly appreciated.

---

### Post by RJ8722 on 2008-03-07
Bumping to reflect code change.
The code doesn't throw any segfaults anymore. Now I just can't seem to get the actual width/height of the video. I don't even know if I'm looking in the right places for it.

---

### Post by wilsoniya on 2008-05-31
Howdy! I'm in the same boat (my head's about to explode).  I think it has something to do with querying the caps of the the sourcepad of your decoder element.  Check this: [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/section-caps-api.html]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/section-caps-api.html").

However, that tutorial is semi-worthless b/c i've found it rare that video size information is even present in the caps.  

-mike

---

### Post by Lau_of_DK on 2008-05-31
Boys, 

calm down, Heikaman will be here soon :)

/Lau

---

### Post by wilsoniya on 2008-05-31
Hi again.

I've come with better news. [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstvideo.html#gst-video-get-size]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-libs/html/gst-plugins-base-libs-gstvideo.html#gst-video-get-size"). Please note you'll need to install the headers for plugins-base (for me it was libgstreamer-plugins-base0.10-dev).

Also, it's not overly straight forward when to call this function. It must be called after your pipeline is initialized to some degree.  I don't yet know a good way to find the appropriate time to call the function.

-mike

---

