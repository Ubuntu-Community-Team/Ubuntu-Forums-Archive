---
title: "Where is the WebKit API?"
date: 2008-08-26
forum: Programming Talk
---

### Post by Vadi on 2008-08-26
I'm starting a new project and I was looking to use WebKit as a widget for displaying coloured text (along with the ability to save buffer as html, good scalability, and customization).

I ran into a bit of an odd problem though. Typing "webkit api" in google leads me to [this page]("http://webkit.org/projects/webkit/"), which simply says the following:

> WebKit API
Needs to be written.
 
Is there any api at all for it besides Apple's of Objective C ([here]("http://developer.apple.com/documentation/Cocoa/Conceptual/DisplayWebContent/DisplayWebContent.html"))?

---

### Post by Darkhack on 2008-08-26
Yes, there is an API for WebKitGtk which is the name for the GTK+ port of WebKit.  Qt also has a port as of 4.4.  Unfortunately, the GTK+ port is still under heavy development and probably shouldn't be used in anything critical.  It works fairly well though despite a few small bugs and missing features.

Firstly, you'll need to install WebKit and the development libs.  Hardy as some, but they are somewhat out of date.  Stéphane Marguet has been nice enough to keep a PPA with regular nightly builds of WebKitGtk at [https://launchpad.net/~stemp/+archive]("https://launchpad.net/~stemp/+archive").

Documentation is pretty scarce and almost non-existent at this point.  The way I learned was by reading the header files, but thankfully they are well written and easy to understand.  I've been pondering the idea of writing a guide/tutorial for it.  The header files are located at "/usr/local/include/webkit-1.0/webkit".

One more thing.  This has nothing to do with your question, but for anyone else out there who is interested in WebKitGtk, I highly recommend [Alp Toker's Blog]("http://www.atoker.com/blog/").  He's the lead developer of the project currently.  He also has two presentations on WebKitGtk which are very interesting.

[http://www.atoker.com/blog/2007/09/05/webkitgtk-at-linuxconf-europe-2007/](http://www.atoker.com/blog/2007/09/05/webkitgtk-at-linuxconf-europe-2007/)
[http://www.atoker.com/blog/2008/02/26/developing-hybrid-web-gtk-applications/](http://www.atoker.com/blog/2008/02/26/developing-hybrid-web-gtk-applications/)

---

### Post by Vadi on 2008-08-26
Thanks much.

---

