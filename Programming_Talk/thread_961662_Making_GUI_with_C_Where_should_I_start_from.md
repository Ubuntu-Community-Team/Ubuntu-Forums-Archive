---
title: "Making GUI with C? Where should I start from?"
date: 2008-10-28
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-28
Ok I already know syntax and basic maths with C.

But I want to learn making GUI with GTK. I never really
touched GTK before, when I was programming in python.

And I ain't got an idea where to start from. I want a simple
GTK application/tutorial written in C to play around with.


Can't find any good tuts with google.

Or if you know better API for making GUI tell me.

I want just a window, I already know how to use OpenGL.
But OpenGL is useless without a window to draw on.

Or perhaps SDK is better? As much as I have heard, it can be
used for sounds and keyboard/mouse capturing.


*Just say a good API and tell me how to use it thanks.*

---

### Post by nvteighen on 2008-10-28
The GTK+ lib is a rather difficult one.

The best tutorial to start out with GTK+ is the official one: [http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)

But for such huge APIs that are almost impossible to master completely I recommend you to learn the basic concepts from the tutorial and then just refer to the API documentation for any doubt you have. 

But, to make your life easier, I highly recommend you to install the GTK+ docs from the repos (so you can work offline) and also the Devhelp browser, which allows you to browse and search the GTK+ API very easily. To do this, use:

```

sudo apt-get install libgtk2.0-doc devhelp

```

---

### Post by snova on 2008-10-28
There are probably plenty of GTK tutorials around, but as I don't know anything about that toolkit myself, I can't suggest anything except for looking around the homepage.

SDK? That's "Software Development Kit". Perhaps you meant SDL? It might be easier, and maybe not. Take a look at the examples and decide if they look too complicated.

Personally I use Qt, but that's just because it's the only one I know how to use. It's not for C, either.

---

### Post by crazyfuturamanoob on 2008-10-28
Yes, I mean SDL. By the way, what does it stand for?

---

### Post by snova on 2008-10-28
Simple DirectMedia Layer. I think it's kinda like DirectX in that it does quite a lot of useful things, but with the exception of graphics. It might go nicely in tandem with OpenGL.

I've never used it. It's on my infinite TODO list to try it out.

---

### Post by mike_g on 2008-10-28
I'd go with SDL instead as its very easy to setup a window. You can do it in about 10 lines of C code. And yes, SDL also does input handling and basic sound, which is a reason its often used with OGL.

For GUIs C is not a very suitable language you can effectively achieve the same thing in 1/10th of the time/code using PyGtk.

---

### Post by LaRoza on 2008-10-28
> **snova said:**
> Simple DirectMedia Layer. I think it's kinda like DirectX in that it does quite a lot of useful things, but with the exception of graphics. It might go nicely in tandem with OpenGL.


No, it isn't like DirectX, although I think DirectX does the things SDL can do.

SDL is just what its name says. It provides interfaces for various controls, media and images.

For 3d, OpenGL and the like would be used. SDL and OpenGL are often used together.

@OP My wiki has information on GTK, C, SDL and OpenGL.

---

### Post by LaRoza on 2008-10-28
> **mike_g said:**
> 
For GUIs C is not a I'd go with SDL instead as its very easy to setup a window. You can do it in about 10 lines of C code. And yes, SDL also does input handling and basic sound, which is a reason its often used with OGL.very suitable language you can effectively achieve the same thing in 1/10th of the time/code using PyGtk.

What about Glade? Can't its output be used in C (or any language that GTK supports)

---

### Post by snova on 2008-10-28
> **LaRoza said:**
> No, it isn't like DirectX, although I think DirectX does the things SDL can do.

SDL is just what its name says. It provides interfaces for various controls, media and images.

For 3d, OpenGL and the like would be used. SDL and OpenGL are often used together.

[quote=Wikipedia][FONT=Verdana]Simple DirectMedia Layer (SDL) is a cross-platform, free and open source software multimedia library written in C that presents a simple interface to various platforms' **graphics,**[/FONT]** sound, and input devices**[/quote]

Well, there is at least some overlap. DirectX also does networking, I think.

But since the OP made it clear he mostly just wanted a window to do OpenGL rendering to, I would also suggest trying SDL.

(Snowing! :biggrin:)

---

### Post by mike_g on 2008-10-28
> What about Glade? Can't its output be used in C (or any language that GTK supports) 
IMO glade is awful, although tbh I'm not to keen on any visual GUI designers really. I guess you could use it to set up a window, but to me using SDL would be simpler and neater. 

For more complex stuff I generally find the UI layout to be the easy bit. For example creating a treeview with a decent amount of functionality in C is a nightmare (although Gtk does it about as well as could be done in C), all Glade can really do is dump the container at a location and set a few variables. Plus, then theres 1000s lines of XML.

---

### Post by LaRoza on 2008-10-28
> **snova said:**
> 
(Snowing! :biggrin:)

Raining...

It snowed a little earlier, then proceeded to rain for hours (and hours more, if the report was accurate).

Cold, slippery, and icy.

---

### Post by crazyfuturamanoob on 2008-10-29
Tried SDL with NeHe tutorials. Looks good.

---

### Post by orphean on 2008-10-29
> **mike_g said:**
> IMO glade is awful, although tbh I'm not to keen on any visual GUI designers really. I guess you could use it to set up a window, but to me using SDL would be simpler and neater. 

For more complex stuff I generally find the UI layout to be the easy bit. For example creating a treeview with a decent amount of functionality in C is a nightmare (although Gtk does it about as well as could be done in C), all Glade can really do is dump the container at a location and set a few variables. Plus, then theres 1000s lines of XML.

I'd agree with you if you're talking about glade2.  Glade3 however is quite nice.  Also, libglade (the library that slurps in the xml to create the gui) is a separate thing from the glade program.

Furthermore, libglade is essentially deprecated at this point since in Gtk 2.14 we now have GtkBuilder which is a much nicer api for dealing with this stuff.  Glade3 in svn trunk writes directly to the GtkBuilder schema but there's also a conversion program for this transition period to convert glade files to gtkbuilder files.

Don't be too quick to dismiss it since pretty much every Gnome program uses it :)

---

