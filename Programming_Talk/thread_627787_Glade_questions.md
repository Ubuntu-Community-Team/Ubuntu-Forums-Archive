---
title: "Glade questions"
date: 2007-11-30
forum: Programming Talk
---

### Post by mdpalow on 2007-11-30
Hi Everyone,

Just some basic questions.

I wrote a shell script that does a lot of nice things for me when I need to use it.

I enjoyed writing it, but now want to take my fun to a higher level and make it a GUI.

I installed Glade and like it, but don't fully understand the process, which I need to do in order to get started.

Glade is an interface designer, which builds the GUI, but that's it - right? Then you have to tie the GUI in with the code that will run when you click on a button for example?

1st Question:

I saw a youtube video that showed the person using Ruby. Is that what I need to install also or is there maybe another package that will work and maybe preferred by you guys/gals. Basically, can you tell me what I need to install to start looking at this project and learning more? Can you also provide version numbers, so I know which one to install with Synaptic?

2nd Question:

If my shell script does everything I want, will the GUI work using code from that script or will it have to be written differently in another language? I just want to use this on my Ubuntu 7.10.

3rd Question:

Having a hard time finding any good reference material on Glade. Does anyone know a link that provides good documentation and maybe even some examples?

I have a few more questions, but I can't think of them right now.

Thanks in advance for any help...

P.S. Please keep in mind I have no programming experience in any language other than what I've done in my script, which is pretty lengthy, but simplistic compared to what many of you do.

P.P.S. Also keep in mind this is a learning project for me to enjoy learning more about my Ubuntu system and how to make it do more of what I like. No professional coder set-up recommendations please. :) Just something simple to get started with at this time. 

Thanks again...

---

### Post by MicahCarrick on 2007-11-30
> I saw a youtube video that showed the person using Ruby. Is that what I need to install also or is there maybe another package that will work and maybe preferred by you guys/gals. Basically, can you tell me what I need to install to start looking at this project and learning more? Can you also provide version numbers, so I know which one to install with Synaptic?

Glade generates an XML file which can be parsed using any library to generate a GTK+ interface. You could use Ruby, Python, PHP, C, C++, and the list goes on. If you're new to programming, Python might be easier. If you want to try C, then you could check out my tutorial: [Tutorial: Simple Gnome Application Using libglade and C/GTK+]("http://www.micahcarrick.com/03-02-2006/gnome-programming-tutorial.html"). I also have a new tutorial which is more thorough and uses Glade3 coming out soon.

Regardless of the language you choose, you can get help with GTK+ on the mailing lists or at [GTK+ Forums]("http://gtkforums.com")

> If my shell script does everything I want, will the GUI work using code from that script or will it have to be written differently in another language? I just want to use this on my Ubuntu 7.10.

If this is just for your own personal use, you can just create a GUI which has a button which when clicked calls your script and shows the output in a text view widget (GtkTextView). The C function you might use is g_spawn_sync() to do this (you'll have to check the GLib reference manual of the language you choose to use).

> Having a hard time finding any good reference material on Glade. Does anyone know a link that provides good documentation and maybe even some examples?

The link I posted above shows using Glade2. As I mentioned, I have a good tutorial in the works now (the glade portion is actually done, just not posted), so if you want to shoot me an email (email at micahcarrick dot com) then I'll let you know when it's posted.

Also, in the examples section of GTK+ Forums is a post called "simple libglade hello world" or something like that. There's a few other examples too.

---

### Post by MicahCarrick on 2007-11-30
I decided that it's pretty common for people to want to run a command from within their application. I posted a little example project which takes a command from a GtkEntry and puts the output into a GtkTextView.

The interface is a glade file and the application is written in C.

_[Execute command into a GtkTextView]("http://www.gtkforums.com/about906.html")_

---

