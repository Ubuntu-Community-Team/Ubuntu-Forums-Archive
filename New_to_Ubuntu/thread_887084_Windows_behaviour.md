---
title: "Windows behaviour"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by NaF on 2008-08-11
So. I've made a thread earlier, that ended up with going into nautilus: edit - preference - behavior and deselecting "always open in browser windows", so i wouldn't end up with a milliion windows of the same folder. kinda solved. Instead of the same folder, i'm drowning in parent folders (or what it's called) When i'm going to /home/naf/.wine/c_program ... / I end up with 11 or more windows, I **really** don't need - just want the same folderwindow to go on, deeper into the hierarchy  

Halp :(? How can i make sure I wont have 11 copies of /home open and make sure that while browsing folders, there wont pop more up than the one i'm focusing on?

---

### Post by NaF on 2008-08-12
Did i explain the issue sufficient, or is it simply not possible?

---

### Post by Dill on 2008-08-12
I think you actually want to check the box that you unchecked originally. When you uncheck "Always open in browser windows" under "Behavior", the file manager acts in a "spatial" manner ([http://en.wikipedia.org/wiki/Spatial_file_manager](http://en.wikipedia.org/wiki/Spatial_file_manager)), and opens a new window for each directory into which you navigate.

However, if you keep the box checked, I think it should behave as you want, where you only have one window open, no matter how far down the file system you go. 

Is that clear? And is that the behavior to which you were referring? 

Cheers,
Dylan

---

### Post by mcduck on 2008-08-12
You have couple of options: 

First, to learn how to use the Spatial mode. It helps a lot to know that if you open something with middle click the parent window will be automatically closed. This alone is enough to stop your desktop from filling with Nautilus windows.

Second, enable the "ubuntu spatial", which isn't really spatial at all but still uses the small windows instead of browser. This allows (or forces) all directories to open in the same window. It can be enabled through gconf-editor (hit alt-f2 and run "gconf-editor"), I can't remember the exact key but it's somewhere under apps/nautilus/..

Third, just use the browser mode.

---

