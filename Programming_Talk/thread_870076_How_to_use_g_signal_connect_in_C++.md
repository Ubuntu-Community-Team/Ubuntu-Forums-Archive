---
title: "How to use g_signal_connect in C++?"
date: 2008-07-25
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-07-25
I am experimenting with GTKmm and Gstreamer. GTKmm uses C++ and Gstreamer C(the C++ bindings aren't complete). The docs of gstreamer use "g_signal_connect" to connect a signal to a callback emmitted by a plugin. My problem is that I cannot use g_signal_connect to call a member function of a class. I know that I need to do something hackish but I am stuck right now. Plz help me!!!

---

### Post by dribeas on 2008-07-25
> **SledgeHammer_999 said:**
> I know that I need to do something hackish but I am stuck right now. Plz help me!!!

As a general rule, to call a function that takes a function pointer, you will need to provide either a free function or an static method.
```

void test( void (*)(void) );

void callback1();
class X
{
   static void callback2();
};

// user code:
{
   test( &callback1 );
   test( &X::callback2 );
}

```

Of course, that is not too object-oriented. From the little I have read from GTKmm the function pointer passed does not necessarily have to be void (*)(void)... check the docs from the filter.

---

### Post by SledgeHammer_999 on 2008-07-25
I don't see where you use **g_signal_connect()**. But your code gave me an idea. The original signal/callback from this [doc](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-helloworld.html#section-helloworld) was:
[php]//callback
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

//signal-connect
g_signal_connect (demuxer, "pad-added", G_CALLBACK (on_pad_added), decoder);
[/php]

Now what I did:
class.h
[php]
class Myclass
{
//code goes here
 public:
     //my 2nd callback - it needs to be public
     void on_new_pad(GstPad *pad);
 private:
     GstElement *demux;
};
[/php]

gst_callbacks.h
[php]
#include "class.h"
// my 1st callback
void new_pad (GstElement *element, GstPad *pad, Myclass *data);
[/php]

class.cpp
[php]
#include "gst_callbacks.h"
Myclass::Myclass()
{
//connect to the 1st callback
g_signal_connect (demux, "pad-added", G_CALLBACK (new_pad), this);
}

void Myclass::on_new_pad(GstPad *pad)
{
//your code goes here
}
[/php]

gst_callbacks.cpp
[php]
void new_pad (GstElement *element, GstPad *pad, Myclass *data)
{
    //call your 2nd callback
    data->on_new_pad(pad);
}
[/php]

EDIT: My question is, do I have to use "static void" for my callback? Right now, I use just "void" because g++ gives an error.

---

### Post by dribeas on 2008-07-25
> **SledgeHammer_999 said:**
> EDIT: My question is, do I have to use "static void" for my callback? Right now, I use just "void" because g++ gives an error.

No, with the code you gave you don't need it to be static. My point before, which was not clear enough, I guess is that the third argument to g_signal_connect must be either a free function (as in your case) or a static method. That is, you could have done the same with a static method:

```

class Myclass
{
//code goes here
 public:
     //my 2nd callback - it needs to be public
     void on_new_pad(GstPad *pad);

     static void on_new_pad_callback( GstPad *pad, Myclass *data );
 private:
     GstElement *demux;
};  
// ...
void MyClass::on_new_pad_callback( GstPad *pad, Myclass *data )
{
    data->on_new_pad( pad );
}
// ...
g_signal_connect (demuxer, "pad-added", G_CALLBACK(MyClass::on_new_pad_callback), decoder);
```

In which case your second step callback does not need to be public anymore. (You could also make the free function callback a friend of your class)

---

### Post by SledgeHammer_999 on 2008-07-25
OMG THANK YOU. At first I was trying to do something similar to you but I was getting an error "cannot produce static linkage". The problem?-->
Instead of ```
void MyClass::on_new_pad_callback( GstPad *pad, Myclass *data )
{
    data->on_new_pad( pad );
}

```

I was doing: ```
static void MyClass::on_new_pad_callback( GstPad *pad, Myclass *data )
{
    data->on_new_pad( pad );
}

```

I didn't know I only had to use "static" in the prototype of the function. Again thank you. Reverting to your solution now!!!


EDIT: Also none of these callbacks needs to be public!!!

---

### Post by rakeshman on 2011-08-26
Hi
 
I followed the same, but am not successful.
 
class and function defs are same and signal connect calls are as follows. But none of them is working. control ot entering into the function onNewBufferCallback.
 
g-signal-connect(appsink,"new-buffer",MyClass::onNewBufferCallback,this)
 
g-signal-connect(appsink,"new-buffer",G_CALLBACK(MyClass::onNewBufferCallback),this)
 
g-signal-connect(appsink,"new-buffer",MyClass::onNewBufferCallback,NULL)
 
g-signal-connect(appsink,"new-buffer",G_CALLBACK(MyClass::onNewBufferCallback),this)
 
Pls help in this issue.

---

### Post by SledgeHammer_999 on 2011-08-26
Could you post more code? Do you run a glib mainloop?

---

