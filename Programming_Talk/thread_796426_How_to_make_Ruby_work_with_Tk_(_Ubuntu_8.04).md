---
title: "How to make Ruby work with Tk ( Ubuntu 8.04) ?"
date: 2008-05-16
forum: Programming Talk
---

### Post by Xanrov on 2008-05-16
I'm playing with Ruby, following the excellent tutorial "The Pragmatic Programmer guide". No problems so far except the following:
The author gives a short example of Ruby/Tk which must start by : require 'tk'. The interpreter immediately complained it didn't know any 'tk'. Well, I apt-get installed tcl, then tk, but I have still the same complaints.
Obviously the file system in Ubuntu may differ somewhat from that of the typical Linux box used for the example.
In Short : what the "require" line must be in ruby 1.8 and Ubuntu 8.04 ?
Thanks in advance for any tip !

---

### Post by winch on 2008-05-16
You probably also need libtcltk-ruby

---

### Post by stevescripts on 2008-05-16
The directions at this link :
[http:///www.tkdocs.com/tutorial/install.html]("http:///www.tkdocs.com/tutorial/install.html")
work well for me on Gutsy.  If you dont mind the bit of hassle of building tcl/tk 8.5 from scratch, (or installing the Active State distro) you will have access to the new widgets (previously known as Tile) ...

That website is a nice tutorial on using RubyTk also. (It is oriented to the new widgets though)

Steve

---

### Post by Cactus Sediento on 2009-03-03
Thanks winch! Your suggestion (libtcltk-ruby) resolved my problem! 

Now **require 'tk'** runs ok from ruby

---

