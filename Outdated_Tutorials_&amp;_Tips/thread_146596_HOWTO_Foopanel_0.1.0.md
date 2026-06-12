---
title: "HOWTO: Foopanel 0.1.0"
date: 2006-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Jefim on 2006-03-18
I suppose, that many of linux users heard of the [Foopanel]("http://foopanel.berlios.de/foopanel/doku.php"). Well, I saw it on gnomefiles.org and decided to try it out. There are several problems with installing this thing on breezy, so I decided to post my experience here :) 

Ok. Here goes:
(preparation phase)

1. Get the wnck.tar.gz attached to this post.

2. Crack it into any folder.

3. Overwrite files
[LIST]
[*]/usr/lib/python2.4/site-packages/gtk-2.0/wnck.so
[*]/usr/lib/python2.4/site-packages/gtk-2.0/wnck.la
[/LIST]
with files wnck.so and wnck.la you got from the attachment (the files in attachment were taken from package python2.4-gnome2-extras_2.12.1 for Debian: this fixes the problem with "ImportError: /usr/lib/python2.4/site-packages/gtk-2.0/wnck.so: undefined symbol: wnck_window_demands_attention").

4. Reqired package install:
> sudo apt-get install python2.4-dev python-vte

(installation phase)

5. Grab the latest version of Foopanel:
> wget [http://prdownload.berlios.de/foopanel/foopanel-0.1.0.tar.gz](http://prdownload.berlios.de/foopanel/foopanel-0.1.0.tar.gz)

6. Crack foopanel-0.1.0.tar.gz.

7. cd into folder with extracted files and
sudo python setup.py install

8. Now
> cd /usr/lib/python2.4/site-packages/foopanel/plugins
and
> mv pager ~/any_folder
(you can just delete them too. I just didn't find a way to make foopanel load this plugin, it's smth connected to wmck)

9. Run the Foopanel with the command foopanel.

---

### Post by k84 on 2006-03-25
Hi, I followed your guide step by step but when i try to run foopanel i get this error:

> Loading theme SolidBlue
Warning: Unable to load plugin 'menu'
Traceback (most recent call last):
  File "/usr/bin/foopanel", line 37, in ?
    foopanel.run()
  File "/usr/lib/python2.4/site-packages/foopanel/__init__.py", line 88, in run
    plugin_manager = core.PluginManager()
  File "/usr/lib/python2.4/site-packages/foopanel/lib/core.py", line 97, in __init__
    functions.load_plugin( plugin, settings )
  File "/usr/lib/python2.4/site-packages/foopanel/lib/functions.py", line 56, in load_plugin
    plugwidget = plugin.Plugin()
  File "/usr/lib/python2.4/site-packages/foopanel/plugins/menu/__init__.py", line 317, in __init__
    obj = menu(m)
  File "/usr/lib/python2.4/site-packages/foopanel/plugins/menu/__init__.py", line 165, in __init__
    icon = obj.getIcon()
AttributeError: MenuEntry instance has no attribute 'getIcon'

---

### Post by k84 on 2006-03-25
nevermind... I checked the code for the menu plugin and there are some missing code lines compared to the menu plugin offered from the SVN repository. It looks cool and it would be great to have more themes. The rest of the plugins work with no problems.

---

