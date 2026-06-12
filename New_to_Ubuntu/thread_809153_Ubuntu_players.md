---
title: "Ubuntu players"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-27
Hy all
Is there another music player, beside Amarok, which shows the song lyrics? I am having troubles with Amarok (no lyrics script are working) so I decided to ditch it.Any suggestions?

---

### Post by dje on 2008-05-27
I think banshee can get song lyrics

EDIT: It can't by default, there's a plugin [here]("http://www.gtk-apps.org/content/show.php/Banshee+Lyrics+plugin?content=64837")

EDIT 2: listen has lyrics by default
```
sudo apt-get install listen
```

hope that helps,
dje

---

### Post by skip mcshwang on 2008-05-27
Exaile has lyrics, also artist and album info from wikipedia

---

### Post by Troll_the_Great on 2008-05-27
Hmm...Something is wrong....I installed Exile and when I tried to play a file it just froze...Any ideas why?The same thing happened with banshee....Any ideas why?

---

### Post by Troll_the_Great on 2008-05-27
If I try to play something I get this message "You do not have the appropriate Gstreamer plugin installed to play this file: file:///media/disk/Muzica/Smokie - Full Discography/1990 - Boulevard of Broken Dreams/11 - Heart need company.mp3".How can I get the plugin?If I try to install from "Plugins" it says "No plugins or updates could be found for your version"...Can someone help me?

---

### Post by sayakb on 2008-05-27
```
sudo apt-get install ubuntu-restricted-extras
```
Would install the needed gstreamer plugins.

---

### Post by Troll_the_Great on 2008-05-27
Ok, it works now, but how can I see the lyrics?

---

### Post by skip mcshwang on 2008-05-27
Right-click a song and choose "Information"

---

### Post by Troll_the_Great on 2008-05-27
If I chose "Informations" it says I have to install gnome-python-extras.I can't find them with my synaptic package manager.What are those and where do I find them?

---

### Post by sayakb on 2008-05-27
```
sudo apt-get install python-gnome2-extras
```

---

### Post by lazyart on 2008-05-27
Are you sure that's not python-gnome2-extras?

---

### Post by Troll_the_Great on 2008-05-27
Thanks, you are a life saviour.

---

