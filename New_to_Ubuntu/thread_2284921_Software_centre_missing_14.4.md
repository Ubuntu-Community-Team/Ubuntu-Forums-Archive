---
title: "Software centre missing 14.4"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by dylanthomas1 on 2015-07-02
Hi I have been using ubuntu for years and updated to 14.4 last year but over the last couple of months I have been having problems but the two main ones are that I cant open the Software centre and Flash is not working any more

I have gone into Terminal and typed Software-centre and it opened then it shut down and I got this which means nothing to me apart form it mentions Dropbox which is another program I am having problems with.

How can I fix it?

```
dylan@Spandex:~$ software-center
2015-07-02 10:32:06,756 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-07-02 10:32:08,921 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-07-02 10:32:08,929 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-07-02 10:32:09,088 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-07-02 10:32:10,508 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-07-02 10:32:10,509 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 74 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_trusty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
2015-07-02 10:32:16,932 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1378, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1316, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 227, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 326, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 121, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 255, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 240, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
dylan@Spandex:~$ Traceback (most recent call last):
  File "/usr/share/software-center/update-software-center-agent", line 81, in <module>
    cache = apt.Cache(memonly=True)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_trusty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
```

---

### Post by plucky on 2015-07-02
> SystemError: E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_trusty_main_i18n_Tr anslation-en, E:The package lists or status file could not be parsed or opened.

Open the "Software & Updates" application and disable the Dropbox Repository.

Then open a terminal and run ```
sudo rm -rf /var/lib/apt/lists/*
```

Then run ```
sudo apt-get update
``` and if no errors,see if Software Centre now opens.

Good Luck

---

### Post by dylanthomas1 on 2015-07-02
Plucky 

That rocks thanks so much I was pulling my hair out trying to work out how to sort it. It has also sorted out the Dropbox problem and also the software updater is now running again so I dont have to use the terminal to update.


THANKS!

---

