---
title: "Software centre not loading - 14.04"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by sandesh.sboa on 2014-07-08
Hey guys,

I recently moved completely from Windows 8.1 to Ubuntu 14.04 . Everything has been running fine until last week. whenever I try to open the Software centre, it opens up and closes off instantaneously. I also have a big red 'negative sign' on the right side top of my screen. I tried opening Softwre centre from the terminal and was getting this message, Could any of you guys kindly help me out with this!

Thanks,

Sandesh

The error message :
```
2014-07-08 16:10:41,758 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-07-08 16:10:42,197 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2014-07-08 16:10:42,202 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2014-07-08 16:10:42,202 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2014-07-08 16:10:42,238 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2014-07-08 16:10:42,677 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2014-07-08 16:10:42,678 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 68 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 70 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.
2014-07-08 16:10:44,743 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
```

[B]
Also[/B]

I tried reinstalling the software centre using the command sudo apt-get --purge --reinstall install software-center , it did not work either. Got the error message :

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
```

I dont understand what it is saying with respect to Spotify?

Please help me out !

---

### Post by slickymaster on 2014-07-08
Hi sandesh.sboa. I'ce edited your post adding [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to it.
Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of 'Code' tags makes the post clean, compact and more appealing, thus getting more attention from readers.

As for your problem, please try the following:```
sudo apt-get remove --purge software-center
sudo apt-get install software-center
sudo software-center &
```If you still get errors please post them back in the thread using the appropriate code tags.

---

### Post by plucky on 2014-07-08
> SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS, E:The package lists or status file could not be parsed or opened.

That will by your problem.People have been reporting problems with the Spotify repositories lately.

Open Software & Updates and disable the Spotify repository.

Then open a terminal and run ```
sudo apt-get update
```

If that runs without any errors,you should be able to open the Software Centre.

Good Luck

---

### Post by slickymaster on 2014-07-08
It seems that we were both editing your post at the same time.

But at the light of your update spotify is having some problem with their repository URL being incorrectly resolved on DNS level. As a temporary solution replace the URL in your **/etc/apt/sources.list.d/spotify.list** to read as follows```
deb http://repository-origin.spotify.com stable non-free
```
Afterwards clean the apt lists cache and update as usual:```
sudo rm /var/lib/apt/lists/*
sudo apt-get update && sudo apt-get -y upgrade
```
It should work.

---

### Post by sandesh.sboa on 2014-07-10
Hi slickymaster,

Sorry about the code tags. I'm new here and was not aware about it. Will make sure to include it in all further posts.

Hi plucky,

Thanks for the Solution. It is working now. It was indeed the problem with the Spotify repositories. I have disabled them now. 

BTW ,

The solution also exists here [http://askubuntu.com/questions/491620/problem-with-mergelist-var-lib-apt-lists-repository-spotify-com-while-updatin]("http://askubuntu.com/questions/491620/problem-with-mergelist-var-lib-apt-lists-repository-spotify-com-while-updatin")

Thanks all :)

Cheers !

---

### Post by slickymaster on 2014-07-10
No problem. Glad you got it solved.

Happy *buntuing.

---

