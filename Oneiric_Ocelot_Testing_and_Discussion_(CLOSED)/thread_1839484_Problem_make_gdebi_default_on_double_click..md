---
title: "Problem: make gdebi default on double click."
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Xgen on 2011-09-05
Is there a trick to make gdebi the default selection for .deb files in oneiric nautilus? It does not show up in the alternate selections (unless under a different name) and there isn't a way to list it manually as before. I know that it is on the context menu, but I would like it as default.

---

### Post by mc4man on 2011-09-05
go -
```
gedit ~/.local/share/applications/mimeapps.list
```
mimeapps.list now uses at least 2 sections, add a line into each one as below
Edit: if either or both of those lines exist then append gdebi.desktop; to the Added & make gdebi.desktop the only entry on the Default line.

```
[Added Associations]
application/x-deb=gdebi.desktop;
```

```
[Default Applications]
application/x-deb=gdebi.desktop
```
log out/in and you should be ok

(note that there are some .debs that gdebi will now refuse to install, if that ever happens just use dpkg

---

### Post by Xgen on 2011-09-05
Thank you immensely, Mc4man -that worked fine. What an incredibly intuitive solution <sarcasm> :P compared to the the overly simplistic way that it used to be. I have been using Ubuntu since Dapper but it is getting harder and harder not to stick with Maverick...but I like the stress of the challenge.

---

### Post by mc4man on 2011-09-05
Back in A1 gdebi wouldn't even show up - that was fixed by adjusting the gdebi.desktop
Now it does show in the context but for some unknown reason will not show in the properties ( seems nonsensical because, as you probably have seen, just about every other app installed does show in that list.

Chalking it up to some gnome/nautilus 3 behavioral defect, don't think I'll bother refiling a bug

---

