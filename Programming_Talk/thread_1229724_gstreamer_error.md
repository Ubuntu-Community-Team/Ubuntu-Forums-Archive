---
title: "gstreamer error"
date: 2009-08-02
forum: Programming Talk
---

### Post by swappo1 on 2009-08-02
Hello,

I am having a problem with the following function:
```
static gboolean update_time_callback(GstElement *pipeline)
{
	GstFormat fmt = GST_FORMAT_TIME;
	gint64 position;
	gint64 length;
	gchar time_buffer[25];
	
	if(gst_element_query_position(pipeline, &fmt, &position) 
	   && gst_element_query_duration(pipeline, &fmt, &length))
	{
		g_snprintf(time_buffer, 24,
		   "%u:%02u.%02u", GST_TIME_ARGS(position));
		gui_update_time(time_buffer, position, length);
	}
	
	return TRUE;
}
```
I am getting an error stating there are too many arguments for format for the g_snprintf statement.  Any ideas?

---

### Post by dwhitney67 on 2009-08-02
How is the GST_TIME_ARGS macro defined?

Your usage of g_snprintf() seems ok, at least according to this [API site]("http://library.gnome.org/devel/glib/stable/glib-String-Utility-Functions.html#g-snprintf").

-------------

EDIT:

I just found the definition for GST_TIME_ARGS().  Apparently it formats the given arg to be used with GST_TIME_FORMAT, which is defined as "u:%02u:%02u.%09u".

---

### Post by swappo1 on 2009-08-02
> I just found the definition for GST_TIME_ARGS(). Apparently it formats the given arg to be used with GST_TIME_FORMAT, which is defined as "u:%02u:%02u.%09u".
Thanks, that clears it up.  I looked at GST_TIME_FORMAT and didn't even see it.

---

