---
title: "just installed and have problems"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by WadeWilson on 2013-03-24
hihihi! i just installed ubuntu using widowinstaller. tried to install skype and wine but could not do it. reading few post i tried to install thru software senter but it does not open. it opens up for second and closes down and invalide problem report shows up. 
please help me.

---

### Post by fantab on 2013-03-24
You should tell us more about what "invalid" problem does it report?

You open "Terminal" (ctrl+alt+T) and run the following command:

```
$ software-center
```

Post the output here.

---

### Post by WadeWilson on 2013-03-24
after i type it it gives me this. 
2013-03-24 01:27:34,141 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-03-24 01:27:34,163 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-03-24 01:27:35,120 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-03-24 01:27:35,395 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-03-24 01:27:35,412 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Malformed line 5 in source list /etc/apt/sources.list (dist parse)
2013-03-24 01:27:39,581 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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

---

### Post by fantab on 2013-03-24
*SystemError: E:Malformed line 5 in source list /etc/apt/sources.list (dist parse)*

You have to look into you /etc/apt/sources.list, run:

```
$ cat /etc/apt/sources.list
```

and post the output here enclosed in code tags (Use # in you editor tools after selecting the pasted output).

---

### Post by WadeWilson on 2013-03-24
i get
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by fantab on 2013-03-24
Post the complete output.
From what you have posted [s]your sources look fine[/s]... there is problem in the third link...

Ok.. run:

```
$ sudo apt-get update
```

Post the output IF you see any errors, otherwise run:

```
$ sudo apt-get install skype
```

---

### Post by WadeWilson on 2013-03-24
E: Malformed line 5 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by fantab on 2013-03-24
please post the output (complete)

$ cat /etc/apt/sources.list.

---

### Post by WadeWilson on 2013-03-24
bash: cat/etc/apt/sources.list.: No such file or directory

---

### Post by fantab on 2013-03-24
$ cat /etc/apt/sources.list

there is space after "cat"

just copy paste:

cat /etc/apt/sources.list

---

### Post by WadeWilson on 2013-03-24
wow im sorry. 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by WadeWilson on 2013-03-24
thanks.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by fantab on 2013-03-24
The output I wanted to see was this:

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha amd64 (20130130)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```

So that we will know where exactly the problem is...

We will have regenerate the sources.list use this **[UTILITY]("http://repogen.simplylinux.ch/")** (When using this utility DO NOT check ANY **3rd Parties Repos**, you can select everything before that).

After you have generated the file SAVE it and name it as "sources.list"

```
$ gksu nautilus
```

Navigate to filesystem(computer)-> etc -> apt -> sources.list

right click on it and choose properties, rename the file to sources.list.backup -> ok.

Now copy the file that you have generated and save and paste it here (/etc/apt/sources.list) and name it as "sources.list"

```
$ sudo apt-get update
$ software-center
```

---

### Post by WadeWilson on 2013-03-24
ok i can not replace old sources.list document
the old document contains

# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner

---

### Post by WadeWilson on 2013-03-24
i cannot detele or replace

---

### Post by WadeWilson on 2013-03-24
trying to replace the file it says
error moving file: Permission denied

---

### Post by fantab on 2013-03-24
That is why we asked you to use "**gksu nautilus**", after that command you will prompted for your password, and Nautilus (File Manager will open with all the necessary root permissions).

You can also do the same with CLI:

```
$ sudo cp -b /etc/apt/sources.list /etc/apt/sources.list.backup
$ sudo cp -i /PATH/TO/NEW_SOURCES.LIST /etc/apt
```

After the second command you will be asked if you want to replace the file, say yes.
"Sudo" will help you become root with all the permissions to copy files.

---

### Post by WadeWilson on 2013-03-24
cp: cannot stat `PATH/TO/NEW_SOURCES.LIST': No such file or directory


do i do something wrong?

---

### Post by fantab on 2013-03-24
> **WadeWilson said:**
> cp: cannot stat `PATH/TO/NEW_SOURCES.LIST': No such file or directory


do i do something wrong?

you have to replace /Path/to/new_sources.list with the path to the generated and saved sources.list for instance, /home/Wilson/sources.list

Try again it will work.

After that:

$ sudo apt-get update

---

### Post by WadeWilson on 2013-03-24
im really sorry but can u give more details?

---

### Post by WadeWilson on 2013-03-30
okoko reinstalled ubuntu. all works tnx

---

