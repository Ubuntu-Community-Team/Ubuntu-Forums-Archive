---
title: "Software Center will not remain open"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by flunewname on 2014-01-11
e day old newbie...seems i made a mistake cut and pasting from a 2012 article entitled 25 things to do after a clean umbuntu install.  Now the Software center will not remain open. It appears to open then immediately closes.  when i run software-center, i get this screen:  see above.  

the screen shot does not cover entire text.  So I have tried to copy and paste the entire thing:  
 ```
:~$ software-center
2014-01-11 12:50:19,975 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-01-11 12:50:19,982 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2014-01-11 12:50:20,681 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-01-11 12:50:21,154 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2014-01-11 12:50:22,055 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
2014-01-11 12:50:24,724 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```


Im a bone head but I truely appreciate and help you can give.  Thanks.

---

### Post by flunewname on 2014-01-11
```
ebecca@rebecca-MM061:~$ software-center
2014-01-11 12:50:19,975 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-01-11 12:50:19,982 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2014-01-11 12:50:20,681 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-01-11 12:50:21,154 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2014-01-11 12:50:22,055 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
2014-01-11 12:50:24,724 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 271, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 450, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 439, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```

---

### Post by QIII on 2014-01-11
Hello!

I had to edit your first post.  If you are using Firefox, when you cut and paste an image directly in the text box, what is known as base64 code will appear rather than the image you expect.  To clear it, I had to go to a Windows machine and use IE or my machine would lock up.

When adding an image to your post, please use the upload functionality you can invoke by clicking the paperclip icon above the input box.  You can go to your original post, click edit and then click "Go Advanced" to use that functionality to add your image back to the original post.

Also, please enclose code in code tags.  (See link in my sig)

Thanks!

Welcome to the forums.  Hopefully someone will be along shortly to help you out.

Cheers!

---

### Post by mc4man on 2014-01-11
You should provide a link to whatever 'guide' you followed & which of the 25 things you did..
Also which release of Ubuntu you are on

---

### Post by flunewname on 2014-01-11
Thanks.  Found link on code tags.  And got it about image.

---

### Post by flunewname on 2014-01-11
I am using 12.04 LTS     Here is link to article.  [http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html](http://www.techdrivein.com/2012/06/25-things-i-did-after-installing-ubuntu.html) I did "Installed Restricted Extras"; "Updated Repositories"; "Enabled full DVD Playback"; "Enabled Show Remaining Space in Nautilus"; "Umbuntu Tweek" and tried "Deluge." It couldn't find Deluge so I figured I could look for it on Umbuntu Software Center.  Thats how i found out that I had problem.  
[Absolute Beginners Section]("http://ubuntuforums.org/showthread.php?t=2198974")
 
Hope I posted link correctly

---

### Post by mc4man on 2014-01-11
doesn't apply.

---

### Post by mc4man on 2014-01-11
You could see if fixing this helps
> SystemError: E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
Open up Software Sources > Other & delete all medibuntu entries

---

