---
title: "how to remove brave browser"
date: 2023-07-12
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-07-12
I believe Brave browser is installed as snap version. I tried this 1st with this result
sudo apt remove brave-browser
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package brave-browser
then i tried this
sudo snap remove brave
snap "brave" is not installed
 can anyone help? thx

---

### Post by maketopsite on 2023-07-12
> **tuesdaybarrett said:**
> I believe Brave browser is installed as snap version. I tried this 1st with this result
sudo apt remove brave-browser
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package brave-browser
then i tried this
sudo snap remove brave
snap "brave" is not installed
 can anyone help? thx

```
# apt remove brave-browser
Reading package lists... Done
Construction of the dependency tree       
Reading state information... Done
The following package has been installed automatically and is no longer required:
  brave keyring
Please use “apt autoremove” to delete it.
The following packages will be REMOVED:
  brave-browser
0 updated, 0 newly installed, 1 to be removed and 0 not updated.
After this operation, 340 MB of disk space will be released.
Would you like to continue? [Y/n]
```

---

### Post by deadflowr on 2023-07-12
Did you remove it already?
How do you know it's installed?
What signs do you have that it is?

Possible installations could be

1) apt/dpkg?
could run
```
dpkg -l | grep brave
```
see if anything is listed.

2) snap?
use
```
snap list
```
see if it lists there.

3) flatpak? (does it exist as a flatpak, I would think so)
try
```
flatpak list
```
see if an entry for brave is listed.

4)appimage?
don't know how you'd search for this.
But most likely be in your Downloads folder, or somewhere else you would have downloaded it to.

5) source.
I guess you could have installed it from source, but i think you would have remember doing that.

I would think 4 and 5 you'd remember.

Not enough information to go on...

---

### Post by maketopsite on 2023-07-12
```
$ locate brave-browser
/etc/alternatives/brave-browser
/etc/apt/sources.list.d/brave-browser-release.list
/etc/apt/sources.list.d/brave-browser-release.list.distUpgrade
/etc/cron.daily/brave-browser
/etc/default/brave-browser
/usr/bin/brave-browser
/usr/bin/brave-browser-stable
/usr/share/appdata/brave-browser.appdata.xml
/usr/share/applications/brave-browser.desktop
/usr/share/doc/brave-browser
/usr/share/doc/brave-browser/changelog.gz
/usr/share/gnome-control-center/default-apps/brave-browser.xml
/usr/share/icons/hicolor/128x128/apps/brave-browser.png
/usr/share/icons/hicolor/16x16/apps/brave-browser.png
/usr/share/icons/hicolor/24x24/apps/brave-browser.png
/usr/share/icons/hicolor/256x256/apps/brave-browser.png
/usr/share/icons/hicolor/32x32/apps/brave-browser.png
/usr/share/icons/hicolor/48x48/apps/brave-browser.png
/usr/share/icons/hicolor/64x64/apps/brave-browser.png
/usr/share/keyrings/brave-browser-archive-keyring.gpg
/usr/share/keyrings/brave-browser-beta-archive-keyring.gpg
/usr/share/keyrings/brave-browser-nightly-archive-keyring.gpg
/usr/share/man/man1/brave-browser-stable.1.gz
/usr/share/man/man1/brave-browser.1.gz
/usr/share/menu/brave-browser.menu
/var/lib/apt/lists/brave-browser-apt-release.s3.brave.com_dists_stable_InRelease
/var/lib/apt/lists/brave-browser-apt-release.s3.brave.com_dists_stable_main_binary-amd64_Packages
/var/lib/dpkg/alternatives/brave-browser
/var/lib/dpkg/info/brave-browser.list
/var/lib/dpkg/info/brave-browser.md5sums
/var/lib/dpkg/info/brave-browser.postinst
/var/lib/dpkg/info/brave-browser.postrm
/var/lib/dpkg/info/brave-browser.prerm

```

---

### Post by tuesdaybarrett on 2023-07-12
went to flathub found it there and able to remove it thx for help

---

### Post by ian-weisser on 2023-07-12
Reminder: It's the human's job to keep track of which packaging method or install method was used. That means us.

Folks who use so many that they cannot recall them all might consider keeping a journal or other method of taking notes.

That little notebook has saved me many days of frustration and grief.

---

