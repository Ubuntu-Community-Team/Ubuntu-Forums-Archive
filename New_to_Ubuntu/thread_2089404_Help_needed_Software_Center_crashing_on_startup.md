---
title: "Help needed: Software Center crashing on startup"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by NZJonathan on 2012-11-29
I'm very new to Ubuntu, only installed it today, and I'm having a problem. I attempted to install the application TeamViewer, although during installation within the software center, my laptop died (my fault, there).

Now, whenever I attempt to attempt to boot the Software Center, it crashes almost instantly. 

I've tried to reinstall, but I get this error:
E: The package teamviewer7 needs to be reinstalled, but I can't find an archive for it.

Any help would be much appreciated.

---

### Post by airplanesimen on 2012-11-29
Do ```
 sudo software-center
``` in your terminal, and copy what it says in that terminal in here, so we can have a closer look on your problem.

---

### Post by NZJonathan on 2012-11-29
> **airplanesimen said:**
> Do ```
 sudo software-center
``` in your terminal, and copy what it says in that terminal in here, so we can have a closer look on your problem.
Hope this is what you wanted.

```
2012-11-29 23:10:19,636 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-11-29 23:10:21,325 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_2012-11-29 23:10:19,636 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-11-29 23:10:21,325 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-11-29 23:10:22,540 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2012-11-29 23:10:22,645 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-11-29 23:10:22,679 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-11-29 23:10:22,679 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2012-11-29 23:10:22,864 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-11-29 23:10:22,870 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package teamviewer7 needs to be reinstalled, but I can't find an archive for it.
2012-11-29 23:10:24,186 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 173, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 324, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 119, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 253, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 238, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
agent=True
2012-11-29 23:10:22,540 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2012-11-29 23:10:22,645 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-11-29 23:10:22,679 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-11-29 23:10:22,679 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2012-11-29 23:10:22,864 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-11-29 23:10:22,870 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package teamviewer7 needs to be reinstalled, but I can't find an archive for it.
2012-11-29 23:10:24,186 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 173, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 324, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 119, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 253, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 238, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

---

### Post by howefield on 2012-11-29
Try this in your terminal

```
sudo apt-get -f install
```

---

### Post by NZJonathan on 2012-11-29
> **howefield said:**
> Try this in your terminal

```
sudo apt-get -f install
```

I get this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package teamviewer7 needs to be reinstalled, but I can't find an archive for it.

And it doesn't fix the problem.

---

### Post by airplanesimen on 2012-11-29
-f  Attempt to correct a system with broken dependencies in place

does the manual say, so try this:

```
sudo apt-get -f install
```

okay, try to use

```
sudo apt-get autoremove
```

then go here and try to download:
[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

---

### Post by NZJonathan on 2012-11-29
> **airplanesimen said:**
> -f  Attempt to correct a system with broken dependencies in place

does the manual say, so try this:

```
sudo apt-get -f install
```okay, try to use

```
sudo apt-get autoremove
```then go here and try to download:
[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

```
sudo apt-get autoremove 
``` again just gave me this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package teamviewer7 needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by airplanesimen on 2012-11-29
Try the link i gave you. download the file and install teamveiwer from it.

[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

---

### Post by NZJonathan on 2012-11-29
> **airplanesimen said:**
> Try the link i gave you. download the file and install teamveiwer from it.

[http://www.teamviewer.com/download/teamviewer_linux.deb](http://www.teamviewer.com/download/teamviewer_linux.deb)

I tried this, and the software center didn't crash, but seems to have frozen at this stage:
(Hope the image worked)

---

### Post by airplanesimen on 2012-11-29
show me the output from terminal now, usin "sudo software-center"

oh, wait, what is the "stop" sign on your unity saying? Tell me, it could be a solution

---

### Post by NZJonathan on 2012-11-29
> **airplanesimen said:**
> show me the output from terminal now, usin "sudo software-center"

oh, wait, what is the "stop" sign on your unity saying? Tell me, it could be a solution

Ah, I didn't see that:

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what's wrong. The error message was: ' Unknown Error '<type 'exceptions.SystemError'>' (E:The package teamviewer7 needs to be reinstalled, but I can't find the archive for it.)'. This usually means that your installed packages have unmet dependencies."

---

### Post by airplanesimen on 2012-11-29
Do ```
 apt-get 
``` in your terminal, and look. if it is the same, i suggest you to try ```
sudo apt-get remove teamviewer7
```

i am out of ideas really :/ if you are able to remove, try to install it again :P

---

