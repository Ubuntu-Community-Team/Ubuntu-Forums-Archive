---
title: "Mono + Converting .NET app to Mono"
date: 2007-11-02
forum: Programming Talk
---

### Post by carlosjuero on 2007-11-02
Ok, heres the deal: I have this nice little app I programmed in C# .NET on Windows, what it does is connect to my websites backend and allow me to post news updates and whatnot without opening my web control panel - it is basic, but it works well for what I want it to do.

I am wondering if there is a nice way to 'convert' this to a Linux Mono project?

The app uses .NET 2 routines (of course), and it has the embedded IE control as well as making good use of the toolbar ribbons. It also uses the MSXML web interface to submit data to the backend scripts.

Where should I take a gander to try and start converting this? What is the best Mono development app for this type of work? (I have MonoDevelop installed, and it is ok but if there is something better I am wide open to suggestions).

I know I could create a text based updater with no problems, but I want a GUI and I would like to be able to keep it in C# (or the Mono equivalent) so that the rewriting of code is at a minimal (the code works great on Windows, I don't like messing too much with something that works great :) ).

Thanks in advance.

---

### Post by emperon on 2007-11-02
If you haven't used P/Invoke and non managed libraries, your application is most likely to work on mono out of box. Current windows forms support although not complete , is quite promising. There is a special tool for mono people prepared for porting programs called [Moma]("http://www.mono-project.com/MoMA")
This might help you to analyze how portable your application for the time being and how you could further iron out the incompabilities.

Concerning your application, the biggest question mark arose on my mind was of course the embedded IE thingy. I bet mono counter part was embedded Gecko. However if your intention is to post news to a website WebRequest and WebResponse classes with standard winforms looks like a smarter choice

For the development environment you have two options. One is monodevelop which is quite nice these days as of 0.16 version. The other was using vim/gedit + nant. In the latter you lose the intellisense but including me lot's of mono guys find this option as viable as well.

I hope it helps. Happy Mono'ing!

---

### Post by tyoc on 2007-11-02
Take in count that MoMa is no definitive, I mean after pass all checks that MoMa perform, you should actually try to run it and start debug.

There was a presentation on SUSE that contain 10 steps to watch in the migration process, try to find it if possible.

---

### Post by carlosjuero on 2007-11-03
Ok, thanks both of you; I will check out MoMa and see what it says.

I spent some time reviewing the .NET code, I think the GUI will present the most problems - the XML requests can be converted easily enough but the GUI uses newer .NET GUI items. Data file access is pretty standard (for local files), so that doesn't worry me.

The IE control was used for a 'live preview' of how the entry will look online (with the website styles applied), the gecko control might work - I will have to see about that. If that fails, I can just route the preview through a local webserver copy of the base site code for style preview (it is much much less overhead intensive to have Apache running with PHP, Perl, and MySQL here on Ubuntu :D).

@emperon: I will try out a vim + nant combo to see how it works. Monodevelop is a nice 'easing' app, as it tries to emulate the .NET IDE pretty successfully.

@tyoc: I will do a search for that SuSE presentation, thanks.

---

