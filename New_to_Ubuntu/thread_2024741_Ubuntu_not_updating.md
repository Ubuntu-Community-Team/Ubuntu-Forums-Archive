---
title: "Ubuntu not updating"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by TheManno1 on 2012-07-14
I have Ubuntu 12.04 LTS
After purging 
ppa:gnome3-team/gnome3 in yppa.

then 
sudo apt-get update

N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
E: The list of sources could not be read.

---

### Post by coffeecat on 2012-07-14
You have some problems in the /etc/apt/sources.list.d/ directory. Post the output of these two terminal commands:

```
ls /etc/apt/sources.list.d/
cat /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
```

You can paste the terminal output into your post by highlighting it with the mouse and right-click -> copy.

---

### Post by TheManno1 on 2012-07-14
john@john-laptop:~$ ls /etc/apt/sources.list.d/
banshee-team-ppa-lucid.list
banshee-team-ppa-lucid.list.distUpgrade
banshee-team-ppa-lucid.list.save
cheleb-blender-svn-lucid.list
cheleb-blender-svn-lucid.list.distUpgrade
cheleb-blender-svn-lucid.list.save
cinelerra-ppa-ppa-lucid.list
cinelerra-ppa-ppa-lucid.list.distUpgrade
cinelerra-ppa-ppa-lucid.list.save
docky-core-ppa-lucid.list
docky-core-ppa-lucid.list.distUpgrade
docky-core-ppa-lucid.list.save
doctormo-xorg-wizardpen-lucid.list
doctormo-xorg-wizardpen-lucid.list.distUpgrade
doctormo-xorg-wizardpen-lucid.list.save
dreibh-ppa-lucid.list
dreibh-ppa-lucid.list.distUpgrade
dreibh-ppa-lucid.list.save
ferramroberto-java-lucid.list
ferramroberto-java-lucid.list.distUpgrade
ferramroberto-java-lucid.list.save
flexiondotorg-shotwell-lucid.list
flexiondotorg-shotwell-lucid.list.distUpgrade
flexiondotorg-shotwell-lucid.list.save
getdeb.list
getdeb.list.bck
getdeb.list.distUpgrade
getdeb.list.save
globalmenu-team-ppa-lucid.list
globalmenu-team-ppa-lucid.list.distUpgrade
globalmenu-team-ppa-lucid.list.save
gnome3-team-gnome3-lucid.list.save
gnome3-team-gnome3-precise.list
gnome3-team-gnome3-precise.list.save
gnome-media-player-development-development-lucid.list.save
gregory-hainaut-pcsx2.official.ppa-lucid.list
gregory-hainaut-pcsx2.official.ppa-lucid.list.distUpgrade
gregory-hainaut-pcsx2.official.ppa-lucid.list.save
lucid-bleed-ppa-lucid.list
lucid-bleed-ppa-lucid.list.distUpgrade
lucid-bleed-ppa-lucid.list.save
lucid-partner.list
lucid-partner.list.distUpgrade
lucid-partner.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
motumedia-mplayer-daily-lucid.list
motumedia-mplayer-daily-lucid.list.distUpgrade
motumedia-mplayer-daily-lucid.list.save
mozillateam-thunderbird-stable-lucid.list
mozillateam-thunderbird-stable-lucid.list.distUpgrade
mozillateam-thunderbird-stable-lucid.list.save
nilarimogard-webupd8-lucid.list
nilarimogard-webupd8-lucid.list.distUpgrade
nilarimogard-webupd8-lucid.list.save
n-muench-vlc2-lucid.list
n-muench-vlc2-lucid.list.distUpgrade
n-muench-vlc2-lucid.list.save
n-muench-vlc-lucid.list
n-muench-vlc-lucid.list.distUpgrade
n-muench-vlc-lucid.list.save
paul-climbing-ppa-lucid.list
paul-climbing-ppa-lucid.list.distUpgrade
paul-climbing-ppa-lucid.list.save
playdeb.list
playdeb.list.distUpgrade
playdeb.list.save
playonlinux.list
playonlinux.list.distUpgrade
playonlinux.list.save
ricotz-ppa-lucid.list
ricotz-ppa-lucid.list.distUpgrade
ricotz-ppa-lucid.list.save
stellarium-stellarium-releases-lucid.list
stellarium-stellarium-releases-lucid.list.distUpgrade
stellarium-stellarium-releases-lucid.list.save
sunab-kdenlive-release-lucid.list
sunab-kdenlive-release-lucid.list.distUpgrade
sunab-kdenlive-release-lucid.list.save
ubuntu-desktop-gnome3-builds-lucid.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.distUpgrade
ubuntu-wine-ppa-lucid.list.save
webupd8team-y-ppa-manager-lucid.list
webupd8team-y-ppa-manager-lucid.list.distUpgrade
webupd8team-y-ppa-manager-lucid.list.save
zyv-inkscape-backports-lucid.list
zyv-inkscape-backports-lucid.list.distUpgrade
zyv-inkscape-backports-lucid.list.save

---

### Post by TheManno1 on 2012-07-14
john@john-laptop:~$ cat /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main
ain

---

### Post by coffeecat on 2012-07-14
Problem 1 - the file getdeb.list.bck is misnamed. Backups usually take the filename *.list.save. Did you create that yourself? Since you have a getdeb.list.save, you might as well delete the problem file with:

```
sudo rm /etc/apt/sources.list.d/getdeb.list.bck
```

Problem 2 - the third line in your /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list file is spurious:
```
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
[COLOR="Red"]ain[/COLOR] 
```

Edit the file with:

```
gksudo gedit /etc/apt/sources.list.d/gnome3-team-gnome3-precise.list
```

And remove the third line so that it looks like this:

```
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
```

In your OP you say that you purged ppa:gnome3-team/gnome3, but it is still active.

---

### Post by TheManno1 on 2012-07-14
I reinstalled it after purging.And I think your suggestion fixed it. I can update now.

---

