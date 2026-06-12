---
title: "Java: How to retreive a file icon for a file?"
date: 2010-11-15
forum: Programming Talk
---

### Post by veroslav on 2010-11-15
Hi all,

I would like to know how I can obtain an Icon for a File in Ubuntu.
In Windows, I was using the following code:

FileSystemView.getSystemIcon(File)

but it does not work in Ubuntu (it always returns a generic file icon no matter what the file type is). I guess it has to do with the many different desktop managers being used (such as Gnome). Is there any other way I can pull this off? Perhaps through
JNI?

Thank you in advance!

Kind Regards,
Veroslav

---

### Post by muze4life on 2010-11-15
Yes with a but and no with an unless.

Yes, but you'll have to work quite a lot.
No, unless you're willing to put up with the problems that will arise.

Java only supports file icons in a half-hearted way as a stopgap, to get "the real native icons" you have to learn how Linux distros work.

Linux distros (try to) follow the so called "free desktop specifications", in your case you'll have to learn at least this:
(Icon theme specification)
[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)
and this:
(Desktop entry specification)
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

Then, create your implementation plus work around Java related issues, for instance, the icons in Linux might be not only in .png or .jpeg format but also .svg (quite often) and .xpm (still used by "super-conservatives" to stay backwards compatible with commodore-64 era software), so you'll have to find Java software that can read these image formats, Batik might do well for SVG but it's still a half baked solution (you'll learn why as you start testing it).

So good luck with this, but I doubt you're willing to go that far.

Or, you could use command-line  utilities, but you probably can't count on them being installed by default, plus, they didn't work for me as expected either.

---

### Post by Reiger on 2010-11-15
There are a few ways to do it. One of them is a JDIC incubator project: 

[https://jdic.dev.java.net/servlets/ProjectDocumentList?folderID=2750&expandFolder=2750&folderID=1304](https://jdic.dev.java.net/servlets/ProjectDocumentList?folderID=2750&expandFolder=2750&folderID=1304)

With a little experimenting you should be able to get that to work.

Another way is to tie yourself to a specific platform, for instance GNOME. Then you can probably get bindings like:
[http://java-gnome.sourceforge.net/4.0/](http://java-gnome.sourceforge.net/4.0/)

Which provide icon theme access like this:
[http://java-gnome.sourceforge.net/4.0/doc/api/org/gnome/gtk/Icon.html](http://java-gnome.sourceforge.net/4.0/doc/api/org/gnome/gtk/Icon.html)

---

### Post by muze4life on 2010-11-15
Using a "Gnome-only" solution might not be the best idea since nowadays both KDE and Gnome pretty much follow the "free desktop specification", not to mention that the JDIC project hasn't been updated in the past 5 years.
Yes, what I'm suggesting is that if one goes down to Gnome-specific features then the whole point of using Java becomes less reasonable and make one wonder if C/C++ with Gtk+ is more appropriate.

---

### Post by veroslav on 2010-11-17
Hi again,

thank you for your replies, the links provided were interesting but as you already mention, it seems a bit of a hassle for such a small benefit it provides.

Therefore I decided to keep the current "solution" and show generic icons.

I am aiming for maximum platform independence and that is why I cant lock myself to Gnome only.

Btw, if you are interested, the project I am working on is a BT client implementation and so far it is going pretty well :)

Kind Regards,
Veroslav

---

