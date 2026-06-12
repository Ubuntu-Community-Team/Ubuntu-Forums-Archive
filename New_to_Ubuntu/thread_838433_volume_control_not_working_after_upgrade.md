---
title: "volume control not working after upgrade"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by ayeshap on 2008-06-23
i just downloaded the upgrade from ubuntu 7.10 to 8.04 LTS and now there's an red x by my volume control.when i try to play music an error occured msg comes up. when i double click on the volume control a msg comes up saying 'no volume control GStreamer plugins and/or devices found'

how can i fix this?

---

### Post by Biggy on 2008-06-23
install from Add/Remove GStreamer plugins

---

### Post by ayeshap on 2008-06-23
i did that and i have all the Gstreamer plugins i could find in add/remove but the red x is still next to the volume control and the same msgs are still coming up.
no sound is playing at all

---

### Post by Duck2006 on 2008-06-23
Try finding it in Synaptic Package Manager.

---

### Post by ayeshap on 2008-06-23
what exactly do i have to search for in the synaptic package manager? because i searched for Gstreamer plugins and i have them all but the same msg is still coming up.

---

### Post by Biggy on 2008-06-23
from System > Administration > Software Sources make checked all options on first tab ( Ubuntu Software )

from terminal :

sudo aptitude update

---

### Post by ayeshap on 2008-06-23
ok still the same thing...however, another msg came up saying
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

the sound was working fine all the time with 7.10.my laptop is a dell inspiron 1525.i dunno if that info would help.

---

### Post by ayeshap on 2008-06-23
should i reinstall 7.10?

---

### Post by Duck2006 on 2008-06-23
I had this problem a wile back, and thats what fixed it for me a reinstall.

---

### Post by the_doc on 2008-06-23
I don't know if this thread helps, it originated a while ago but has helped someone recently by the looks of it.

[http://ubuntuforums.org/showthread.php?t=543793](http://ubuntuforums.org/showthread.php?t=543793)

---

