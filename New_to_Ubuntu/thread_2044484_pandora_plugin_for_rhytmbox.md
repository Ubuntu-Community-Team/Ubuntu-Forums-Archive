---
title: "pandora plugin for rhytmbox"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by Arendyl on 2012-08-19
Can somebody give me step-by-step instructions on how to install this plugin? please and thank you.
[https://github.com/mzheng/rhythmbox-pandora/downloads](https://github.com/mzheng/rhythmbox-pandora/downloads)

---

### Post by ubudog on 2012-08-19
[Download]("https://github.com/mzheng/rhythmbox-pandora/zipball/master") the zip and place it in your home directory.  Open a terminal and run:
```
mkdir pandoraplugin; cp mzheng-rhythmbox-pandora-1d03068.zip pandoraplugin && cd pandoraplugin; unzip mzheng-rhythmbox-pandora-1d03068.zip && chmod +x setup.sh && ./setup.sh
```

That should do it, post back if you get any errors.  :)

---

### Post by Arendyl on 2012-08-19
> **ubudog said:**
> [Download]("https://github.com/mzheng/rhythmbox-pandora/zipball/master") the zip and place it in your home directory.  Open a terminal and run:
```
mkdir pandoraplugin; cp mzheng-rhythmbox-pandora-1d03068.zip pandoraplugin && cd pandoraplugin; unzip mzheng-rhythmbox-pandora-1d03068.zip && chmod +x setup.sh && ./setup.sh
```

That should do it, post back if you get any errors.  :)
Error: 
```
 arendyl@Arlithen:~$ mkdir pandoraplugin; cp mzheng-rhythmbox-pandora-1d03068.zip pandoraplugin && cd pandoraplugin; unzip mzheng-rhythmbox-pandora-1d03068.zip && chmod +x setup.sh && ./setup.sh
Archive:  mzheng-rhythmbox-pandora-1d03068.zip
1d03068a80dff2f4a3002bda0988d8d79b1a8740
   creating: mzheng-rhythmbox-pandora-1d03068/
 extracting: mzheng-rhythmbox-pandora-1d03068/.gitignore  
  inflating: mzheng-rhythmbox-pandora-1d03068/README.rst  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora-prefs.ui  
 extracting: mzheng-rhythmbox-pandora-1d03068/plugin/pandora.png  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora.rb-plugin  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/PandoraConfigureDialog.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/PandoraSource.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/__init__.py  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/DeleteDialog.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/DeleteDialog.ui  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/SearchDialog.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/SearchDialog.ui  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/SongsAction.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/StationsAction.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/actions/__init__.py  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/models/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/models/SongsModel.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/models/StationsModel.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/models/__init__.py  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/notification_icon/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/notification_icon/NotificationIcon.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/notification_icon/__init__.py  
 extracting: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/notification_icon/pandora.png  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pandora-ui.xml  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/__init__.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/gobject_worker.py  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/__init__.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/blowfish.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/fake.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/pandora.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/pandora_keys.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/pithos/pandora/xmlrpc.py  
   creating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/ErrorView.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/SongEntryView.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/StationEntryView.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/__init__.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/cellpixbufbutton.py  
  inflating: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/error_area.ui  
 extracting: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/star-off.png  
 extracting: mzheng-rhythmbox-pandora-1d03068/plugin/pandora/widgets/star-on.png  
  inflating: mzheng-rhythmbox-pandora-1d03068/setup.sh  
chmod: cannot access `setup.sh': No such file or directory
arendyl@Arlithen:~/pandoraplugin$ 

```

---

### Post by ubudog on 2012-08-19
Oops, do:
```
cd ~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068
```

And then:
```
chmod +x setup.sh; ./setup.sh
```

---

### Post by Arendyl on 2012-08-19
it appeared to install, but its not showing up on the plugin list in rhythmbox.
```
 arendyl@Arlithen:~$ cd ~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068
