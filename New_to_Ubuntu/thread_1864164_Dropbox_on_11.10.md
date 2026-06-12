---
title: "Dropbox on 11.10"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-10-18
Hi All,

I did a clean install of 11.10.
I then set up Dropbox.  It works fine, except, in previous versions of Ubuntu I used to have the ability to right click a file and copy the public link for the file.

Now the entire Dropbox menu is gone from my right click menu.

Does anyone know how I can get it back?

---

### Post by computerandu on 2011-10-18
Try this:

sudo add-apt-repository ppa:nilarimogard/webupd8 sudo apt-get update
sudo apt-get install dropbox-share
sudo apt-get install unity-dropbox-share


**The Unity Dropbox Share icon isn't automatically added to your Unity launcher so you'll have to add it manually it: **open Nautilus and navigate to */opt/unity-dropbox-share/*, then drag and drop the icon to the Unity launcher or Cairo Dock, AWN, Docky, etc.


Now you can share files or folders using Dropbox by right clicking in Nautilus and selecting *Scripts > Dropbox Share* or by drag'n'drop onto the custom launcher.

Source:
[http://www.webupd8.org/2011/09/dropbox-share-updated-for-ubuntu-1110.html](http://www.webupd8.org/2011/09/dropbox-share-updated-for-ubuntu-1110.html)

---

### Post by GrouchyGaijin on 2011-10-18
> **computerandu said:**
> Try this:

sudo add-apt-repository ppa:nilarimogard/webupd8 sudo apt-get update
sudo apt-get install dropbox-share
sudo apt-get install unity-dropbox-share


**The Unity Dropbox Share icon isn't automatically added to your Unity launcher so you'll have to add it manually it: **open Nautilus and navigate to */opt/unity-dropbox-share/*, then drag and drop the icon to the Unity launcher or Cairo Dock, AWN, Docky, etc.


Now you can share files or folders using Dropbox by right clicking in Nautilus and selecting *Scripts > Dropbox Share* or by drag'n'drop onto the custom launcher.

Source:
[http://www.webupd8.org/2011/09/dropbox-share-updated-for-ubuntu-1110.html](http://www.webupd8.org/2011/09/dropbox-share-updated-for-ubuntu-1110.html)

Thank you.
That works to a point.  I used to be able to choose "Copy public link" from the right click menu as well.
Am I missing something in the script or do I need to go to the Dropbox website and click copy public link?

SCRATCH THAT

I see the copy last public link to the clipboard thing now.

---

### Post by computerandu on 2011-10-18
Ubuntu means helping...:P

---

