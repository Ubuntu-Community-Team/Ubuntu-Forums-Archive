---
title: "Ubuntu 12.10 Software center don't start"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by SergeyAka on 2013-03-09
Hi!
Today I've got problem with software center, it doesn't start.
Before the bug was occur I installed by terminal some packages:
```
sudo apt-get install python-dev
```
```
sudo apt-get install libqt4-core libqt4-dev libqt4-gui qt4-dev-tools
```
I don't know is there a correlation between bug in software center and that packages.

And now if I try to launch software center I get these:
```
software-center
2013-03-10 09:28:12,468 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-03-10 09:28:12,474 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-03-10 09:28:12,616 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-03-10 09:28:12,616 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 337, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 139, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 75, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
```

Need help!

UPD. Ubuntu One doesn't start too.

---

### Post by SergeyAka on 2013-03-10
It's really strange... But after I compiled and install **PyQt** the software center began to work... 

All packeges I intalled:
sudo apt-get install python-dev
sudo apt-get install libqt4-core libqt4-dev libqt4-gui qt4-dev-tools


and compiled packeges:
sip-4.14.4
PyQt-x11-gpl-4.10
gsl-1.15

Problem solved.

---