arendyl@Arlithen:~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068$ chmod +x setup.sh; ./setup.sh
`./plugin/pandora' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora'
`./plugin/pandora/widgets' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets'
`./plugin/pandora/widgets/star-on.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/star-on.png'
`./plugin/pandora/widgets/ErrorView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/ErrorView.py'
`./plugin/pandora/widgets/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/__init__.py'
`./plugin/pandora/widgets/error_area.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/error_area.ui'
`./plugin/pandora/widgets/star-off.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/star-off.png'
`./plugin/pandora/widgets/cellpixbufbutton.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/cellpixbufbutton.py'
`./plugin/pandora/widgets/StationEntryView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/StationEntryView.py'
`./plugin/pandora/widgets/SongEntryView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/SongEntryView.py'
`./plugin/pandora/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/__init__.py'
`./plugin/pandora/pandora-ui.xml' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pandora-ui.xml'
`./plugin/pandora/PandoraSource.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/PandoraSource.py'
`./plugin/pandora/PandoraConfigureDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/PandoraConfigureDialog.py'
`./plugin/pandora/notification_icon' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon'
`./plugin/pandora/notification_icon/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/__init__.py'
`./plugin/pandora/notification_icon/NotificationIcon.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/NotificationIcon.py'
`./plugin/pandora/notification_icon/pandora.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/pandora.png'
`./plugin/pandora/pithos' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos'
`./plugin/pandora/pithos/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/__init__.py'
`./plugin/pandora/pithos/pandora' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora'
`./plugin/pandora/pithos/pandora/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/__init__.py'
`./plugin/pandora/pithos/pandora/pandora_keys.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/pandora_keys.py'
`./plugin/pandora/pithos/pandora/pandora.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/pandora.py'
`./plugin/pandora/pithos/pandora/xmlrpc.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/xmlrpc.py'
`./plugin/pandora/pithos/pandora/blowfish.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/blowfish.py'
`./plugin/pandora/pithos/pandora/fake.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/fake.py'
`./plugin/pandora/pithos/gobject_worker.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/gobject_worker.py'
`./plugin/pandora/actions' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions'
`./plugin/pandora/actions/DeleteDialog.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/DeleteDialog.ui'
`./plugin/pandora/actions/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/__init__.py'
`./plugin/pandora/actions/SongsAction.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SongsAction.py'
`./plugin/pandora/actions/SearchDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SearchDialog.py'
`./plugin/pandora/actions/DeleteDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/DeleteDialog.py'
`./plugin/pandora/actions/SearchDialog.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SearchDialog.ui'
`./plugin/pandora/actions/StationsAction.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/StationsAction.py'
`./plugin/pandora/models' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models'
`./plugin/pandora/models/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/__init__.py'
`./plugin/pandora/models/SongsModel.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/SongsModel.py'
`./plugin/pandora/models/StationsModel.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/StationsModel.py'
`./plugin/pandora.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora.png'
`./plugin/pandora-prefs.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora-prefs.ui'
`./plugin/pandora.rb-plugin' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora.rb-plugin'

```

---

### Post by ubudog on 2012-08-19
Hmm, according to [this]("http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html"), it appears Pithos needs to be installed.

```
sudo apt-get install pithos
```

After that, try installing again and checking in Rhythmbox:
```
cd ~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068; ./setup.sh
```

---

### Post by Arendyl on 2012-08-19
> **ubudog said:**
> Hmm, according to [this]("http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html"), it appears Pithos needs to be installed.

```
sudo apt-get install pithos
```

After that, try installing again and checking in Rhythmbox:
```
cd ~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068; ./setup.sh
```

