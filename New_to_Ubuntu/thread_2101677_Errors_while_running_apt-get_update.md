---
title: "Errors while running apt-get update"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by mnmanjunath on 2013-01-05
Hi,

When i run *sudo apt-get update* in terminal I get the below errors at the end of the output:

[COLOR="DarkRed"]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures were invalid: BADSIG F1773AF13B1510FD Launchpad PPA for GNOME3 Team
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry 'non-free/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/COLOR]


Also when i run the software updater i get the below error:
[COLOR="DarkRed"]This requires installing packages from unauthenticated sources.
Details:
---------
brasero brasero-cdrkit brasero-common cups-pk-helper gir1.2-gtk-3.0 gir1.2-peas-1.0 gnome-accessibility-themes gnome-session-canberra gnome-settings-daemon gnome-themes-standard libbrasero-media3-1 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0 libcanberra-gtk3-module libcanberra-pulse libcanberra0 libgail-3-0 libgnome-control-center1 libgtk-3-0 libgtk-3-bin libgtk-3-common libnautilus-extension1a libpeas-1.0-0 libpeas-common nautilus nautilus-data python-cupshelpers system-config-printer-common system-config-printer-gnome system-config-printer-udev transmission-common transmission-gtk zenity zenity-common
[/COLOR]


I have tried the Software source server but of no use.Can anybody help me fix this problem?

regards
Manju

---

### Post by vasiliscnisrok on 2013-01-05
1) ```
sudo -e /etc/apt/sources.list
```
remove lines
[http://ppa.launchpad.net/lkjoel/](http://ppa.launchpad.net/lkjoel/)
[http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) 

2) see in /etc/apt/sources.list.d/ and remove file(s) with line 1)

3) add keys
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com `sudo apt-get update 2>&1 | grep -o '[0-9A-Z]\{16\}$' | xargs`
```

4) ```
sudo apt-get update && sudo apt-get upgrade
```

---

