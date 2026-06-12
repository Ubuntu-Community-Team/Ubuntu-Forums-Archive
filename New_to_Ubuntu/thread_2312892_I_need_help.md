---
title: "I need help"
date: 2016-02-08
forum: New to Ubuntu
---

### Post by jensen4 on 2016-02-08
My ubuntu desktop is showing this red sign it says malformed line 52 in source lists what to do?

---

### Post by howefield on 2016-02-08
You remove or fix line 52 in the file /etc/sources.list

Can you run the following terminal command and post the output back here (between code tags)

```
cat /etc/apt/sources.list
```

---

### Post by jensen4 on 2016-02-08
```
deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb [http://download.bitdefender.com/repos/deb/bitdefender](http://download.bitdefender.com/repos/deb/bitdefender) non-free
```

this is what I got after running the code.

---

### Post by howefield on 2016-02-08
In the last line there should be a space before the word bitdefender, so the line should look like..

```
deb http://download.bitdefender.com/repos/deb/ bitdefender non-free
```

Do you know how to do that ?

You could use the following..

```
sudo apt edit-sources
``` (select the default option 2)

Scroll down to the last line and put a space between the / and the word bitdefender.

Then Ctrl + o to write the file, press enter and then Ctrl + x to close out.

---

### Post by jensen4 on 2016-02-08
File Name to Write: /etc/apt/sources.list                                       
^G Get Help         M-D DOS Format      M-A Append          M-B Backup File
^C Cancel           M-M Mac Format      M-P Prepend         ^T To Files

 
This is what I got after pressing Ctrl + o I already seperate the / to the word bitdefender. What's next? Thank you.

---

### Post by howefield on 2016-02-08
Not sure how you got the above but if you have successfully modified and saved the file, you should be able to carry on presumably to update and install whatever it is you were going to.

If you didn't successfully amend the file, it might be easier for you to do it graphically with

```
sudo -H gedit /etc/apt/sources.list
```

---

### Post by jensen4 on 2016-02-08
Ok it's all good how do I update my system?

Nvm my system is up to date. My problem now is the red sign on the top right is still there. Should I restart my system?

Oh I have another problem whenever I open Ubuntu software center it always close on its own. :(

---

### Post by howefield on 2016-02-08
> **jensen4 said:**
> ...Nvm my system is up to date. My problem now is the red sign on the top right is still there. Should I restart my system?

Oh I have another problem whenever I open Ubuntu software center it always close on its own. :(

A screenshot of the "red sign" might help.

I don't use the Software Centre, (preferring a mixture of synaptic package manager but mostly the terminal). Try opening the Software Centre from the command line, you might get some clues as to what is it complaining about.,

```
software-center
```

---

### Post by jensen4 on 2016-02-08
The red sign is circle it has a one horizontal white bar on it.  ```
2016-02-08 19:37:17,730 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled 2016-02-08 19:37:17,782 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None' 2016-02-08 19:37:18,056 - softwarecenter.ui.gtk3.app - INFO - building local database 2016-02-08 19:37:18,056 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() 2016-02-08 19:37:21,672 - softwarecenter.db.update - WARNING - Problem creating rebuild path '/var/cache/software-center/xapian_rb'. 2016-02-08 19:37:21,673 - softwarecenter.db.update - WARNING - Please check you have the relevant permissions. 2016-02-08 19:37:22,753 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file 2016-02-08 19:37:22,755 - softwarecenter.plugin - INFO - activating plugin '' 2016-02-08 19:37:22,803 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open() /usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:584: Warning: Source ID 78 was not found when attempting to remove it   return super(MainContext, self).iteration(may_block) Traceback (most recent call last):   File "/usr/bin/software-center", line 183, in      app.run(args)   File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1378, in run     self.show_available_packages(args)   File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1316, in show_available_packages     self.view_manager.set_active_view(ViewPages.AVAILABLE)   File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view     view_widget.init_view()   File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 193, in init_view     SoftwarePane.init_view(self)   File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 138, in init_view     self.icons, self.show_ratings)   File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appview.py", line 71, in __init__     self.helper = AppPropertiesHelper(db, cache, icons)   File "/usr/share/software-center/softwarecenter/ui/gtk3/models/appstore2.py", line 112, in __init__     self.all_categories = cat_parser.parse_applications_menu()   File "/usr/share/software-center/softwarecenter/db/categories.py", line 277, in parse_applications_menu     category = self._parse_menu_tag(child)   File "/usr/share/software-center/softwarecenter/db/categories.py", line 473, in _parse_menu_tag     query = self._parse_include_tag(element)   File "/usr/share/software-center/softwarecenter/db/categories.py", line 431, in _parse_include_tag     xapian.Query.OP_AND)   File "/usr/share/software-center/softwarecenter/db/categories.py", line 368, in _parse_and_or_not_tag     operator_elem, xapian.Query(), xapian.Query.OP_OR)   File "/usr/share/software-center/softwarecenter/db/categories.py", line 414, in _parse_and_or_not_tag     q = self.db.xapian_parser.parse_query(s,   File "/usr/share/software-center/softwarecenter/db/database.py", line 185, in xapian_parser     xapian_parser = self._get_new_xapian_parser()   File "/usr/share/software-center/softwarecenter/db/database.py", line 211, in _get_new_xapian_parser     xapian_parser.set_database(self.xapiandb)   File "/usr/share/software-center/softwarecenter/db/database.py", line 177, in xapiandb     self._db_per_thread[thread_name] = self._get_new_xapiandb()   File "/usr/share/software-center/softwarecenter/db/database.py", line 190, in _get_new_xapiandb     xapiandb = xapian.Database(self._db_pathname)   File "/usr/lib/python2.7/dist-packages/xapian/__init__.py", line 3667, in __init__     _xapian.Database_swiginit(self,_xapian.new_Database(*args)) xapian.DatabaseOpeningError: Couldn't detect type of database
```  This is what I got after typing it. It's still closing on its own.

---

### Post by howefield on 2016-02-08
Not sure about the Software Centre not being a user of it, but you might have a look at the steps here

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_10_Ubuntu_Software_Center_fails_to_open](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_10_Ubuntu_Software_Center_fails_to_open)

---

### Post by jensen4 on 2016-02-08
Oh wow I just use the code : sudo update-software-center  Thank you for your time! :) I'm so happy now. It worked!

---

### Post by howefield on 2016-02-08
Cool, well done on sussing it out.. :) and presumably the "error" icon is gone also ?

---

