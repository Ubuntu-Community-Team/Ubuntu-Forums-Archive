---
title: "my ubuntusoftware link isnt working properly"
date: 2022-10-25
forum: New to Ubuntu
---

### Post by phillip1882 on 2022-10-25
i just fresh installed ubuntu, and the ubuntu software app isn't working properly, all the categories, when i click on them are blank.
i just see a large white square with three large dots in the middle.

---

### Post by Impavidus on 2022-10-25
Have you installed all available updates?

---

### Post by phillip1882 on 2022-10-25
all except snaps which can't seem to install.
i get the error
unable to update "snapStore":
 (null):cannot refresh "Snap-Store": snap "snap-store" has running apps (ubuntu-software), pid:1866

---

### Post by phillip1882 on 2022-10-25
i went into terminal and ran sudo apt-get update and it installed an approximate 433 files.
then it asked me to restart my cpu, and when i tried i got the following error
incorrect permissions on usr/lib/policykit-1/polkit-agent-helper-1 (needs to be retuid root)
it give me an option to authenticate, but its unclickable.

---

### Post by phillip1882 on 2022-10-25
ok i was able to restart, but i still have the same problem of white block with 3 dots

---

### Post by westie457 on 2022-10-26
Take look at this [https://askubuntu.com/questions/1412575/pending-update-of-snap-store](https://askubuntu.com/questions/1412575/pending-update-of-snap-store)

At best it should fix your issue, at worst it might not do anything to help you.

---

### Post by phillip1882 on 2022-10-26
i get
sorry, something went wrong:
Error calling StartServiceByName for
org.freedesktop.fwupd: failed to activate service
'org.freedesktop.fwupd':timed out
(service_start_timeout=25000ms)

---

### Post by tea for one on 2022-10-26
Can you open a terminal and enter:-
```
snap-store
```
Copy and paste within code tags any error messages.

---

### Post by phillip1882 on 2022-10-26
i get
Failed to load module "canberra-gtk-module"
Failed to load module "canberra-gtk-module"

---

### Post by zebra2 on 2022-10-26
sudo apt-get install libcanberra-gtk-module

---

### Post by Dennis N on 2022-10-26
> **phillip1882 said:**
> i get
Failed to load module "canberra-gtk-module"
Failed to load module "canberra-gtk-module"

I don't have **libcanberra-gtk-module** installed and Ubuntu Software works correctly (Ubuntu 22.04). So that error is puzzling.

I would refresh all snap packages with **snap refresh**. That may help.

_Last resort:_
If problems remain, you can use Gnome Software instead of Ubuntu Software by installing: 
**gnome-software** 
**gnome-software-plugin-snap**
**gnome-software-plugin-flatpak**
Gnome Software is NOT a snap. Its icon is labeled "Software".
The same .deb and snap packages are available as in Ubuntu Software.

---

### Post by phillip1882 on 2022-10-26
i get
```
phillip1882@phillip-SPN:~/Desktop$ snap refresh
snap-store 41.3-64-g512c0ff from Canonical&#10003; refreshed
phillip1882@phillip-SPN:~/Desktop$ snap-store
Warning: Schema “org.gnome.system.locale” has path “/system/locale/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy” has path “/system/proxy/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.http” has path “/system/proxy/http/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.https” has path “/system/proxy/https/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.ftp” has path “/system/proxy/ftp/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
Warning: Schema “org.gnome.system.proxy.socks” has path “/system/proxy/socks/”.  Paths starting with “/apps/”, “/desktop/” or “/system/” are deprecated.
18:18:35:0886 Gtk Failed to load module "canberra-gtk-module"
18:18:35:0897 Gtk Failed to load module "canberra-gtk-module"
18:19:01:0074 Gs  plugin fwupd took 25.0 seconds to do setup
18:19:02:0353 Gs  plugin appstream took 1.3 seconds to do setup
18:19:02:0690 Gs  /etc/PackageKit/Vendor.conf file not found
18:19:28:0007 Gs  can't reliably fixup error code 20 in domain g-dbus-error-quark
18:19:28:0007 Gs  not handling error failed for action refresh: Error calling StartServiceByName for org.freedesktop.fwupd: Failed to activate service 'org.freedesktop.fwupd': timed out (service_start_timeout=25000ms)
18:19:28:0007 Gs  can't reliably fixup error code 20 in domain g-dbus-error-quark
18:19:28:0008 Gs  not handling error failed for action get-updates-historical: Error calling StartServiceByName for org.freedesktop.fwupd: Failed to activate service 'org.freedesktop.fwupd': timed out (service_start_timeout=25000ms)
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.Builder.desktop/* to plugin cache
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.Calculator.desktop/* to plugin cache
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.clocks.desktop/* to plugin cache
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.Dictionary.desktop/* to plugin cache
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.Documents.desktop/* to plugin cache
18:19:36:0547 Gs  adding wildcard app */*/*/org.gnome.Evince/* to plugin cache
18:19:36:0548 Gs  adding wildcard app */*/*/org.gnome.gedit.desktop/* to plugin cache
18:19:36:0548 Gs  adding wildcard app */*/*/org.gnome.Maps.desktop/* to plugin cache
18:19:36:0548 Gs  adding wildcard app */*/*/org.gnome.Weather/* to plugin cache
18:19:36:0551 Gs  Only 0 apps for recent list, hiding
18:19:47:0424 Gs  no desktop_groups for all
18:20:02:0326 Gs  can't reliably fixup error code 20 in domain g-dbus-error-quark
```

---

### Post by Dennis N on 2022-10-26
This is too much to untangle. I would proceed to the **Last Resort** given in post #11 and you can then move on.

---

### Post by grahammechanical on 2022-10-26
> i just see a large white square with three large dots in the middle.

I get something similar. I just click on the background and the squares get updated.

Regards

---

### Post by phillip1882 on 2022-10-26
that works for me too, though i'm still getting error messages.

---

