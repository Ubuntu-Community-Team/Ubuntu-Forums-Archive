---
title: "Transition to gstreamer 1.0"
date: 2012-12-17
forum: Programming Talk
---

### Post by bird1500 on 2012-12-17
Hi,
Version 0.10 works fine, but 1.0 yields this:
>  GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failedat the second line:
[PHP]
GstElement *refPlay = gst_element_factory_make("playbin", NULL);
GstBus *bus = gst_pipeline_get_bus(GST_PIPELINE(refPlay)); //THIS LINE
[/PHP]Anyone knows what's wrong and why refPlay (GstElement*) isn't a pipeline anymore in gstreamer 1.0?

---

### Post by SledgeHammer_999 on 2012-12-17
Does **GST_IS_ELEMENT(refPlay)** return false or **GST_IS_ELEMENT(GST_PIPELINE(refPlay))**?

---

### Post by bird1500 on 2012-12-17
It turns out the first line returns NULL. I'm not sure why.

Before this I do:

guint major, minor, micro, nano;
gst_version(&major, &minor, &micro, &nano);
printf("Using gstreamer v.%d.%d.%d.%d\n", major, minor, micro, nano);

and get "Using gstreamer v.1.0.3.0". So I'm certainly using v1.0 version and it probably works/is installed fine.

Looks like for some reason neither playbin nor playbin2 work in gstreamer 1.0


EDIT: [this solves it]("http://lists.freedesktop.org/archives/gstreamer-devel/2012-December/038468.html")

---

### Post by SledgeHammer_999 on 2012-12-17
Nice. Happy coding then.

---

