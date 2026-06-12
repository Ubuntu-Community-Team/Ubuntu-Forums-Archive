---
title: "Writing Gnome Panel Applets"
date: 2004-11-29
forum: Programming Talk
---

### Post by Enygma on 2004-11-29
Hey, 

I've been messing about with Mono and C# lately, I really like what I'm seeing. 
It's quite nice to develop in and you can see results very quickly. 
I'd now like to write a Gnome Panel Applet so that I can be notified every time someone adds a message to my website.  (It's just a chatterbox, I'll just check a file on the server every few minutes)

Does anyone know how to write a Panel Applet in C#, or maybe even in C, I should be able to use P/Invoke to write a wrapper.

Thanks

Peter

---

### Post by nehalem on 2004-11-29
You cannot yet write applets in C# and mono, that's one of the last areas where the bindings are not complete.  I would think this will happen when they relese the next upgrade with GTK#, etc.  But we'll just have to wait and see.

The best option may be C but I've never actually attempted it and am not that up-to-date when it comes to C (never used Python).

---

### Post by Daniel G. Taylor on 2004-11-29
I'd say go with Python if you've used it before; in my opinion it's much easier than the C equivalent, not to mention that the Ubuntu devs will love you forever. You'll need Python and pygtk (which you should already have).

Here is a quick tutorial to get you started:
[http://pygtk.org/articles/applets_arturogf/](http://pygtk.org/articles/applets_arturogf/)

If you have any questions about that let me know ;)

---

### Post by Enygma on 2004-11-30
Excellent stuff! Thanks a lot! 
I'll give Python a go then, just wanted to try it in C# as I'm learning it at the moment. 

Python it is then :)

---

### Post by randy on 2004-11-30
You can write a Notification Area Applet quite easily in C# though.  I've done them in a couple of hundred lines of Code.  An example of one is rml's homeland security threat level applet. They'll still show up on the task bar (that's were gaim and rhythmbox icons live)

---

### Post by Daniel G. Taylor on 2004-11-30
[QUOTE=randy]You can write a Notification Area Applet quite easily in C# though.  I've done them in a couple of hundred lines of Code.  An example of one is rml's homeland security threat level applet. They'll still show up on the task bar (that's were gaim and rhythmbox icons live)[/QUOTE]
 According to the GNOME Human Interface Guidelines this area should be used for notifications, **not** for applets that continually sit on the panel.

GNOME HIG: [http://developer.gnome.org/projects/gup/hig/](http://developer.gnome.org/projects/gup/hig/)
Section on the notification area: [http://developer.gnome.org/projects/gup/hig/2.0/desktop-notification-area.html](http://developer.gnome.org/projects/gup/hig/2.0/desktop-notification-area.html)

As an example this area would be where you show a mail envelope icon when (and only when) the user has new email. If there is no new email, no icon is shown.

P.S. Thought I'd also mention that the best support for GTK and GNOME is for C, and all the other language bindings are based on the C versions. That said, the Python bindings are usually great, but I have run into occaisional problems.

Also, at some point you should be able to use your Python applets with C# code using IronPython in the CLR.

---

### Post by Enygma on 2004-11-30
[QUOTE=randy]You can write a Notification Area Applet quite easily in C# though.  I've done them in a couple of hundred lines of Code.  An example of one is rml's homeland security threat level applet. They'll still show up on the task bar (that's were gaim and rhythmbox icons live)[/QUOTE]
 That's great stuff randy, just what I was looking for!
Can some explain the autogen stuff to me please? Looks like there's a lot going on here. Do I need to know about all of it?

---

### Post by randy on 2004-11-30
The autogen stuff is for autoconf and automake.  The best tutorial/introduction that I've found is the one that is in The Official Gnome 2 Developer's Guide.  (I'm not sure if it's available online though)  Have you checked the mono developers notebook? And I don't think you would have to add much to it to get it to work though.

---

### Post by Enygma on 2004-11-30
Managed to adapt that code for my own purposes. I'll look into those guides now, thanks a lot.

---

### Post by Enygma on 2004-12-01
Found this little gem on my travels, displays svg notifications. Sweet.

[http://mspace.berlios.de/gunther-user/view.php/page/MonkeyPop](http://mspace.berlios.de/gunther-user/view.php/page/MonkeyPop)

---

