---
title: "Wrong default application after upgrading to Ibex"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by david_kt on 2008-11-02
This morning I just finished upgrading from hardy to ibex, some functions not working:

Application > Home folder  ===> open movie player
Application > Desktop      ===> open movie player

all bookmark also open movie player.

I suspect the default application is wrong and it is true.
The default application to open directory is movie player, and many movie player listed on the "open with" tab.

Mp3 file property are also includes many unrelated programs such as text editor in "open with" tab.

So, I need to do some cleaning on the open with tab, and also set the appropriate program as the default application.

Hopefully this information will be useful for you.

DK

---

### Post by bscbrit on 2008-11-02
I assume you are in Ubuntu and K- or Xbuntu. 

Open Nautilus and navigate to the type of file that you want to open e.g 'something'.mp3.  Right click on 'something.mp3' and select Properties.  Select the 'Open With' tab and choose the program that you wish to be the default from those in this list.  Done.

This works for directories/folders as well.

There is no problem with there being too many entries in the Open With tab - you can just ignore them.

---

### Post by taavikko on 2008-11-02
Known bug
[https://bugs.launchpad.net/bugs/260492](https://bugs.launchpad.net/bugs/260492)

---

