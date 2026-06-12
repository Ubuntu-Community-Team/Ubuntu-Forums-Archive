---
title: "Gstreamermm example"
date: 2010-06-12
forum: Programming Talk
---

### Post by INeedAUserID on 2010-06-12
I am trying to write a very, very simple command line music player (just to see if I can) with Gstreamermm. I really can not find a single example anywhere on the internet to help me. I am in the early stages of learning C++ when I decided to try this (yes I do realize it is way over my head and that I should just stick to simple stuff for now to learn, but I felt like trying something new).

---

### Post by SledgeHammer_999 on 2010-06-12
Just read the Gstreamer [guide](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html) and use the C++ equivalents instead of the C functions.

The gstreamermm online documentation is here->[http://library.gnome.org/devel/gstreamermm/unstable/](http://library.gnome.org/devel/gstreamermm/unstable/)

---

### Post by INeedAUserID on 2010-06-12
I need an equivalent for 

g_main_loop_run (loop);

---

### Post by SledgeHammer_999 on 2010-06-12
Are you using Gtkmm? If yes, then Gtk::Main::run() will take care of that. Otherwise you can use "g_main_loop_run (loop);" directly. It is a glib function.

---

### Post by INeedAUserID on 2010-06-12
I need gtkmm?

Edit: 
Nevermind, I made it work with g_main_loop_run (loop);

Edit 2:
I wanted to get the first edit in before I forced you to pointlessly respond to my idiocy. Thank you for all the help. This probably should have been obvious to me, but I really am dumb sometimes. Thank you, you saved me a lot of frustration.

---

### Post by SledgeHammer_999 on 2010-06-12
No you don't. But if you want to make a gui application gtkmm is a CHOICE.
Since gstreamer is based on glibmm then you can use [Glib::MainLoop](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1MainLoop.html) to create the loop and run it. Something like this:

```

#include <glibmm/main.h>

Glib::RefPtr<Glib::MainLoop> loop = Glib::MainLoop::create();

//set up gstreamer stuff here

loop->run();

```

---

### Post by INeedAUserID on 2010-06-12
> **SledgeHammer_999 said:**
> No you don't. But if you want to make a gui application gtkmm is a CHOICE.
Since gstreamer is based on glibmm then you can use [Glib::MainLoop](http://library.gnome.org/devel/glibmm/unstable/classGlib_1_1MainLoop.html) to create the loop and run it. Something like this:

```

#include <glibmm/main.h>

Glib::RefPtr<Glib::MainLoop> loop = Glib::MainLoop::create();

//set up gstreamer stuff here

loop->run();

```
Wow, that is another very interesting choice. Thank you and sorry for my idiocy once again. I'll have to try that.
Edit: Yes, that works wonderfully and looks nicer (to me) than the g_main_loop_run way of doing it.

---

### Post by INeedAUserID on 2010-06-12
One more question, how do I make it exit when the song finishes?

---

### Post by SledgeHammer_999 on 2010-06-12
As the [gstreamer hello world example](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-helloworld.html#section-helloworld) shows, you should listen for the **GST_MESSAGE_EOS** in the bus and then do a loop->quit();

---

### Post by INeedAUserID on 2010-06-13
> **SledgeHammer_999 said:**
> As the [gstreamer hello world example](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-helloworld.html#section-helloworld) shows, you should listen for the **GST_MESSAGE_EOS** in the bus and then do a loop->quit();

Since you didn't explain very well and the example does not help me too much, I tried to use:
bus->pop(Gst::MessageEos)
But, that gave me an error at compile time (error: expected primary-expression before &#8216;)&#8217; token), and I can not figure out why.Can you help?

Edit: I realized that this approach will not work even if I do get it to, can you help translate the example to c++?

---

### Post by SledgeHammer_999 on 2010-06-13
For this, it is kind of hard for me to give sample code without re-writing the whole example. Could you be kind enough to post your code so far so I can modify it? (I am too lazy to re-write the C hello world on my own).

---

### Post by INeedAUserID on 2010-06-13
> **SledgeHammer_999 said:**
> For this, it is kind of hard for me to give sample code without re-writing the whole example. Could you be kind enough to post your code so far so I can modify it? (I am too lazy to re-write the C hello world on my own).

Well, my code is really bad and does not really follow the tut at all. :oops:
I can post it anyway, though. I'll now get to work rewriting the tut code as best I can.

[PHP]#include <gstreamermm.h>
#include <glibmm/main.h>
#include "boost/filesystem.hpp"
#include <iostream>

Glib::RefPtr<Glib::MainLoop> loop;

int main(int argc, char* argv[]) {
    Gst::init();
    loop = Glib::MainLoop::create();
    Glib::RefPtr<Gst::PlayBin2> playbin = Gst::PlayBin2::create();
    Glib::ustring path = boost::filesystem::initial_path().string();
    Glib::ustring songName = argv[1];
    songName = "file://" + path + "/" + songName; 
    playbin->set_property("uri",songName);
    playbin->set_state(Gst::STATE_PLAYING);
    loop->run();
    std::cout<<"done\n";
    playbin->set_state(Gst::STATE_NULL);

}
[/PHP]

Edit: Okay, my horribly done version of the one you linked to. There were several parts I had no idea what to do on and it won't come close to compiling, but I am too tired and unskilled to fix them.

[PHP]

#include <gstreamermm.h>
#include <glibmm/main.h>
#include <iostream>

static bool bus_call(GstBus *bus, GstMessage *msg, gpointer data)
{
Glib::RefPtr<Glib::MainLoop>* loop = (Glib::RefPtr<Glib::MainLoop>*) data; 
switch (GST_MESSAGE_TYPE (msg)) { //I have no idea what to do with the switch
    case GST_MESSAGE_EOS:
        std::cout << "End of stream\n"; //they use g_print, but I am trying to translate
        loop->quit();
        break;

    case GST_MESSAGE_ERROR: { //most of this code I really don't understand
        gchar *debug;
        GError *error;

        gst_message_parse_error (msg, &error, &debug);
        g_free (debug);

        std:cerr << "Error: " + error->message + std::endl;
        g_error_free (error);

        loop -> quit();
        break;
    }
    default:
        break;
}
return true;
}

static void on_pad_added (Gst::Element *element, Gst::Pad *pad, gpointer data)
{
    Gst::Pad *sinkpad;
    Gst::Element *decoder = (Gst::Element*) data;
    std::cout << "Dynamic pad created, linking demuxer/decoder\n";
    sinkpad = Gst::ElementFactory::get_static_pad_templates(decoder, "sink"); //this is not even close to right, but I am not at all sure what goes here
    pad -> link(sinkpad);
    //Can not find unref in gstreamermm, I am putting my best guess as to how to get this to work
    gst_object_unref (sinkpad.gobj());
}
    
int main (int argc, char *argv[])
{
    Glib::RefPtr<Glib::MainLoop>* loop;
    Glib::RefPtr<Gst::Element> *pipeline, *source, *demuxer, *decoder, *conv, *sink;
    Gst::Bus *bus;
    Gst::init();
    loop = Glib::MainLoop::create();
    if (argc !=2) {
        std::cerr << "Usage: " + argv[0] + "<Ogg/Vorbis filename>\n";
        return -1;
    }

    pipeline = Gst::Pipeline::create("audio-player");
    source = Gst::FileSrc::Create(); 
    demuxer = Gst::OggDeumux::create(); //best I could come up with
    decoder = Gst::VorbisDec::create(); //best I could come up with
    conv = Gst::AudioConvert::create();
    sink = Gst::AlsaSink::create(); //I was going to use AudioSink, but could not figure out how
    
     if (!pipeline || !source || !demuxer || !decoder || !conv || !sink) {
        std::cerr <<"One element could not be created. Exiting.\n";
        return -1;
     }

     source->set_property_location(argv[1]);
     bus = pipeline->get_bus();
     bus->add_watch(bus_call, loop);
     //Can not find unref in gstreamermm, I am putting my best guess as to how to get this to work
     gst_object_unref (bus.gobj());
     
     //These are probably not right
     pipeline.add(source);
     pipeline.add(demuxer);
     pipeline.add(decoder);
     pipeline.add(conv);
     pipeline.add(sink);
     
     //These are also probably not right
     source.link(demuxer);
     demuxer.link(decoder);
     decoder.link(conv);
     conv.link(sink);
     //This needs fixed:
     g_signal_connect (demuxer, "pad-added", G_CALLBACK (on_pad_added), decoder);
     //It won't work at all, way over my head
     
     std::cout << "Now Playing" << std::endl;
     pipeline->set_state(Gst::STATE_PLAYING);

     std::cout << "Running" << std::endl;
     loop->run();
     std::cout << "Stopping Playback" << std::endl;
     pipeline->set_state(Gst::STATE_NULL);
     //Once again, the unref thing
     gst_object_unref (pipeling.gobj());

     return 0;
}
[/PHP]

---

### Post by SledgeHammer_999 on 2010-06-15
You should read the whole Guide not only the hello world example. You forgot to add a watch to the pipeline bus in your code. This is one way to do it:

[php]
#include <gstreamermm.h>
#include <glibmm/main.h>
#include <iostream>

bool on_bus_callback(const Glib::RefPtr<Gst::Bus> &bus, const Glib::RefPtr<Gst::Message> &message, Glib::RefPtr<Glib::MainLoop> &loop)
{
    //I am not sure if it should be Glib::RefPtr<Glib::MainLoop> &loop
    //or Glib::RefPtr<Glib::MainLoop> loop. It works though
    switch(message->get_message_type())
    {
        case Gst::MESSAGE_EOS:
            loop->quit();
            break;        
    }
            
    return true;
}

int main(int argc, char* argv[]) {
    Gst::init();    
    Glib::RefPtr<Glib::MainLoop> loop = Glib::MainLoop::create();
    Glib::RefPtr<Gst::PlayBin2> playbin = Gst::PlayBin2::create();
    Glib::ustring path = Glib::get_current_dir();
    Glib::ustring songName = argv[1];
    songName = "file://" + path + "/" + songName; 
    playbin->set_property("uri",songName);
    
    //get the bus
    Glib::RefPtr<Gst::Bus> bus = playbin->get_bus();        
    //Add a bus watch. Bind to the slot the loop variable so you don't
    //have to declare it as global.    
    bus->add_watch(sigc::bind(sigc::ptr_fun(&on_bus_callback), loop));
    playbin->set_state(Gst::STATE_PLAYING);
    loop->run(); //execution blocks here until loop->quit() is called
    //loop->quit() has been called.
    std::cout<<"done\n";
    playbin->set_state(Gst::STATE_NULL);
    return 0;
}[/php]

I think I've documented the code enough. I got rid of the boost call and made some other changes. It compiles and works on my machine as expected. If you have more questions, just ask.

ps: compile with > g++ -o "untitled" "untitled.cpp" `pkg-config  gstreamermm-0.10 glibmm-2.4 --libs --cflags`

---

### Post by INeedAUserID on 2010-06-26
> **SledgeHammer_999 said:**
> You should read the whole Guide not only the hello world example. You forgot to add a watch to the pipeline bus in your code. This is one way to do it:

[php]
#include <gstreamermm.h>
#include <glibmm/main.h>
#include <iostream>

bool on_bus_callback(const Glib::RefPtr<Gst::Bus> &bus, const Glib::RefPtr<Gst::Message> &message, Glib::RefPtr<Glib::MainLoop> &loop)
{
    //I am not sure if it should be Glib::RefPtr<Glib::MainLoop> &loop
    //or Glib::RefPtr<Glib::MainLoop> loop. It works though
    switch(message->get_message_type())
    {
        case Gst::MESSAGE_EOS:
            loop->quit();
            break;        
    }
            
    return true;
}

int main(int argc, char* argv[]) {
    Gst::init();    
    Glib::RefPtr<Glib::MainLoop> loop = Glib::MainLoop::create();
    Glib::RefPtr<Gst::PlayBin2> playbin = Gst::PlayBin2::create();
    Glib::ustring path = Glib::get_current_dir();
    Glib::ustring songName = argv[1];
    songName = "file://" + path + "/" + songName; 
    playbin->set_property("uri",songName);
    
    //get the bus
    Glib::RefPtr<Gst::Bus> bus = playbin->get_bus();        
    //Add a bus watch. Bind to the slot the loop variable so you don't
    //have to declare it as global.    
    bus->add_watch(sigc::bind(sigc::ptr_fun(&on_bus_callback), loop)); 
    playbin->set_state(Gst::STATE_PLAYING);
    loop->run(); //execution blocks here until loop->quit() is called
    //loop->quit() has been called.
    std::cout<<"done\n";
    playbin->set_state(Gst::STATE_NULL);
    return 0;
}[/php]

I think I've documented the code enough. I got rid of the boost call and made some other changes. It compiles and works on my machine as expected. If you have more questions, just ask.

ps: compile with

Wow, thank you. You're right, I should have read the whole tutorial. I will now. Getting rid of the boost thing is great also, I really should have looked for a Glib solution. Thank you again.

Edit: one question, why does gstreamermm use Glib::RefPtr?

---

### Post by SledgeHammer_999 on 2010-06-27
Glib::RefPTr is a smart pointer. If you were to use the pure gobject system(on which both gtk and gstreamer rely) then you would have to *_ref()/*_unref() almost every pointer that gstreamer returns. The smart pointer approach makes it easier to do memory management. If you're not familiar with the gobject system, then you won't actually understand what I meant with ref()/unref().

Also gstreamer uses glib so gstreamermm uses glibmm(the C++ wrapper of glib) which contains the Glib::RefPtr.

---

### Post by INeedAUserID on 2010-06-27
> **SledgeHammer_999 said:**
> Glib::RefPTr is a smart pointer. If you were to use the pure gobject system(on which both gtk and gstreamer rely) then you would have to *_ref()/*_unref() almost every pointer that gstreamer returns. The smart pointer approach makes it easier to do memory management. If you're not familiar with the gobject system, then you won't actually understand what I meant with ref()/unref().

Also gstreamer uses glib so gstreamermm uses glibmm(the C++ wrapper of glib) which contains the Glib::RefPtr.

Oh, I figured it was pointer related (the Ptr part makes it a bit obvious). Thank you for the information, smart pointers must make a lot of things a lot easier.

Edit: I hope that does not sound mean or insulting. Rereading it, it almost seems like I was saying something similar to "duh", this was not the intent.

---

