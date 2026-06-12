---
title: "Trying to install gnome 3..."
date: 2013-07-07
forum: New to Ubuntu
---

### Post by amantonas on 2013-07-07
I'm running 13.04, and I'm trying to install the gnome desktop, so I followed these instructions:
```
Type in the following commands then hit Enter after each.

sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell gnome-shell-extensions gnome-tweak-tool
```

But when I run update, I get this at the end:
```
W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Which I don't understand. Why should it be looking at .../ubuntu/dists/**precise** instead of .../raring ?
How can I change it to look in the right folder?


EDIT: nevermind this is so embarrassing, I'm running 12.04. I'm gonna upgrade now haha

---

### Post by grahammechanical on 2013-07-07
I think that you are missing a step here. Those PPAs are appropriate mainly for someone running Ubuntu Gnome.

[http://ubuntugnome.org/](http://ubuntugnome.org/)

If you want to install Gnome 3 Shell you can do so from the Ubuntu Software Centre. Just search for Gnome shell. You might also want to install Gnome shell extension preferences.

If you go to the Launchpad page and click on technical details about this PPA you will find a menu where you can select your version of Ubuntu. I really do not think that this PPA should be used with just the Gnome shell desktop being installed over Ubuntu.

Regards.

---

