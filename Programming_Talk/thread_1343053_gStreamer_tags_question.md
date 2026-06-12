---
title: "gStreamer tags question"
date: 2009-12-01
forum: Programming Talk
---

### Post by wanting2learn on 2009-12-01
Hi,
I am investigating gStreamer and I have a few issues.

I have to obtain the bitrate and GOP of a video stream.  I read in gStreamer manual that i have to listen for a GST_MESSAGE_TAG message.  Well I have got code to do this but I never seem to get one of these messages.

Does that mean the video stream does not contain any tags???

I'm new to gStreamer but not to video or c++.


Thanks

---

### Post by Vadi on 2009-12-01
I guess so. Might also want to check your implementation against others just to be sure you've done it right: [http://www.google.com/codesearch?q=lang:c%2B%2B+GST_MESSAGE_TAG+&hl=en&btnG=Search+Code](http://www.google.com/codesearch?q=lang:c%2B%2B+GST_MESSAGE_TAG+&hl=en&btnG=Search+Code)

---

### Post by SledgeHammer_999 on 2009-12-01
Maybe the file doesn't have tags or the used demuxer doesn't emit them. 
But for the bitrate, you should check the caps of the pads of each element on your pipeline, because I don't think tag message is emitted for that. To do that you need to study a little bit the gobject system.

If you need more help just ask.

By the way what kind of file do you test?

---

### Post by wanting2learn on 2009-12-02
> re: By the way what kind of file do you test?

The video is a stream coming from a video camera and not a file as such.

I may have more questions shortly.

Thanks

---

### Post by wanting2learn on 2009-12-02
> re: But for the bitrate, you should check the caps of the pads of each element on your pipeline,

I have did the following:

> GstCaps *caps = gst_buffer_get_caps(buffer);
const GstStructure *str = gst_caps_get_structure( caps, 0 );
gst_structure_get_int (str, "rate", &rate);
fprintf( stderr, "DEBUG:buffer rate = %i\n",rate);

The values I am gettign for bitrate are 130396 a nd then i ran it again it gave me 4972220.  Is this correct?  This does not seem right for the bitrate.

Am I doing this right?  

Thanks

---

### Post by SledgeHammer_999 on 2009-12-02
Are you sure there is "rate" in that GstStructure?
Also I hope you initialize rate. Something like "**gint rate = 0;**"

---

### Post by wanting2learn on 2009-12-03
I initialized it to 0 and its now 0 all the time.

Probably like you say this is not supported in this structure.  Do you know how I would go about getting the bitrate??

Many thanks.

---

### Post by SledgeHammer_999 on 2009-12-03
Probably some caps in some pad has a structure name "bitrate". Anyways, test all caps's gstructure with this(prints all available fields):

```

gint fields = 0;
fields = gst_structure_n_fields(str);
for (unsigned int i = 0; i < fields; i++)
{
  g_print("%s\n", gst_structure_nth_field_name(str,i));
}

```

This way you may find a relevant field that suits you.
Just try all the caps of all the pads of each element in your pipeline.

---

