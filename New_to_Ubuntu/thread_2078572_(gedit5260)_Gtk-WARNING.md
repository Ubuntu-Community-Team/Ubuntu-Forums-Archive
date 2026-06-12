---
title: "(gedit:5260): Gtk-WARNING"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by chacank on 2012-10-31
hi all ..
I have a problem .. :-?
when I open gedit through terminal, a warning message appears as follows : :-k

```
chacank@biters:~$ sudo gedit /etc/apt/sources.list

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:92:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:209:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:245:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:361:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:626:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:802:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1147:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1217:18: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1217:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1241:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1253:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1753:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1848:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1865:21: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1881:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1971:11: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:27:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:104:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:194:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:514:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:861:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:936:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:952:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:968:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1023:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1031:21: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1043:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1112:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1246:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: gnome-panel.css:92:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:14:18: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:14:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:110:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:115:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:140:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:146:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:152:21: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Theme parsing error: nautilus.css:168:20: Not using units is deprecated. Assuming 'px'.

(gedit:5260): Gtk-WARNING **: Failed to parse /usr/share/themes/mac-os-lion-theme-v2/gtk-3.0/settings.ini: Key file contains line '/* ' which is not a key-value pair, group, or comment
chacank@biters:~$ 

```

I think maybe my nautilus error, so I removed and replace it with nemo. :idea:
but the problem still appears, when I open the file manager .... about 2 minutes later, I could not do anything (freeze / hang) and the file manager is closed by itself. #-o

please help me .... 
what is wrong with my linux and how do I fix it. ?? ](*,) ](*,)

---

### Post by Zill on 2012-10-31
From [RootSudo Community Documentation:]("https://help.ubuntu.com/community/RootSudo")
> Graphical sudo

You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root.
Example:
```
gksudo gedit /etc/fstab
```

---

### Post by chacank on 2012-11-18
thanks for your answer were very helpful .. (y)

my problem is solved now .. :)

---

