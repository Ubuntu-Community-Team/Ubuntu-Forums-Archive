---
title: "Single-window Epiphany"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by ow50 on 2006-02-12
With some tricks, it's possible to get Epiphany to open new tabs instead of new windows. For this to work some settings need to be changed and a patched version of Epiphany, which I have packaged for i386, is needed.

**Opening external links in existing window**

Epiphany has an option "-n" or "--new-tab", which opens a new tab instead of a new window. To use that always, do the following:

Add a bash alias to your ~/.bashrc
```
alias epiphany='epiphany -n'
```

Go in your panel to System -> Settings -> Default Applications and change your browser to command "epiphany -n".

Edit the desktop file
```
sudo gedit /usr/share/applications/epiphany.desktop
```
Include "-n" on the "Exec" line.
```
Exec=epiphany -n %U
```

**Opening internal links in existing window**

I grabbed Epiphany 1.9.6 from Dapper and patched it with some patches I found in an Epiphany 1.9.6 AUR Arch Linux [package](http://aur.archlinux.org/packages.php?do_Details=1&ID=2156&O=0&L=0&C=0&K=epiphany&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd). Note that this is an unstable release of Epiphany and it is patched, so install at your own risk. As always, I have uploaded the source as well so feel free to check the patches used. Based on my couple days experience, this works as expected, but there could be some side-effects.

Get the epiphany-browser and epiphany-extensions i386 packages from my repository
[http://koti.mbnet.fi/~ots/ubuntu/breezy/](http://koti.mbnet.fi/~ots/ubuntu/breezy/)

---

