---
title: "Ubuntu Software Center in 12.04 does not open"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by macsathish on 2012-06-03
when i start it in terminal it displays the following error
i'm a newbie i don't know much technical info
pls say as simple as possible


2012-06-03 21:10:40,921 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-06-03 21:10:40,927 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1341, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1271, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 177, in init_view
    root_category=self.cat_view.categories[0])
IndexError: list index out of range

---

### Post by raja.genupula on 2012-06-03
open your terminal and do as 
```
sudo apt-get install --reinstall software-center
``` and try again.

---

### Post by macsathish on 2012-06-03
ubuntu software does not reinstall 


Reading state information... Done
The following packages will be upgraded:
  software-center
1 upgraded, 0 newly installed, 0 to remove and 210 not upgraded.
Need to get 620 kB of archives.
After this operation, 20.5 kB disk space will be freed.
Get:1 [http://mirrors.us.kernel.org/ubuntu/](http://mirrors.us.kernel.org/ubuntu/) precise-updates/main software-center all 5.2.2.2 [620 kB]
Fetched 620 kB in 7s (86.8 kB/s)                                               
(Reading database ... 156664 files and directories currently installed.)
Preparing to replace software-center 5.2 (using .../software-center_5.2.2.2_all.deb) ...
Unpacking replacement software-center ...
dpkg: error processing /var/cache/apt/archives/software-center_5.2.2.2_all.deb (--unpack):
 trying to overwrite '/usr/share/app-install/channels', which is also in package app-install-data-partner 12.12.04.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_5.2.2.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by raja.genupula on 2012-06-03
open your terminal and do this

```
sudo -i
cd /var/cache/apt/archives
dpkg -i --force-overwrite software-center_5.2.2.2_all.deb
dpkg --configure -a
```

do the last command a few times if things not set up . 

Thanks to [http://www.linuxquestions.org/questions/debian-26/broken-apt-get-227042/](http://www.linuxquestions.org/questions/debian-26/broken-apt-get-227042/)

---

### Post by macsathish on 2012-06-04
thanks raja
it worked
once again thank you very much

---

### Post by birdie1234 on 2012-06-04
thanks raja
it worked

---

### Post by raja.genupula on 2012-06-04
you are welcome :) and thanks for marking as solved .

---

### Post by Frank Blood on 2012-11-09
Im having this issue. software center just craps out. something about a file not being able to be parsed or opened. i tried your remedy but it says that file does not exist. halp!

---

### Post by Atone410 on 2012-11-18
I am also having this issue, but your fix did not work for me. I'm running on an Asus K52N 
```
AMD Turion II P540 Dual-Core Processor
6gb memory
Mobility Radeon HD 4200 Series (display)
Storage- SB7x0?SB8x0/SB9x0 SATA Controller [ACHI mode]
Disk- ATA Disk ST95005620AS Seagate
```

Error Message:
```
hobbit@ALaptop:~$ sudo apt-get install --reinstall software-center
[sudo] password for hobbit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/622 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 207166 files and directories currently installed.)
Preparing to replace software-center 5.2.6 (using .../software-center_5.2.6_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up software-center (5.2.6) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 169, in <module>
    result = rebuild_database(pathname)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 1043, in rebuild_database
    cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 149, in open
    self._list.read_main_list()
SystemError: E:Type '--2012-11-17' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: Type '--2012-11-17' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
hobbit@ALaptop:~$ sudo -i
root@ALaptop:~# cd /var/cache/apt/archives
root@ALaptop:/var/cache/apt/archives# dpkg -i --force-overwrite software-center_5.2.2.2_all.deb
dpkg: error processing software-center_5.2.2.2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 software-center_5.2.2.2_all.deb

```

Please keep in mind I'm as new as new gets and I've been googling pretty much EVERYTHING I've read on these forums. So in lamens terms: just give me the dummies guide to the dummies guide.

---

