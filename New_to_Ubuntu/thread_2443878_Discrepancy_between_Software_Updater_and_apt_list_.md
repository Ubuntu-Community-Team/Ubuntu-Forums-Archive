---
title: "Discrepancy between Software Updater and apt list --upgradable"
date: 2020-05-21
forum: New to Ubuntu
---

### Post by rawthey on 2020-05-21
Today I had a notice on my desktop advising that some updates were ready, I allowed it to apply the updates and rebooted.

After rebooting I ran Software Updater and it confirmed that no further updates were needed.

I then ran 'apt list --upgradable' and got a list of 27 upgradable packages
> Listing...
evolution-data-server-common/focal-updates,focal-updates 3.36.2-0ubuntu1 all [upgradable from: 3.36.1-2]
evolution-data-server/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
fonts-opensymbol/focal-updates,focal-updates 2:102.11+LibO6.4.3-0ubuntu0.20.04.1 all [upgradable from: 2:102.11+LibO6.4.2-0ubuntu3]
gnome-settings-daemon-common/focal-updates,focal-updates 3.36.1-0ubuntu1 all [upgradable from: 3.36.0-1ubuntu2]
gnome-settings-daemon/focal-updates 3.36.1-0ubuntu1 amd64 [upgradable from: 3.36.0-1ubuntu2]
gnome-shell-common/focal-updates,focal-updates 4.36.2-1ubuntu1~20.04.1 all [upgradable from: 3.36.1-5ubuntu2]
gnome-shell-extension-prefs/focal-updates 3.36.2-1ubuntu1~20.04.1 amd64 [upgradable from: 3.36.1-5ubuntu2]
gnome-shell/focal-updates 3.36.2-1ubuntu1~20.04.1 amd64 [upgradable from: 3.36.1-5ubuntu2]
libcamel-1.2-62/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libebackend-1.2-10/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libebook-1.2-20/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libebook-contacts-1.2-3/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libecal-2.0-1/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libedata-book-1.2-26/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libedata-cal-2.0-1/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libedataserver-1.2-24/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
libedataserverui-1.2-2/focal-updates 3.36.2-0ubuntu1 amd64 [upgradable from: 3.36.1-2]
liblirc-client0/focal-updates 0.10.1-6.1ubuntu1.1 amd64 [upgradable from: 0.10.1-6.1]
libnautilus-extension1a/focal-updates 1:3.36.2-0ubuntu1 amd64 [upgradable from: 1:3.36.1.1-1ubuntu2]
libsmbclient/focal-updates 2:4.11.6+dfsg-0ubuntu1.2 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.1]
libwbclient0/focal-updates 2:4.11.6+dfsg-0ubuntu1.2 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.1]
nautilus-data/focal-updates,focal-updates 1:3.36.2-0ubuntu1 all [upgradable from: 1:3.36.1.1-1ubuntu2]
nautilus/focal-updates 1:3.36.2-0ubuntu1 amd64 [upgradable from: 1:3.36.1.1-1ubuntu2]
python3-distupgrade/focal-updates,focal-updates 1:20.04.19 all [upgradable from: 1:20.04.18]
samba-libs/focal-updates 2:4.11.6+dfsg-0ubuntu1.2 amd64 [upgradable from: 2:4.11.6+dfsg-0ubuntu1.1]
ubuntu-release-upgrader-core/focal-updates,focal-updates 1:20.04.19 all [upgradable from: 1:20.04.18]
ubuntu-release-upgrader-gtk/focal-updates,focal-updates 1:20.04.19 all [upgradable from: 1:20.04.18]

Which should I believe?

---

### Post by VMC on 2020-05-21
From terminal try this ```
sudo apt upgrade
```, you can say 'N', to stop. Just compare to software updater.

---

### Post by &amp;KyT$0P# on 2020-05-21
> **rawthey said:**
> Which should I believe?

Both.  The discrepancy is related to [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

---

### Post by rawthey on 2020-05-21
> **VMC said:**
> From terminal try this ```
sudo apt  upgrade
```, you can say 'N', to stop. Just compare to software  updater.
```
mike@otter:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  evolution-data-server evolution-data-server-common fonts-opensymbol  gnome-settings-daemon gnome-settings-daemon-common gnome-shell
  gnome-shell-common gnome-shell-extension-prefs libcamel-1.2-62  libebackend-1.2-10 libebook-1.2-20 libebook-contacts-1.2-3 libecal-2.0-1
  libedata-book-1.2-26 libedata-cal-2.0-1 libedataserver-1.2-24  libedataserverui-1.2-2 liblirc-client0 libnautilus-extension1a  libsmbclient
  libwbclient0 nautilus nautilus-data python3-distupgrade samba-libs ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
27 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 9,612 kB/9,840 kB of archives.
After this operation, 103 kB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
Why does Software Updater say everything is up to date?

---

### Post by rawthey on 2020-05-21
> **halogen2 said:**
> Both.  The discrepancy is related to [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").
So I shouldn't worry about checking with apt list --upgradable. Software Updater will update them in due course?

---

### Post by VMC on 2020-05-21
If you run ```
sudo apt update
```, you'll get same response as software updater.
In your case I would let software updater decide.

---

