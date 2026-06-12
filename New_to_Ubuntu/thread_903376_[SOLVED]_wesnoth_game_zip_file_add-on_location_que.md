---
title: "[SOLVED] wesnoth game zip file add-on location question"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-28
hi
I am using battle for wesnoth and downloaded the add-on campaigns from the server but they have not shown up when I start the game
Where would they have gone? (they are not in downloads)
The official website says they are often zip files which need extracting
I have looked in the .wesnoth folder but they are not there
if anyone knows where this type of download file goes then I would appreciate it

---

### Post by mcduck on 2008-08-28
All official extra campaigns are in Ubuntu's repositories, so you can just install them with Synaptic.. ;)

---

### Post by Vadi on 2008-08-28
Probably somewhere in the system files (/usr)... why, does wesnoth not see them or something?

---

### Post by LTFC2020 on 2008-08-29
no they are not recognised by wesnoth

---

### Post by Vadi on 2008-08-29
Try installing .debs from getdetdeb ([http://www.getdeb.net/search.php?keywords=wesnoth)?](http://www.getdeb.net/search.php?keywords=wesnoth)?) It has some campaigns packaged

---

### Post by maybeway36 on 2008-08-29
Normally the addons show up in ~/.wesnoth/data somewhere.
If you downloaded a one-player campaign it should be in the Campaigns menu, but many of the add-ons are actually 2-player scenarios which would be in Multiplayer.

---

### Post by LTFC2020 on 2008-08-29
thanks vadi
I tried get deb but there was a conflict with the packages so I could not install the campaign deb
maybe because I have wesnoth 1.4.1 and this was 1.4.4?

---

### Post by Vadi on 2008-08-29
Ah maybe, but there is a wesnoth package right there too. Install that to get 1.4.4 wesnoth

---

