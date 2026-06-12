---
title: "snap updated Inkscape to 1.2 but this snap version has issues."
date: 2022-07-06
forum: New to Ubuntu
---

### Post by dale-walton on 2022-07-06
Inkscape list several issues for snap version Inkscape 1.2

The one that affects me is an issue of exporting files.  Inkscape website states this is a vendor problem:
If you try to save as PDF or any other non-SVG file format and Inkscape  creates an SVG file instead that only has a different file extension and  does not open correctly in the program it should be opened with, this  is usually the result of outdated xdg-portals. Please talk to your  desktop vendor about updating them.

The application is saving to a directory /run/user/1000/doc/ <8 character hexidecimal> 
and creating a file in the target directory that looks like .xdp_<file name>.ZDP701.

Have the  outdated xdg-portals mentioned been fixed?

---

### Post by deadflowr on 2022-07-07
What release of Ubuntu?

---

### Post by dale-walton on 2022-07-07
20.04.4 LTS 64-bit Gnome 3.36.8 X11
Intel® Core&#8482;2 Quad CPU Q9450 @ 2.66GHz × 4  / NVE7 3.4 Gib Memory.

---

### Post by grahammechanical on 2022-07-07
> Have the  outdated xdg-portals mentioned been fixed?

You should be directing that question to the developers of Inkscape. By the way, Ubuntu Software on 20.04 still has the deb version of Inkscape.

[https://snapcraft.io/inkscape](https://snapcraft.io/inkscape)

---

### Post by deadflowr on 2022-07-07
According to this bug report it was fixed: [https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal-gtk/+bug/1973564]("https://bugs.launchpad.net/ubuntu/+source/xdg-desktop-portal-gtk/+bug/1973564")
Though, if you are having issues still, you might need to file new bug report.

Sort of +1 to posting over at the [snapcraft forums]("https://forum.snapcraft.io/"), as the snap developers tend to frequent there more than here.
They might be able to help better with this issue. If it is still an issue.

---

### Post by ajgreeny on 2022-07-07
Should you not want to use a snap version and are prepared to accept the risk (not certain how big a risk that is), you could try the ppa for both Focal and Jammy which is at [https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable-1.2](https://launchpad.net/~inkscape.dev/+archive/ubuntu/stable-1.2)

I haven't used inkscape for many years now so have no idea how good the version available is, so I give you the opportunity to look at test for yourself.

---

### Post by #&amp;thj^% on 2022-07-07
Along with ajgreeny's suggestion it's available as a flatpak as well.
```
flatpak search inkscape
Name    Description                  Application ID       Version Branch Remotes
Inksca? Vector Graphics Editor       ?g.inkscape.Inkscape 1.2     stable flathub
Boxy S? Scalable Vector Graphics ed? com.boxy_svg.BoxySVG 3.86.5  stable flathub

```

---

