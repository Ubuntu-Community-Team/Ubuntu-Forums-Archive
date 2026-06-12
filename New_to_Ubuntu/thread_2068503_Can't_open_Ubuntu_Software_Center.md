---
title: "Can't open Ubuntu Software Center"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by czgirb on 2012-10-09
Today, I unable to open the **Software Center** by clicking on it.
When I tried to type the following command in the Terminal, the information as follow:

> 
czgirb@czgirb:~$ gksudo software-center
2012-10-09 19:11:11,355 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-10-09 19:11:11,510 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-10-09 19:11:11,707 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-10-09 19:11:11,709 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/videolan-stable-daily-precise.list
2012-10-09 19:11:14,927 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
czgirb@czgirb:~$ 
Please guide me to solve the problem
Thank you

---

### Post by NikTh on 2012-10-09
Hi , 

I don't know for sure if this error is related to USC , but take a look at this 

> **czgirb said:**
> ```
 SystemError: E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/videolan-stable-daily-precise.list
``` 

This is an error in your sources.list. 

Give the results of ```
cat /etc/apt/sources.list.d/videolan-stable-daily-precise.list
``` 

We will fix this error and then we will see if this affected USC. 

Thanks

---

### Post by czgirb on 2012-10-09
As requested.
> czgirb@czgirb:~$ cat /etc/apt/sources.list.d/videolan-stable-daily-precise.list
deb [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) precise main
deb-src [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) precise main
ain
czgirb@czgirb:~$ 
Thank you

---

### Post by cortman on 2012-10-09
Unfortunately the quickest, easiest solution I've found for most USC problems is just reinstallation-

```
sudo apt-get install --reinstall software-center
```

And as NikTh pointed out, you want to remove that "ain" from the repository file.

---

### Post by czgirb on 2012-10-09
> **cortman said:**
> 
... as NikTh pointed out, you want to remove that "ain" from the repository file.

Would you mind for doing a favor by guiding me how to remove "ain" from the repository file?

---

### Post by NikTh on 2012-10-09
> **czgirb said:**
> Would you mind for doing a favor by guiding me how to remove "ain" from the repository file?

```
gksudo gedit /etc/apt/sources.list.d/videolan-stable-daily-precise.list
``` 

remove "ain" , save and close the file 

Then in terminal run 

```
sudo apt-get update 
``` 

and as @cortman suggested 
```
sudo apt-get install --reinstall software-center 
sudo update-software-center
``` 

If any errors occurred , post them back here.

Thanks

---

### Post by matt_symes on 2012-10-09
Hi

The quickest way to do this is, open a terminal and type (or copy and paste)

```
sudo sed -i 3d /etc/apt/sources.list.d/videolan-stable-daily-precise.list
``` Enter your password. It will not be echoed to the screen.

It will delete the third line from the file and it does need to be removed. You can check this by **cat**ting the file again.

```
cat /etc/apt/sources.list.d/videolan-stable-daily-precise.list
```

Try the software center after that.

Kind regards

---

### Post by NikTh on 2012-10-09
> **matt_symes said:**
> 

The quickest way to do this is, open a terminal and type (or copy and paste)

```
sudo sed -i 3d /etc/apt/sources.list.d/videolan-stable-daily-precise.list
``` Enter your password. It will not be echoed to the screen.

And how you know that the 3rd line is "ain" ? Maybe he copied-pasted wrong the output and 2 blank lines exists between the 2nd and "ain" 
:lolflag:

> **matt_symes said:**
> 
It will delete the third line from the file and it does need to be removed. You can check this by **cat**ting the file again.

```
cat /etc/apt/sources.list.d/videolan-stable-daily-precise.list
```Try the software center after that.

But cat command is a safety "valve" . ;)

And as I told already [here]("http://ubuntuforums.org/showthread.php?t=2067894") (post #15) 
sed is magic :)

---

### Post by matt_symes on 2012-10-10
Hi

> **NikTh said:**
> And how you know that the 3rd line is "ain" ? Maybe he copied-pasted wrong the output and 2 blank lines exists between the 2nd and "ain" 
:lolflag:



I have seen this error a number of times so experience helps here :)

The output of the cat command showed the third line was 'ain' and the error from software centers traceback also highlighted 'ain' as an error. This really does point to it being an error.

sed is not so arcane when you understand it. I'll explain what that command i posed does for you.

```
sudo sed -i 3d /etc/apt/sources.list.d/videolan-stable-daily-precise.list
```sudo => To edit the ppa file requires elevated privileges.
sed   => The sed command.
-i       => In place edit. Make changes to the actual file.
3d     => Delete the third line from the file.
lastly => The name of the file to edit.

As i stated, that file does need to be edited to remove that errant line. It may, and could well, not be the only problem but it is a problem that does need to be fixed.

> 
But cat command is a safety "valve" . ;)

And as I told already [here]("http://ubuntuforums.org/showthread.php?t=2067894") (post #15) 
sed is magic :)There are many good tutorials on the net for sed and, i agree, cat is a good way to check the changes made to a file along with the less command for larger files. 

I hope i have helped clarify my post as i am only here to help :D

Kind regards

---

