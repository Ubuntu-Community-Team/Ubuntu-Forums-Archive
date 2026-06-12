---
title: "how to make a firefox PLUGIN not EXTENSION??"
date: 2007-09-11
forum: Programming Talk
---

### Post by the_darkside_986 on 2007-09-11
Does anyone know how to make a firefox plugin, as opposed to a mere extension that is limited to the firefox api? 

This is only what I have found out: plugins rely on a shared library file, a *.so file in linux. These files are usually located in /usr/lib/firefox/plugins/ or at least a link to them is in there. I assume that these files contain a set of C/C++ functions that are called by the plugin. But what I do not understand is how they are integrated with firefox or where to get started.

I do have some experience with Lua and C/C++ integration, X11 and openGL, and I know how to find an firefox extension tutorial. (They always appear instead of the plugin writing tutorial I search for.)

My vision is a 100% GPL'd virtual machine web applet system that will compete with existing non-free technologies such as Flash, Java, etc. instead of trying to hopelessly clone them. This system's applets would be written with the Lua scripting language, be accelerated with the combination of Xlib and openGL, and developed primarily for Unix-like platforms. :guitar:

If there is already an existing technology such as this then I can't find it but would be interested in learning about it. 

Any links or resources would be helpful. Thanks.

---

### Post by Fbot1 on 2007-09-11
Seems like a waste of time. Anyway:
[http://developer.mozilla.org/en/docs/Gecko_Plugin_API_Reference:Plug-in_Basics](http://developer.mozilla.org/en/docs/Gecko_Plugin_API_Reference:Plug-in_Basics)

---

### Post by pmasiar on 2007-09-11
> **the_darkside_986 said:**
> Does anyone know how to make a firefox plugin, as opposed to a mere extension that is limited to the firefox api? 

I am not sure how you expect something to run as FF plugin and at the same time circumvent FF API. And I am not sure I would want something like that running on my desktop either - in fact, I am sure I would NOT want it :-)

> My vision is a 100% GPL'd virtual machine web applet system that will compete with existing non-free technologies such as Flash, Java, etc. instead of trying to hopelessly clone them. 

So you want to beat MSFT, Sun and Adobe in game where they have 10 years head start and lots of money? Good luck!

---

### Post by Fbot1 on 2007-09-11
> **pmasiar said:**
> I am not sure how you expect something to run as FF plugin and at the same time circumvent FF API.

Actually, that's kinda the point of plug-ins.

---

### Post by pmasiar on 2007-09-11
Fine, but how?

---

### Post by the_darkside_986 on 2007-09-11
I made my first extension today. It just makes the status bar say "My First FF Extension" but most of it is copy and paste from a tutorial. I am also studying the gecko plugin API, and whatever else I can find.

I've always wanted to experiment with virtual machine script technology, and I find projects such as Java, Flash, etc. to be very interesting. But of course, they are non-free and it bothers me to have to use them. I do still have confidence in gnash. But I can't use it all the time yet. And I'm not trying to build a compatible replacement to the non-free technology.

This plugin, since it will be based on Lua, could be described as an in-browser Lua script player. Lua is a lightweight, expandable, open-source scripting language that integrates well with real languages such as C/C++. Lua by itself doesn't do much except standard c library functions, so Lua's true power comes in its ability to be expanded. Bindings for popular C libs such as openGL can easily be added to Lua. Programs using lualibs can either run lua plain-text scripts OR lua programs compiled into the lua virtual machine language.

The libraries that will be accessed by this plugin's api implementation would be openGL, networking functions, I/O, and whatever I can think of. The plugin script writer would not need to call binded openGL functions, for example, but there would be wrappers around those low-level C functions, and those would be called so that drawing an image or catching a keystroke would take only a few lines of Lua. 

This will not be a nasty mess that lives on the desktop and wastes time and memory. It will be an in-browser plugin that is loaded only as necessary. A stand-alone modded Lua player is easy to make though.

Adding openGL and other libs to Lua is nothing new under the sun, but I thought it would be a unique idea to make a browser plugin for it.

---

### Post by kavithabangera on 2008-11-20
Do you have any idea about adding browser plugin to an opengl based player ..?
I wanted to know how to write and install plugins... and how to send pointers to opengl....?
any good tutorial?

---

