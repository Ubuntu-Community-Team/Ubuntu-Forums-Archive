---
title: "Any gstreamer 1.0 tutorial?"
date: 2012-12-05
forum: Programming Talk
---

### Post by bird1500 on 2012-12-05
Hi,
Are there any gst 1.0 tutorials?

All I found are 0.10 [tutorials]("http://docs.gstreamer.com/display/GstSDK/Playback+tutorial+1%3A+Playbin2+usage").

I installed gst 1.0.3 thru a PPA but can't get it to work, simple code that compiles for gst1.0 fails to run with:
> 
(basic:448: GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(basic:448: GStreamer-CRITICAL **: gst_element_get_bus: assertion `GST_IS_ELEMENT (element)' failed

(basic:448: GStreamer-CRITICAL **: gst_bus_timed_pop_filtered: assertion `GST_IS_BUS (bus)' failed

(basic:448: GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

(basic:448: GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(basic:448: GStreamer-CRITICAL **: gst_object_unref: assertion `object != NULL' failed

The official gst1.0 manuals don't give working examples.

---

