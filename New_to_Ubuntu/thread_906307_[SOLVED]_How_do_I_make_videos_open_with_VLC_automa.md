---
title: "[SOLVED] How do I make videos open with VLC automatically?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Anathallo on 2008-08-31
When I open videos they only open in totem, I have to right click on them to open with vlc. How do I get them to open with vlc automatically?

---

### Post by WRDN on 2008-08-31
Right click on the file, and select Properties. Click the Open With tab, and select VLC.

---

### Post by jemate18 on 2008-08-31
> **Anathallo said:**
> When I open videos they only open in totem, I have to right click on them to open with vlc. How do I get them to open with vlc automatically?

1. Right click on the video file
2. Click "the Open with" tab
3. Select VLC Media Player

or

1. Right click on the video file
2. Click Open with Other Application
3. Scroll down and select VLC


Take note that you have to do this for different video files separately
for example for avi, rmvb and other file formats

Mark this thread SOLVED "https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button on the lower right "medal icon" for their help and useful post

jemate18

---

### Post by drubin on 2008-08-31
Also to change it perminatly 
  
System,Preferences, Preferred applications. Multimedia tab.

Change that option to VLC.

---

### Post by silkstone on 2008-08-31
Do you mean mpeg files or DVDs? To make VLC the default DVD player....

gksudo gedit /etc/gnome/defaults.list

Scroll down to the entries for "x-content/video", and change "totem.desktop" entries to "vlc.desktop". Close and save.

Next, right-click on "Applications" in the top panel and select "Edit Menus" to open the menu editor. Navigate down to "Sound & Video" in the left pane and click on it to show the applications in the right hand pane.

Find "VLC media player", right-click on it, then click on "Properties" in the context menu to open "Launcher Properties" and change the launch command from "vlc %U" to "vlc %m" - without the inverted commas, of course.

---