I had pithos installed in its newest version before I created this thread. I ran the line anyway, gave no new updates. ```
 arendyl@Arlithen:~$ sudo apt-get install pithos
[sudo] password for arendyl: 
Sorry, try again.
[sudo] password for arendyl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pithos is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
arendyl@Arlithen:~$ cd ~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068; ./setup.sh
`./plugin/pandora' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora'
`./plugin/pandora/widgets' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets'
`./plugin/pandora/widgets/star-on.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/star-on.png'
`./plugin/pandora/widgets/ErrorView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/ErrorView.py'
`./plugin/pandora/widgets/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/__init__.py'
`./plugin/pandora/widgets/error_area.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/error_area.ui'
`./plugin/pandora/widgets/star-off.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/star-off.png'
`./plugin/pandora/widgets/cellpixbufbutton.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/cellpixbufbutton.py'
`./plugin/pandora/widgets/StationEntryView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/StationEntryView.py'
`./plugin/pandora/widgets/SongEntryView.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/widgets/SongEntryView.py'
`./plugin/pandora/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/__init__.py'
`./plugin/pandora/pandora-ui.xml' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pandora-ui.xml'
`./plugin/pandora/PandoraSource.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/PandoraSource.py'
`./plugin/pandora/PandoraConfigureDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/PandoraConfigureDialog.py'
`./plugin/pandora/notification_icon' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon'
`./plugin/pandora/notification_icon/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/__init__.py'
`./plugin/pandora/notification_icon/NotificationIcon.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/NotificationIcon.py'
`./plugin/pandora/notification_icon/pandora.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/notification_icon/pandora.png'
`./plugin/pandora/pithos' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos'
`./plugin/pandora/pithos/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/__init__.py'
`./plugin/pandora/pithos/pandora' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora'
`./plugin/pandora/pithos/pandora/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/__init__.py'
`./plugin/pandora/pithos/pandora/pandora_keys.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/pandora_keys.py'
`./plugin/pandora/pithos/pandora/pandora.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/pandora.py'
`./plugin/pandora/pithos/pandora/xmlrpc.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/xmlrpc.py'
`./plugin/pandora/pithos/pandora/blowfish.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/blowfish.py'
`./plugin/pandora/pithos/pandora/fake.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/pandora/fake.py'
`./plugin/pandora/pithos/gobject_worker.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/pithos/gobject_worker.py'
`./plugin/pandora/actions' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions'
`./plugin/pandora/actions/DeleteDialog.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/DeleteDialog.ui'
`./plugin/pandora/actions/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/__init__.py'
`./plugin/pandora/actions/SongsAction.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SongsAction.py'
`./plugin/pandora/actions/SearchDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SearchDialog.py'
`./plugin/pandora/actions/DeleteDialog.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/DeleteDialog.py'
`./plugin/pandora/actions/SearchDialog.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/SearchDialog.ui'
`./plugin/pandora/actions/StationsAction.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/actions/StationsAction.py'
`./plugin/pandora/models' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models'
`./plugin/pandora/models/__init__.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/__init__.py'
`./plugin/pandora/models/SongsModel.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/SongsModel.py'
`./plugin/pandora/models/StationsModel.py' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora/models/StationsModel.py'
`./plugin/pandora.png' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora.png'
`./plugin/pandora-prefs.ui' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora-prefs.ui'
`./plugin/pandora.rb-plugin' -> `/home/arendyl/.gnome2/rhythmbox/plugins/pandora/pandora.rb-plugin'
arendyl@Arlithen:~/pandoraplugin/mzheng-rhythmbox-pandora-1d03068$ 

```
Still nothing in the plugins list.

---

### Post by ubudog on 2012-08-19
What version of Rhythmbox are you using?

---

### Post by Arendyl on 2012-08-19
Rhythmbox 2.96 I believe. My update manager is up-to-date.

---

### Post by Arendyl on 2012-08-20
err... bump?

---

### Post by davidmohammed on 2012-08-22
The plugin you have found will not work with v2.9x versions of Rhythmbox.

I've done a quick google - I dont think anybody has updated this plugin to be compatible.

---

### Post by Petro Dawg on 2012-08-22
I too am not able to get a pandora plug in to work in rhythmbox, I get the same errors as Arendyl. 

However, Pithos works fine for what I need.

---

### Post by ubudog on 2012-08-23
Have you tried [these]("http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html") instructions?

---

### Post by Arendyl on 2012-08-23
> **ubudog said:**
> Have you tried [these]("http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html") instructions?

I tried them without luck, I'm getting tired of this problem. Thanks for the help, I guess I'll just have to get used to having two media players. Thanks for the help.

---

### Post by davidmohammed on 2012-08-24
those instructions will not work for v2.9x of rhythmbox.  I've looked at the current code for the pandora plugin.  The code base is  relatively large and will take a few days/weeks to port to GTK3.

Might be a nice project for someone with some time on their hands...

---

### Post by Arendyl on 2012-08-24
> **davidmohammed said:**
> those instructions will not work for v2.9x of rhythmbox.  I've looked at the current code for the pandora plugin.  The code base is  relatively large and will take a few days/weeks to port to GTK3.

Might be a nice project for someone with some time on their hands...

Can I upgrade/downgrade my current version of RhythmBox? Instructions?

---

### Post by davidmohammed on 2012-08-25
I'm not aware of any PPA that has an older version of rhythmbox.

Thus - no - not easily.

You could try to compile - again, I'm not aware of anyone trying this on precise.  You could get the Natty source and try to compile.  Doubtful this will work though given the changes between 12.04 and 11.04.  I gave it a quick try - no joy - lots of issues with libraries.

---

