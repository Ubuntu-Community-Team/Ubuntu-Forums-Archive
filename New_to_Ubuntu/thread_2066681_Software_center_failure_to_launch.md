---
title: "Software center failure to launch"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by BryoMcKim on 2012-10-05
My ubuntu software center has failed to open. it launches and closes  almost immediately. Some applications like netbeans also have failed to  be installed. this is what the terminal says when i try to install it.

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

________________________________________________________________________________
For software center this is what it states:

2012-10-06 11:54:09,348 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'http://proxy.ku.ac.ke:6060/'
2012-10-06 11:54:09,399 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-06 11:54:09,894 - softwarecenter.backend.reviews - WARNING -  Could not get usefulness from server, no username in config file
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 242, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem  with MergeList  /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages,  E:The package lists or status file could not be parsed or opened.
2012-10-06 11:54:11,835 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 262, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1341, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1271, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 165, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 240, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 491, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 266, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 430, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 419, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 262, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

______________________________________________________________________________________
please help. I will kindly appreciate. thanks in advance.

---

### Post by albandy on 2012-10-05
First you have to backup /var/list/apt/lists folder:
```

sudo tar zcvf ~/backup.tgz /var/list/apt/lists

```
then delete the contents of /var/list/apt/lists folder:

```

sudo rm -rf /var/list/apt/lists/*

```

now run:
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by newb85 on 2012-10-05
The tar command seems a bit excessive here.  Simply moving or renaming the folder should be sufficient.

---

### Post by sodoscar on 2012-10-05
I'm having same issue, been looking through any post I can find on the subject, tried many suggested solutions, still no fix.

As this only started occurring on my system immediately after an ubuntu update I am leaning to the possibility of some issue with the last update. 

Heres what I get:

```
sod@zeta:~$ software-center
2012-10-06 15:38:03,581 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-06 15:38:03,585 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-06 15:38:03,920 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-06 15:38:04,070 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
Killed
sod@zeta:~$ ^C

``` 

I've also tried the following: 
```

sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
```

and prior to that:

```
sod@zeta:~/.config$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sod@zeta:~/.config$ software-center
2012-10-06 15:20:44,765 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-06 15:20:44,770 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-06 15:20:45,106 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-06 15:20:45,251 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-06 15:20:45,268 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
^CKilled
sod@zeta:~/.config$ cd ..
sod@zeta:~$ sudo apt-get --reinstall software-center
E: Invalid operation software-center
sod@zeta:~$ sudo apt-get --reinstall software-center
E: Invalid operation software-center
sod@zeta:~$ sudo apt-get reinstall software-center
E: Invalid operation reinstall
sod@zeta:~$ sudo apt-get purge software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 4,417 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 196650 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing software-center ...
Purging configuration files for software-center ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
sod@zeta:~$ sudo apt-get clean
sod@zeta:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  software-center
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 622 kB of archives.
After this operation, 4,358 kB of additional disk space will be used.
Get:1 http://nz.archive.ubuntu.com/ubuntu/ precise-updates/main software-center all 5.2.6 [622 kB]
Fetched 622 kB in 1s (585 kB/s)          
Selecting previously unselected package software-center.
(Reading database ... 196208 files and directories currently installed.)
Unpacking software-center (from .../software-center_5.2.6_all.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up software-center (5.2.6) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
sod@zeta:~$ software-center
2012-10-06 15:26:27,838 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-10-06 15:26:27,842 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-06 15:26:28,189 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-06 15:26:28,332 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
Killed

```

so yeah... if any of that makes sense to any of you and you got a clue about where I go next I'm certainly keen on hearing your thoughts.

---

