---
title: "Citrix Receiver install can't resolve dependencies"
date: 2019-08-28
forum: New to Ubuntu
---

### Post by gabrie on 2019-08-28
Hi,
Just freshly installed Ubuntu 19.04 on my laptop and all pending updates (not that much). First step now was to install the Citrix Receiver client since that actually is the only really important thing I need for work tomorrow. 

I downloaded icaclient_13.10.0.20_amd64.deb and tried to install it through the command line:

```
sudo dpkg -i icaclient_13.10.0.20_amd64.deb
```

This gave the following output about missing dependencies:
```
Selecting previously unselected package icaclient.
(Reading database ... 180618 files and directories currently installed.)
Preparing to unpack icaclient_13.10.0.20_amd64.deb ...
Unpacking icaclient (13.10.0.20) ...
dpkg: dependency problems prevent configuration of icaclient:
 icaclient depends on libgtk2.0-0 (>= 2.12.0); however:
  Package libgtk2.0-0 is not installed.
 icaclient depends on libwebkit-1.0-2 | libwebkitgtk-1.0-0; however:
  Package libwebkit-1.0-2 is not installed.
  Package libwebkitgtk-1.0-0 is not installed.

dpkg: error processing package icaclient (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 icaclient
```


So I ran:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  icaclient
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 52,3 MB disk space will be freed.
```

I hoped it would now solve and install the missing components, but unfortunately not. How can I get this resolved? Should I select and find each package individually?

Regards
Gabe

---

### Post by Autodave on 2019-08-29
Don't know anything about that program, but I did find this:  [https://www.citrix.com/downloads/citrix-receiver/linux/](https://www.citrix.com/downloads/citrix-receiver/linux/)

One other thing: you may have to go back to 18.04.  18.04 is a long term service (LTS) release.  The next LTS will be 20.04.  The interim releases (in my opinion) should always be regarded as beta releases: new things being tried.  Some work, some don't.

---

### Post by gabrie on 2019-09-02
> **Autodave said:**
> Don't know anything about that program, but I did find this:  [https://www.citrix.com/downloads/citrix-receiver/linux/](https://www.citrix.com/downloads/citrix-receiver/linux/)

One other thing: you may have to go back to 18.04.  18.04 is a long term service (LTS) release.  The next LTS will be 20.04.  The interim releases (in my opinion) should always be regarded as beta releases: new things being tried.  Some work, some don't.

That is the same I'm using, but I read issues everywhere on forums. Seems the packages don't get any real support and updates.

---

### Post by hutchers on 2020-01-23
I have the exact same issue. Did you make any further progress?

Thanks

---

