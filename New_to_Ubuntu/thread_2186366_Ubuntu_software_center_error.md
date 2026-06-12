---
title: "Ubuntu software center error"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by jamesy871 on 2013-11-07
Ive been using the software enter for some time, up until now, it forces itself closed without loading the catalog! 
I get this error...

WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.
james@james-MM061:~$ software-center

** (software-center:4237): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-NsjBoLy6rX: Connection refused
2013-11-07 09:10:20,382 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-11-07 09:10:22,069 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-11-07 09:10:22,073 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-11-07 09:10:22,090 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-11-07 09:10:22,090 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-11-07 09:10:22,233 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Bus error (core dumped)


Ive tried uninstalling and re-installing by the terminal but the problem hasnt gone, could anyone advise me on a solution to this please

---

### Post by ibjsb4 on 2013-11-07
A work-a-round till you find your answer.

[http://ubuntuforums.org/showthread.php?t=2185697&p=12837980#post12837980](http://ubuntuforums.org/showthread.php?t=2185697&p=12837980#post12837980)

---

### Post by jamesy871 on 2013-11-08
thanks ill use this synaptic package manager until the problem is fixed

---

