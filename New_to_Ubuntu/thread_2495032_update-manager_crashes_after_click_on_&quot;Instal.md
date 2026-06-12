---
title: "update-manager crashes after click on &quot;Install now&quot; button"
date: 2024-02-05
forum: New to Ubuntu
---

### Post by maketopsite on 2024-02-05
Ubuntu 22.04, IceWM.

```
maketopsite@maketopsite:~$ update-manager 
Gtk-Message: 18:32:57.533: Failed to load module "xapp-gtk3-module"
Gtk-Message: 18:32:57.533: Failed to load module "appmenu-gtk-module"
WARNING:root:can not import unity GI Namespace Dbusmenu not available

```

```

Feb 04 18:39:08 maketopsite org.debian.apt[2361]: 18:39:08 AptDaemon.Worker [INFO]: Committing packages: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('>
Feb 04 18:39:08 maketopsite AptDaemon.Worker[2361]: INFO: Committing packages: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('linux-headers-5.15.0-92-ge>
Feb 04 18:39:08 maketopsite org.debian.apt[2361]: 18:39:08 AptDaemon.Worker [WARNING]: An additional step to open the cache is required
Feb 04 18:39:08 maketopsite AptDaemon.Worker[2361]: WARNING: An additional step to open the cache is required
Feb 04 18:39:07 maketopsite org.debian.apt[2361]: 18:39:07 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/f01c01c5fe904899abadc99a87e0b49f
Feb 04 18:39:07 maketopsite AptDaemon.Worker[2361]: INFO: Simulating trans: /org/debian/apt/transaction/f01c01c5fe904899abadc99a87e0b49f
Feb 04 18:39:07 maketopsite org.debian.apt[2361]: 18:39:07 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/f01c01c5fe904899abadc99a87e0b49f
Feb 04 18:39:07 maketopsite AptDaemon.Trans[2361]: INFO: Queuing transaction /org/debian/apt/transaction/f01c01c5fe904899abadc99a87e0b49f
Feb 04 18:39:07 maketopsite org.debian.apt[2361]: 18:39:07 AptDaemon [INFO]: CommitPackages() was called: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String(>
Feb 04 18:39:07 maketopsite AptDaemon[2361]: INFO: CommitPackages() was called: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('linux-headers-5.15.0-92-g>
Feb 04 18:39:01 maketopsite CRON[4706]: pam_unix(cron:session): session closed for user root
Feb 04 18:39:01 maketopsite CRON[4707]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Feb 04 18:39:01 maketopsite CRON[4706]: pam_unix(cron:session): session opened for user root(uid=0) by (uid=0)


```

Any idea please ?

---

### Post by MAFoElffen on 2024-02-05
Did you install icewm from the Jammy repo's?

What happens if you do (instead):
```

update-manager -c

```

---

### Post by maketopsite on 2024-02-06
> **MAFoElffen said:**
> Did you install icewm from the Jammy repo's?

What happens if you do (instead):
```

update-manager -c

```

I did not specify any repo so I suppose default was used.

It did not help:
```
maketopsite@maketopsite:~$ update-manager -c
Gtk-Message: 07:08:40.411: Failed to load module "xapp-gtk3-module"
Gtk-Message: 07:08:40.412: Failed to load module "appmenu-gtk-module"
WARNING:root:can not import unity GI Namespace Dbusmenu not available


```

```
root@maketopsite:/home/maketopsite# journalctl -r 
Feb 06 07:10:20 maketopsite systemd[1]: systemd-timedated.service: Deactivated successfully.
Feb 06 07:10:05 maketopsite org.debian.apt[2849]: 07:10:05 AptDaemon.Worker [INFO]: Committing packages: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('>
Feb 06 07:10:05 maketopsite AptDaemon.Worker[2849]: INFO: Committing packages: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('linux-headers-5.15.0-92-generic#a>
Feb 06 07:10:05 maketopsite org.debian.apt[2849]: 07:10:05 AptDaemon.Worker [WARNING]: An additional step to open the cache is required
Feb 06 07:10:05 maketopsite AptDaemon.Worker[2849]: WARNING: An additional step to open the cache is required
Feb 06 07:10:04 maketopsite org.debian.apt[2849]: 07:10:04 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/f0bbe93b682046c0b02d1342b47b3673
Feb 06 07:10:04 maketopsite AptDaemon.Worker[2849]: INFO: Simulating trans: /org/debian/apt/transaction/f0bbe93b682046c0b02d1342b47b3673
Feb 06 07:10:04 maketopsite org.debian.apt[2849]: 07:10:04 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/f0bbe93b682046c0b02d1342b47b3673
Feb 06 07:10:04 maketopsite AptDaemon.Trans[2849]: INFO: Queuing transaction /org/debian/apt/transaction/f0bbe93b682046c0b02d1342b47b3673
Feb 06 07:10:04 maketopsite org.debian.apt[2849]: 07:10:04 AptDaemon [INFO]: CommitPackages() was called: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('linux->
Feb 06 07:10:04 maketopsite AptDaemon[2849]: INFO: CommitPackages() was called: dbus.Array([dbus.String('linux-headers-5.15.0-92#auto'), dbus.String('linux-headers-5.15.0-92-generic#>
Feb 06 07:09:53 maketopsite snapd[3968]: storehelpers.go:791: cannot refresh snap "snapd": snap has no updates available
Feb 06 07:09:52 maketopsite udisksd[1060]: Error getting '/dev/sda11' metadata_size: The function 'bd_crypto_luks_get_metadata_size' called, but not implemented! (g-bd-init-error-qua>
```

---

### Post by ActionParsnip on 2024-02-06
```

sudo apt install xapp

```
Will remove the "xapp-gtk3-module" warning

Source:
[https://askubuntu.com/questions/1396739/failed-to-load-module-xapp-gtk3-module](https://askubuntu.com/questions/1396739/failed-to-load-module-xapp-gtk3-module)

---

### Post by ActionParsnip on 2024-02-06
```

sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module

```
[COLOR=#E8E6E3]Will remove the "[COLOR=#E8E6E3][FONT=&quot]appmenu-gtk-module[/FONT][/COLOR][COLOR=#E8E6E3]" warning

Source:
[https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module](https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module)[/COLOR][/COLOR]

---

### Post by maketopsite on 2024-02-09
> **ActionParsnip said:**
> ```

sudo apt-get install appmenu-gtk2-module appmenu-gtk3-module

```
[COLOR=#E8E6E3]Will remove the "[COLOR=#E8E6E3][FONT=&amp]appmenu-gtk-module[/FONT][/COLOR][COLOR=#E8E6E3]" warning

Source:
[https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module](https://askubuntu.com/questions/1074926/failed-to-load-module-appmenu-gtk-module-canberra-gtk-module)[/COLOR][/COLOR]

I've run Xfce, update-manager has asked for password (unlike the IceWM). I've entered it and updates were successfully installed. update-manager in IceWM works fine since then.

---

