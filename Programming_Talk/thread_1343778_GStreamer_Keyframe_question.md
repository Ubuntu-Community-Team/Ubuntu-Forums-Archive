---
title: "GStreamer Keyframe question"
date: 2009-12-02
forum: Programming Talk
---

### Post by wanting2learn on 2009-12-02
I m trying to detect keyframes in a buffer.  From the following link:
[http://old.nabble.com/keyframes-from-a-video-td24641321.html](http://old.nabble.com/keyframes-from-a-video-td24641321.html)

it says to use the following code:
 ```
if(!buffer->flag_is_set(Gst::BUFFER_FLAG_DELTA_UNIT)) 
     { 
         // it's a keyframe 
     } 
```I am using the following bit of code in my application like so:

```
static void onVideoHandoff( GstElement *object, GstBuffer *buffer,
                            gpointer user_data )
{

     if(!buffer->flag_is_set(Gst::BUFFER_FLAG_DELTA_UNIT)) 
     { 
         // it's a keyframe 
     } 

//blah blah

}
```
I get the error:
error: ‘struct _GstBuffer’ has no member named ‘flag_is_set’

Does anyone know what I am doing wrong??

Thanks

---

### Post by Zugzwang on 2009-12-02
> **wanting2learn said:**
> 
I get the error:
error: &#8216;struct _GstBuffer&#8217; has no member named &#8216;flag_is_set&#8217;

Does anyone know what I am doing wrong??

Thanks

The post you refer to is from august. Maybe the library version of your Ubuntu is older and doesn't yet have this function? Even if you use karmic, the function may not have made it into Ubuntu's version yet. Download the latest source code of the library, extract it somewhere (e.g. to /tmp) and search for the definition of "_GstBuffer". See if it contains this function. Then compare that piece of code to the library version you have installed. Is it different wrt. to "flag_is_set"?

---

### Post by SledgeHammer_999 on 2009-12-02
The post you are linking to most likely uses gstreamermm(C++ bindings), but I suppose you use the C API. So try this instead:
```

 if(!GST_BUFFER_FLAG_IS_SET(buffer, GST_BUFFER_FLAG_DELTA_UNIT))
     { 
         // it's a keyframe 
     } 


```

doc [link](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gstreamer/html/gstreamer-GstBuffer.html#GST-BUFFER-FLAG-IS-SET--CAPS)

---

### Post by wanting2learn on 2009-12-02
I have done the following which seems to work.

  ```
GstBufferFlag flag;
  flag = GST_BUFFER_FLAG_DELTA_UNIT;

  if( !GST_BUFFER_FLAG_IS_SET(buffer, flag ))
  //if(!buffer->flag_is_set(Gst::BUFFER_FLAG_DELTA_UNIT))
  {
      fprintf( stderr, "DEBUG:onVideoHandoff - **********KEYFRAME**********\n");
      //This is a keyframe
  }
  else
  {
      fprintf( stderr, "DEBUG:onVideoHandoff - DELTAFRAME\n");
  }
```


I am getting 28 delta frames for every keyframe.  Does this mean the GOP for the stream is 28?? )


Thanks for your help.

---

### Post by SledgeHammer_999 on 2009-12-02
Your welcome.
Unfortunately I don't know nothing about video/audio terminology/encoding...

---

