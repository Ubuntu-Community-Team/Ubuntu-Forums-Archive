---
title: "Glade3 development"
date: 2007-02-05
forum: Programming Talk
---

### Post by j_g on 2007-02-05
I'm trying to develop a GTK app using Glade3. Unfortunately, it seems like some sort of environment variable is insistent upon directing GCC toward older GTK and glade include and lib files. If I do a libglade-config --cflags, I get:

-I/usr/include/gnome-xml -I/usr/include/libglade-1.0 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include

Now, I do have a libglade-2.0 directory in usr/include. I also have a gtk-2.0.

How do I tell GCC to use the newer includes/libs?

(This foray into Linux programming has really made me appreciate how easy it is to develop Windows software with Microsoft Visual C++. I was thinking of moving my systems to Linux, but now I'm not so sure. Should I maybe switch to Suse or Fedora? I notice that I can get RPMs of the latest version of Anjuta for those distros. But there's no builds of 2.1.0 for Ununtu. How much does Ubuntu support lag the other Linux distros, particularly for dev tools?)

---

### Post by lnostdal on 2007-02-05
uhm, ```
pkg-config --libs --cflags libglade-2.0
``` (both compiler- and linker-flags at the same time)

which leads to:
```
gcc -g -Wall `pkg-config --libs --cflags libglade-2.0` `pkg-config --libs --cflags gtk+-2.0` gtk-app.c -o gtk-app
```

hope i got that right; it was typed without checking .. linux-coders never-ever do this thing "manually" over-and-over though .. they use things like scons which they call from their editor via a shortcut-key

..now, about that misunderstood rant about environments, just see: [http://ubuntuforums.org/showthread.php?p=2106479#post2106479](http://ubuntuforums.org/showthread.php?p=2106479#post2106479)

don't "give up"; linux is just different .. nothing wrong with that .. it is naturally excellent for programming once you figure stuff out - as it is created by people who love programming

edit:
by the way:
```
pkg-config --list-all
```
..shows other libraries

---

### Post by j_g on 2007-02-05
Whew! Thanks. That did the trick.

I am definitely trying to adjust to Linux. Installing Ubuntu was easy. Adding software was easy via Synaptic. I was hoping development would be fairly easy, given an IDE such as Anjuta. Unfortunately not so. On Windows, we have something called "DLL hell". On Linux, I've discovered that we have something called "Dependency hell".

After dealing with Anjuta's particular version of Dependency Hell *, I figured that I had better go back to developing software the way I did 20 years ago on my Amiga. I'd have to open a terminal window and run gcc with everything explicitly typed out at the command line. This worked just fine for developing X Window apps. Then, I moved on to Motif apps, and it still worked fine. Then I moved on to GTK apps, and it fell right over.

If there's a better way to develop Linux software, I sure wish someone would write a tutorial about it. I did a google for a whole bunch of different searches using "Anjuta", "glade3" (I was surprised that I could find only 1 glade3 tutorial!), "GTK", "development environment" etc. I have yet to run across a good tutorial that tells how to setup and use a development system to develop a particular type of app (ie, XWindows, Motif, Gnome, etc). I think that what Linux needs is more detailed, specific tutorials -- more of the "walkthrough" sort, geared for specific environments/tasks.

* Part of the problem with Anjuta was that, even after hours of trying to compile one of its "GTK++ templates" and going through all the error messages about needing to install various other files, I still ended up with something that couldn't use my Glade3 XML file because Ubuntu had installed a version of Anjuta that didn't support Glade3. So, I went over to Anjuta's web site and downloaded the Anjuta source. I got as far as I could resolving errors by installing various needed packages, but then I got the "Orbit 2.0 must be installed". Well, I did install Orbit 2.0, and even had the directory right there in /usr/lib, but Anjuta refused to see it, and I couldn't figure out how to get the damn IDE to let me tell it where to look. The Anjuta manual desperately needs to be fleshed out with this very important information.

---

### Post by lnostdal on 2007-02-05
> **j_g said:**
> If there's a better way to develop Linux software, I sure wish someone would write a tutorial about it.

Hm, I'll consider(#1) putting up some writings. :} It might come in handy as there does seem to be a lot of people having a hard time "connecting the dots" when it comes to setting up and getting started with the Linux programming environment.

#1: I'll bookmark this thread and get back to it _if_ I get something worthwhile written down. Don't get your hopes up though. :P

---

### Post by j_g on 2007-02-05
Yeah, development on Linux is a perilous journey, although I'm told that KDE developers pay better attention to development support than the Gnome folks do. Apparently, having KDE maintained by a commercial entity translates to better, more actively updated IDEs (KDevelop) that seem to "work right out of the box", and they do more tutorials. It looks like the Gnome folks  put out only "API references" and then leave you to your own devices when in comes to putting a program together.  For example, doing a google of "KDE tutorials" produces lots of relevant links, starting with the very first link, to tutorials that are well-written walkthroughs. Doing a "GTK tutorial" produces a lot less useful content. The first link is to [www.gtk.com](www.gtk.com), and there you'll find what I mean when I say "API references" rather than tutorials.

I would have gone with KDE except I prefer working in C rather than C++. I had assumed Gnome would be easier for that, but it looks like Gnome is trying to transition from C to C++, and in the process of doing this transition (that the KDE developers never had to do), the Gnome folks don't have time to attend to things like support for IDEs, writing tutorials, and the various niceties that make development easier. They're halfway between C and C++, and given that somewhat schizophrenic state of the codebase itself, it seems to be reflected in dev tools that also are a bit of "I sort of support this, but not really, because I'm trying to transition to supporting this instead".

---

### Post by lnostdal on 2007-02-05
..ok.. i've added two initial short tuts about how to get started here: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

note that i'm proof-reading these as you're reading this .. just wanted to get them up in a hurry to show the general idea  ("release early and often"?)

i'm thinking next up is how to debug (gdb+ddd), then move along to gtk+, then glade/libglade .. any comments/wishes/suggestions/critique? :)

..html-versions will follow later, maybe i'll put them on a wiki..

---

### Post by lnostdal on 2007-02-05
> **j_g said:**
> 
..but it looks like Gnome is trying to transition from C to C++,

..they have no such intention at all; that would be very foolish for a lot of reasons (#1)

i get [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) as first hit when googling for "gtk tutorial"

i'm having a hard time seeing the problem: [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/), [http://developer.gnome.org/doc/API/2.0/gtk/index.html](http://developer.gnome.org/doc/API/2.0/gtk/index.html) and [http://developer.gnome.org/doc/API/libglade/libglade.html](http://developer.gnome.org/doc/API/libglade/libglade.html) .. what more do you need? (edit: well, i'm adding some short tuts on how to get started with this using ubuntu specifically)

there is no magic going on by adding an IDE that has some things set up as default .. as soon as you want to use stuff that isn't conveniently set up for you as default you will have to deal with how GCC works and how it finds libraries, headers ..etc.. something will eventually break with the default setup and you'll be unable to do anything if you do not understand how things work behind the covers anyways .. the docs for both kde and gtk+ only describe the things that are common for all setups of kde and gtk+ .. this makes sense

#1: actually; it would be so foolish that i'm betting gtk+ would be forked if they did something like this .. one of gtk+'s main goals is for it to be easily used from other languages -- switching to c++ would complicate this in manymany ways .. it is not something they would do .. ever

edit:
> Yeah, development on Linux is a perilous journey
not at all .. it is only different .. getting started might take some time (especially if you are working against it based on expectations of how "things should be") but once you're up it is excellent ..  also being able to get debug-info from most software because it is open source is very nice sometimes ..

---

