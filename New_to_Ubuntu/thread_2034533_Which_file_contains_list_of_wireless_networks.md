---
title: "Which file contains list of wireless networks?"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by zozza on 2012-07-28
What text file contains the list of wireless networks I have either connected to or attempted to connect to?

I want to edit it manually.

Thanks.

---

### Post by Cheesehead on 2012-07-28
It's not a file. It's a directory. /etc/NetworkManager/system-connections

Each file in the directory is a separate connection.

If you change the directory by editing the file, you must restart network-manager. During the restart process, there is a chance it will overwrite your changes - those files are not really intended for direct user editing, and can be edited by NM at any time.

If you don't want to use the GUI, the correct way for another program to interact with NM's connection data is by using dbus.

For example, the following command will pull data on whichever stored connection NM has assigned as #10. Use dbus instrospection (or the d-feet application) to figure out such assignments:
```
READ THE INFORMATION OF A KNOWN/STORED ACCESS POINT
$ dbus-send --system --print-reply \
            --dest=org.freedesktop.NetworkManager \
            /org/freedesktop/NetworkManager/Settings/10 \
            org.freedesktop.NetworkManager.Settings.Connection.GetSettings
```Similarly, dbus has methods for changing various settings. Again, dbus introspection or d-feet can help you figure them out.

The dbus API for NM is at [http://projects.gnome.org/NetworkManager/developers/api/09/spec.html](http://projects.gnome.org/NetworkManager/developers/api/09/spec.html)

---

