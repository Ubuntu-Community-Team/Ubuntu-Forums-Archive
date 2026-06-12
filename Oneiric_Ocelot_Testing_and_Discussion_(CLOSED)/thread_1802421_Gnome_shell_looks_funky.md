---
title: "Gnome shell looks funky"
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by linuxman94 on 2011-07-11
I've installed gnome shell and when i choose it and log in, the top bar sometimes is a werid blue color or it is just clear.  Furthermore, when i go to applications the shell crashes.  I would take a screenshot (attached) but when i do it just shows the wallpaper and not the shell!  I'm using the gnome shell testing ppa but this also happens with the version in the ubuntu repos.  Also using fglrx on a radeon hd3000 (RS780nb).  I have gnome-themes-standard installed.

Any ideas?

---

### Post by ranch hand on 2011-07-12
I realize this is no help what so ever but  I am happy to hear of your problems.

Most of them are pretty well duplicated on my Debian install.

I think the screen shot thing is really strange.  I had the package "scrot" recommended to get a screenshot with.  Works exactly the same as gnome screenshot.  Nice picture of the wallpaper.

I do not know how many times you have booted to GS.  It seems to look different, slightly, each time on my install.  Usually it is an improvement. 

I do have the friperies extensions on mine but it was working some better than yours when I did that.

The top bar can sometimes be readable.  Sometimes not so much.

The screen with the dock and workstations works fine though and always has, if you like the intended functionality.

One of those extensions gives you a real menu.  That is really slick to have back if you can read.

One gives you a bottom bar with a windows list.  Also VERY nice.  That one also gives yo ua set number of workspaces.(you need to set it in gconf-editor) and a workspace switcher on that bottom panel.

If you can get to synaptic see if the package gnome-session-common is in there.  May be different in the Ubuntu repo.  If it is, try reinstalling it.  Might help.  Might not.

What is the worst that can happen?  The thing may be like it is now.

---

### Post by jfernyhough on 2011-07-12
If you're running the AMD proprietary drivers (fglrx) then this is a known issue. It's something AMD are doing (or not doing) as the open-source drivers work fine (as well as it being fine with the NVidia drivers).

---

### Post by el_koraco on 2011-07-12
GS don't work with fglrx, as usual. Remove them and use the open source drivers. Maybe stuff will be rectified with the next Catalyst.

---

