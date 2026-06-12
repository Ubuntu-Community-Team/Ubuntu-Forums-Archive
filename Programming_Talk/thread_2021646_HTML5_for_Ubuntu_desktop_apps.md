---
title: "HTML5 for Ubuntu desktop apps"
date: 2012-07-09
forum: Programming Talk
---

### Post by snowz on 2012-07-09
There's this new **RSS** application called **LightRead ( from Ubuntu App Showdown )** and It's said that everything apart the Unity integration is made with **HTML5**.

What does this mean? How to display it as a standalone application if its using HTML5 and CSS for the GUI design?

---

### Post by juancarlospaco on 2012-07-10
> **snowz said:**
> What does this mean?

I dunno.

> **snowz said:**
> How to display it as a standalone application if its using HTML5 and CSS for the GUI design?

Depends on what you try to do, what App you try to make, 
what language to use, but just embed a Webkit and make the HTML5 there.

I coded this App for myself, for CCNA:

[IMG]https://lh3.googleusercontent.com/-iuYUxz0FQb4/TsmIwOTSoTI/AAAAAAAAA0s/FCunGAzO6mo/s640/nethelper3.jpg[/IMG]

[IMG]https://lh5.googleusercontent.com/-0WawB9zcqig/TsmJOfAxvGI/AAAAAAAAA08/aH0s1SPPvlE/s640/nethelper2.jpg[/IMG]

As you can see, its just a Python + Qt + Webkit script 
and a HTML5 + CSS3 + JS App inside, the PyQt GUI is Transparent.

---

### Post by Dragonbite on 2012-07-10
> **snowz said:**
> There's this new **RSS** application called **LightRead ( from Ubuntu App Showdown )** and It's said that everything apart the Unity integration is made with **HTML5**.

What does this mean? How to display it as a standalone application if its using HTML5 and CSS for the GUI design?

Yeah, I read that article this morning and it got my wheels turning too...  Then when you think the Mozilla's phone is going to run only HTML5 applications on it, I see a bright future.

According to one of the comments> The HTML5 interface runs in WebKitGtkI'm going to have to look into that.

---

### Post by MG&amp;TL on 2012-07-10
There's a good tutorial here: [http://developer.gnome.org/gnome-devel-demos/3.5/message-board.c.html.en](http://developer.gnome.org/gnome-devel-demos/3.5/message-board.c.html.en)
It's for C, but it's not difficult to port to *-gobject languages. Give us a shout if you want help with pywebkitgtk, I used that briefly for a demo.
[]("http://developer.gnome.org/gnome-devel-demos/3.5/message-board.c.html.en")

---

### Post by snowz on 2012-07-10
Thanks for the replies. I've found the information before today though, just forgot to mention it back in my topic. The power of HTML5 and WebKit is pretty interesting yeah :)

---

### Post by Dragonbite on 2012-07-10
> **snowz said:**
> Thanks for the replies. I've found the information before today though, just forgot to mention it back in my topic. The power of HTML5 and WebKit is pretty interesting yeah :)

But in using WebKit, does that cause any problems accessing via Gecko (Mozilla)?

---

### Post by MG&amp;TL on 2012-07-10
> **Dragonbite said:**
> But in using WebKit, does that cause any problems accessing via Gecko (Mozilla)?

I think so, yeah. You can't use both, they use different rendering concepts. Unless of course there's Gecko for GObject and co.

---

### Post by Dragonbite on 2012-07-11
> **MG&TL said:**
> I think so, yeah. You can't use both, they use different rendering concepts. Unless of course there's Gecko for GObject and co.

For applications on Linux, I don't think this is going to be such a big deal.  

On the web, though, people focusing on WebKit over other engines is starting to fragment the web again that if it gets worse, could be reminiscent of sites developed targeting IE.

---

### Post by juancarlospaco on 2012-07-11
> **dragonbite said:**
> is starting to fragment the web again that if it gets worse, could be reminiscent of sites developed targeting ie.

???  :/

---

