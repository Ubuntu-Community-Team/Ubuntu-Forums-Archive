---
title: "Error, bug or something else"
date: 2021-06-10
forum: New to Ubuntu
---

### Post by wilsojeffrey on 2021-06-10
I'm a little gun shy here, as my first question on this forum was met with a face full of arrogant condescension. I'll give it another go, and hope someone else answers. First time this came up, I somehow managed to report it, but don't know if I could do it again. In response to the answer I got, I'm pretty sure I've got no hardware issues, even though this machine is old (probably ancient in computerspeak). It's other wise running as smooth as silk.
Anyway, here goes. When I try to upgrade - this happens

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 evolution : Depends: evolution-common (= 3.36.5-0ubuntu1) but 3.36.4-0ubuntu1 is to be installed
 libevolution : Depends: evolution-common (= 3.36.5-0ubuntu1) but 3.36.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by yetimon_64 on 2021-06-10
> **wilsojeffrey said:**
> ...You might want to run 'apt --fix-broken install' to correct these...

Try running the command ...
```
sudo apt --fix-broken install
```
... as suggested by the terminal output you posted if you haven't already tried such.

Post back any further terminal errors if they occur, preferably between [noparse]```

```[/noparse] tags. To do so use the "Go Advanced" option and use the "#" button to insert the code tags then copy/paste in your terminal output between them. Doing so makes it much easier for helpers to read and interpret terminal output in your posts.

Regards, yeti.

---

### Post by Impavidus on 2021-06-10
Let's see. What output does it give you when you run```
sudo apt update
sudo apt --fix-broken install
```That may give a more helpful error message.

The apt update command is to ensure your package manager has the latest information about available packages.

---

### Post by sudodus on 2021-06-10
Welcome wilsojeffrey :-)

- Which version of Ubuntu are you running (20.04.x LTS or some other version)?
- Can you think of any program package, that you have installed, that can cause a conflict with evolution?
- Did you check that the drive and the file system is healthy? See for example [this link](https://askubuntu.com/questions/1344517/is-it-a-problem-if-i-have-one-bad-sector-on-my-hdd).

- Did you try the suggested command with elevated permissions (sudo)?

```

sudo apt update
sudo apt --fix-broken install

```

and after that

```

sudo apt update
sudo apt full-upgrade

```

You may need to repeat this sequence of commands. Please try it and let us know the result.

---

### Post by wilsojeffrey on 2021-06-10
First off 
SUDO APT UPDATE

```

Hit:1 http://au.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://au.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]    
Hit:3 http://dl.google.com/linux/chrome/deb stable InRelease                  
Get:4 http://au.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]  
Hit:5 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu focal InRelease      
Get:6 http://au.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [490 kB]
Get:7 http://au.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,026 kB]
Get:8 http://au.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [283 kB]
Get:9 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]     
Hit:10 http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu focal InRelease
Get:11 http://au.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [781 kB]
Get:12 http://au.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [330 kB]
Get:13 http://au.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:14 http://au.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [1,768 B]
Hit:15 http://ppa.launchpad.net/savoury1/digikam/ubuntu focal InRelease       
Get:16 http://security.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24.5 kB]
Get:17 http://security.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [58.3 kB]
Get:18 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 3,327 kB in 2s (1,366 kB/s)                                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
14 packages can be upgraded. Run 'apt list --upgradable' to see them.



```

---

### Post by wilsojeffrey on 2021-06-10
```

sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  brasero-cdrkit catdoc cdparanoia dvdauthor k3b-data k3b-i18n keditbookmarks kio kpackagelauncherqml kpackagetool5 libepub0 libflac++6v5 libhfstospell10 libiso9660-11 libk3b7 libk3b7-extracodecs
  libkf5archive5 libkf5attica5 libkf5auth5 libkf5bookmarks-data libkf5bookmarks5 libkf5cddb-data libkf5cddb5 libkf5completion-data libkf5completion5 libkf5declarative-data libkf5declarative5
  libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kiocore5 libkf5kiofilewidgets5
  libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data libkf5package5
  libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5quickaddons5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data libkf5textwidgets5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libmusicbrainz5cc2v5 libphonon4qt5-4 libphonon4qt5-data libpoppler-qt5-1 libqt5positioning5 libqt5quickcontrols2-5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5sensors5 libqt5test5 libqt5webchannel5 libqt5webkit5 libvcdinfo0 libvoikko1 libzip5 phonon4qt5 phonon4qt5-backend-vlc qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-qtqml-models2 qml-module-qtquick-controls2 qml-module-qtquick-templates2 sonnet-plugins vcdimager
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  evolution-common
The following packages will be upgraded:
  evolution-common
