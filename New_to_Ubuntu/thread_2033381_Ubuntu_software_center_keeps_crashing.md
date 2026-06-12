---
title: "Ubuntu software center keeps crashing"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by savagenoble7 on 2012-07-26
I just installed Ubuntu. Everytime i try to open the software center it keeps crashing. At first it flashed a notice saying that it closed unexpectedly and asked to send an error report. I sent the report and restarted my computer. The software center still closes immediately after being opened, and now does not flash any kind of notice...

---

### Post by anewguy on 2012-07-26
What version of ubuntu did you install?  There used to be an obscure problem where the on-screen keyboard had to be set and then unset that caused things like this, but I thought that was fixed quite a while ago.

---

### Post by Bufeu on 2012-07-26
What does the crash log (**/var/log/apport.log**) says?

---

### Post by turbonerd on 2012-08-10
I have the same problem and I am getting this message:


&#10140;  ~  software-center
2012-08-10 15:23:39,428 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-08-10 15:23:39,430 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-08-10 15:23:39,600 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-08-10 15:23:39,677 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-08-10 15:23:39,873 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
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
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 273, in _build_homepage_view
    self._append_recommended_for_you()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 481, in _append_recommended_for_you
    self.recommended_for_you_panel = RecommendationsPanelLobby(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 160, in __init__
    self._try_sso_login()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 224, in _try_sso_login
    self.RECOMMENDATIONS_OPT_IN_TEXT)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 164, in get_sso_backend
    sso_class = LoginBackendDbusSSO(window_id, appname, help_text)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 48, in __init__
    'com.ubuntu.sso', '/com/ubuntu/sso/credentials')
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1

---

### Post by bulver on 2012-09-10
I have been having this problem also, running on a Compaq 6720s, with 160gb hard drive and 3gb of memory
 - the message I get is   "an error occurred, please run package menu from the right-click menu or apt-get in terminal to see what is wrong'
'Error: Opening the cache (E:read error -read (5: input/output error), E: the package lists or status file group could not be parsed or opened.  This usually means that your installed packages have unmet dependencies"
When I try to update the system freezes, the screen dims and I am unable to use the system.  The message "the application Ubuntu Software Center has closed unexpectedly
executable path  usr/share/software-center/update -software-center-channels" appears.

 In frustration, I have tried to reinstall Windows, but find that Ubuntu is preventing the re-format of the disk to NTFS

How do I overcome these difficulties?  I have used Ubuntu for some years, and never experienced anything like this.  Any advice would be greatly appreciated  Thank you

---

### Post by raja.genupula on 2012-09-10
open your terminal and type as 

 
```
sudo apt-get install -f
```

Then let us know what you got .

PS : Making your own thread will help you quickly .

---

### Post by bulver on 2012-09-10
Thanks for response - I am sorry to appear dumb, but on this version of ubuntu I can't find where to locate 'terminal'  This latest version seems much changed on the earlier versions, and I am somewhat lost!

---

### Post by NikTh on 2012-09-10
Hi , 

you can open terminal from Dash (= Ubuntu Icon , up-left . First on Launcher) and write **terminal**

or 

you can press Ctrl+Alt+t combo keys. 

If above command not working try bellow commands , with order. Please copy-paste from here to terminal for more accuracy. 

```
sudo apt-get purge software-center
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install software-center
sudo dpkg-reconfigure software-center --force
``` 

Reboot your system and see if worked. 

Thanks

---

### Post by bulver on 2012-09-10
thanks NikTh
have now got an up-to-date software collection, with no crashes, so am hopeful I can run as normal, your help greatly appreciated

Regards

---

### Post by bulver on 2012-09-11
Just a note to thank all concerned, my laptop is now running as it should be, great stuff, great site, keep up the good work

---

### Post by NikTh on 2012-09-11
> **bulver said:**
> Just a note to thank all concerned, my laptop is now running as it should be, great stuff, great site, keep up the good work

Hi , 

glad you solved it . 

Please mark the thread as solved , by clicking on Thread Tools. 

Thanks

---

### Post by Dai Griffiths on 2012-10-01
My software center worked fine on installation (12.4) but now keeps crashing.

I get this message: 
-------------------------------
"The application Ubuntu Software Center has closed unexpectedly
Executable path /usr/share/softwre-center/software-center"
-------------------------------

and, from the invalid problem report pop up
-------------------------------
"Could not determine the package or source package name.s"
-------------------------------

I have checked the path and there is a missing "a" in "softwre-center". I have no idea how this has come about.

Is there some way that I can edit this, so that the Software Center looks in the right place?

Many thanks

Dai

---

