---
title: "[SOLVED] HOWTO: right click and open a file in Nautilus with gedit as root"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-13
we often need to edit files as root in a text editor. Now we can do this with a right click in Nautilus (no big deal about opening in terminal but what the heck!)
```
gedit ~/.gnome2/nautilus-scripts/gedit-root
```
Copy the following lines into the file and save it and close it.
```
#created by arnieboy
foo=`gksudo -u root -k -m "enter your password for gedit root access" /bin/echo "Do you have root access?"`
sudo gedit $NAUTILUS_SCRIPT_SELECTED_URIS
```
Then make it executable with
```
chmod +x ~/.gnome2/nautilus-scripts/gedit-root
```
thats it you are all set. Now right click on any file in nautilus and under "scripts" u will find "gedit-root"
click and enjoy!
U can even select multiple files and open them in gedit as root in tabbed windows just by right clicking and using this script. The possibilities are endless.

---

