---
title: "Home Center (Low-end HTPC framework)"
date: 2008-04-05
forum: Programming Talk
---

### Post by graey on 2008-04-05
I've had this idea of taking an older (say pentium 3 500mhz - 1000mhz) PC/laptop with tv out, installing a flavour of linux (xubuntu was my idea), add a custom full-screen big-button easy to navigate interface and set it near the tv.
It's not my goal to actually set up a tuner card in this pc, or to view HD-movies or DVDs or something, just a basic frontend to the web (RSS feeds and maybe long-term an easy to use webbrowser) and network (Windows-shares as well) for playing back music from different computers or a NAS. All this through a tabbed interface, easy and clear enough to be used with 5-6 keys on a remote control.
Detailed specifications might be coming up, but I figured such things done once the team is there (if there's ever to be a team ofcourse, but I'm being optimistic here).
Basic idea of me was to enable users to write their own 'applets' for Home Center (working title ofcourse), writing the UI in XML (Home Center'd read that and create GTK(#) widgets and everything), and the real 'applet' code in scripting languages such as LUA (using tao.lua?), javascript and stuff, and maybe using Script# for that too...
It'd obviously be important to add some objects for use in those scripting language that give access to a media player (gstreamer?), network shares (maybe a 'normal' folder mounted with fusesmb?), internet connections, RSS / xml parsing and more...

Now back in the days I used Windows and nothing more I might have been able to pull it off in Visual Studio .net 2005, but even then my WinForms desiging and coding would be crappy, so that's the main issue.
I'm really looking for people who are more experienced in writing C# .net apps for Mono, preferably in MonoDevelop using the Stetic designer, but not necessarily (as long as I can edit, debug and run the stuff in MonoDevelop I'm happy enough :P).

---

### Post by phynix on 2008-05-31
I think this would be a cool idea.

---

