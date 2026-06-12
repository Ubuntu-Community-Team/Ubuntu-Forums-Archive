---
title: "Help installing Last.FM from Repos"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by pedersencato on 2008-07-26
Hi, 
     I'm running Kubuntu Hardy(KDE3), and wanted to add the Last.FM software. I ran:

```
wget -q http://apt.last.fm/last.fm.repo.gpg -O- | sudo apt-key add -
```

Then added:

```
deb http://apt.last.fm/ debian stable
```

to my sources.list... I then ran sudo apt-get update and tried to install the program... 

```

cato@ubuntu:~$ sudo apt-get install lastfm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  lastfm: Depends: libqt4-sql (>= 4.3.3) but it is not going to be installed
E: Broken packages


cato@ubuntu:~$ sudo apt-get install libqt4-sql
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libqt4-sql: Depends: libqt4-core (= 4.3.4-0ubuntu3) but 4.4.0-1ubuntu5~hardy1 is to be installed
E: Broken packages


cato@ubuntu:~$ sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Does anyone know what the problem is? My guess is that it's a problem with the version of that libqt4, I just don't know what to do about it.

Thanks in advance.

---

### Post by tamoneya on 2008-07-26
lets try to clean stuff up:```
sudo apt-get update
sudo apt-get clean
sudo apt-get check
sudo apt-get install lastfm
```

---

### Post by CatKiller on 2008-07-26
Whilst I certainly wouldn't say you shouldn't install whatever software you want, I find that Amarok's last.fm support is great, negating the need to install the last.fm client.

However, the packages seem to have been prepared with older releases in mind. Hence the Gutsy .deb that they have available, and the = rather than >= dependency declaration.

If you'd like the client, you could get the source code and compile the client yourself. You'll need **build-essential**, and using **checkinstall** to install it will create and install a package automatically so that uninstallation and updates are easy.

Otherwise, it might be possible to force the package to install with the newer library.

---