1 to upgrade, 0 to newly install, 0 to remove and 13 not to upgrade.
43 not fully installed or removed.
Need to get 0 B/695 kB of archives.
After this operation, 73.7 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 235361 files and directories currently installed.)
Preparing to unpack .../evolution-common_3.36.5-0ubuntu1_all.deb ...
Unpacking evolution-common (3.36.5-0ubuntu1) over (3.36.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-common_3.36.5-0ubuntu1_all.deb (--unpack):
 failed to stat (dereference) existing symlink '/usr/share/help/sl/evolution/mail-encryption-gpg-decrypting.page': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/evolution-common_3.36.5-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by wilsojeffrey on 2021-06-10
OK. It's a mail client called Evolution. Forgot about it because I couldn't get it to do what I wanted. Now the problem seems to be I can't get rid of it

---

### Post by wilsojeffrey on 2021-06-10
```
[sudo apt remove evolutionReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 evolution-ews : Depends: evolution (>= 3.36) but it is not going to be installed
                 Depends: evolution (< 3.37) but it is not going to be installed
 evolution-plugin-bogofilter : Depends: evolution (= 3.36.5-0ubuntu1) but it is not going to be installed
 evolution-plugin-pstimport : Depends: evolution (= 3.36.5-0ubuntu1) but it is not going to be installed
 evolution-plugins : Depends: evolution (= 3.36.5-0ubuntu1) but it is not going to be installed
 libevolution : Depends: evolution-common (= 3.36.5-0ubuntu1) but 3.36.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```


I feel like a Windows user right now. how do I get rid of this? or am I looking at a re-install? BTW. Ubuntu 20.04, and I'm completely new (a few weeks) to Linux

---

### Post by sudodus on 2021-06-10
Did you try also a full-upgrade?

```

sudo apt full-upgrade

```

and repeat the commands. If still problems, did you try

```

sudo apt update
sudo apt-get install -f
sudo apt-get install -m
sudo apt update

sudo apt remove evolution

```

---

### Post by sudodus on 2021-06-10
Maybe some of the non-ubuntu repositories causes the problem:

```

dl.google.com/linux/chrome/deb
ppa.launchpad.net/audio-recorder/ppa/ubuntu
ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu
ppa.launchpad.net/savoury1/digikam/ubuntu

```

but let us hope that you will soon fix it without removing the applications installed from there and those repositories.

I think there is a **snap** alternative for Chrome, and it should be less intrusive.

[https://snapcraft.io/install/chromium/ubuntu](https://snapcraft.io/install/chromium/ubuntu)

---

### Post by wilsojeffrey on 2021-06-10
Every combination of commands I try ends with that message about unmet dependencies. All associated with one application that I can't seem to delete

---

### Post by sudodus on 2021-06-10
- Did you check that your file system is healthy according to the link in post #4 ?

- Are you prepared to remove the programs installed via the non-ubuntu repositories and then remove those repositories? It can be a lot of work, and it may or may not help you solve the problem.

[hr][/hr]
Edit: At this point I would be happy if some other people will chip in and offer new ideas to try :-P

---

### Post by CatKiller on 2021-06-10
> **wilsojeffrey said:**
> Every combination of commands I try ends with that message about unmet dependencies. All associated with one application that I can't seem to delete

The package manager seems like magic sometimes, but it just goes through the lists of dependencies for each package to create a dependency tree to help determine what it should do to achieve what you've asked it to do. Sometimes it gets confused and can't work it out (in this case, because you seem to have a different version of evolution-common than the other components of evolution).

It's trying its hardest to remove evolution (because you've asked it to) but to keep all of the dependencies (because you haven't asked it to remove them). apt is only one front-end command for the APT system; there are others (like apt-get and aptitude) that make different choices about handling dependencies.

Since you don't want evolution, one approach would be to tell apt that you don't want evolution's dependencies either:

```
sudo apt remove evolution evolution-common evolution-ews evolution-plugin-bogofilter evolution-plugin-pstimport evolution-plugins libevolution
```

to see if that gets your package manager untangled.

---

### Post by wilsojeffrey on 2021-06-10
That did it. Thank you so much, and to everyone who tried to help. If I was younger and had more time, I'd try to learn why. Cheers

---

### Post by wilsojeffrey on 2021-06-10
```
[sudo apt updateHit:1 http://au.archive.ubuntu.com/ubuntu focal InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                        
Get:3 http://au.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                  
Get:4 http://au.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]                                                          
Get:5 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB]                      
Hit:6 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu focal InRelease
Hit:7 http://ppa.launchpad.net/mscore-ubuntu/mscore-stable/ubuntu focal InRelease   
Hit:8 http://ppa.launchpad.net/savoury1/digikam/ubuntu focal InRelease
Fetched 328 kB in 2s (151 kB/s)                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.



```

---

### Post by sudodus on 2021-06-10
Thanks CatKiller, for the solution, and congratulations wilsojeffrey :KS

I would like to know how you found all those dependencies of evolution. Is there a general method (command or web-site)? Or did you simply look for packages with names containing evolution ... ?

---

### Post by CatKiller on 2021-06-10
> **sudodus said:**
> Thanks CatKiller, for the solution, and congratulations wilsojeffrey :KS

I would like to know how you found all those dependencies of evolution. Is there a general method (command or web-site)? Or did you simply look for packages with names containing evolution ... ?

The earlier code output provided showed which packages were having dependency problems.

---

### Post by Impavidus on 2021-06-10
> **wilsojeffrey said:**
> ```

Unpacking evolution-common (3.36.5-0ubuntu1) over (3.36.4-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/evolution-common_3.36.5-0ubuntu1_all.deb (--unpack):
 failed to stat (dereference) existing symlink '/usr/share/help/sl/evolution/mail-encryption-gpg-decrypting.page': Input/output error

```
That looks like the root cause of your problem. Input/output errors on filesystem access indicate filesystem damage, if not hard drive damage. I suggest you keep a close eye on your hard drive.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

