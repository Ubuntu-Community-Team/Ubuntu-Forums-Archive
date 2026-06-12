---
title: "cannot completely remove wine"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by planet81 on 2014-11-28
sory for my bad english, i'm from asian
i currently using kubuntu 14.04 (KDE)
thing strange happen to me, after install wine using terminal with this command:
```
sudo apt-get install wine
```

i using it's wine, install windows app, and after a while i decide to remove it with this command:
```
sudo apt-get remove wine
```

nothing srange at this point, removing wine just work, but after look at application menu, wine still there. more strange its can be open and works well, can configure wine etc.
i was trying using command below (again):

```
sudo apt-get remove wine
sudo apt-get remove --purge wine
sudo apt-get --purge wine
```
its say wine not installed, but i still can run wine, even in terminal by tiping 'wine' and by tiping 'wine --version' its say wine-1.6.2 (i attached a screenshot)

far more was trying removing folder by command:
```

rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```

also did'nt work as well, wine still run. how that can be? thanks for the answer

---

### Post by fantab on 2014-11-28
In my experience, removing Wine is PITA.

Install pkg 'debfoster' and run it... it should show you all the wine related libs and other dependencies. Be careful when using debfoster... read what will be removed before you remove it.
You must also install 'deborphan'.

Also I would use 'dpkg' commands to remove Wine as follows:

```
$ sudo -i
    # dpkg --purge *pkgname*
    # apt-get remove --purge *pkgname*
    # apt-get clean 
    # apt-get install deborphan debfoster
    # debfoster [SIZE=1](shows leftover files and libs) (to undo debfoster action type 'u')[/SIZE]
    # deborphan [SIZE=1](shows orphans)[/SIZE]
    # deborphan | xargs apt-get -y remove purge
    # apt-get clean
    # apt-get update
    # exit
```

You may have to re-install wine, and then run above if debfoster and deborphan don't help.

EDIT: You must use '**synaptic**' package manager, it does a good job in removing packages.

---

### Post by planet81 on 2014-11-28
yay, it works after i try using synaptic, select wine and completely remove it, but why its not work using terminal? 
I not try debfoster yet, so far wine get rid on my system, thanks @fantab

---

### Post by mcduck on 2014-11-29
the "wine" package is just an empty metapackage. So installing it will bring actual wine packages along as dependencies, but removing it will remove just the metapackage itself (as dependencies are one-way mechanism).

The actual package for Wine, at least in Ubuntu 14.10, is called "wine1.6"

---

### Post by planet81 on 2014-12-02
> **mcduck said:**
> the "wine" package is just an empty metapackage. So installing it will bring actual wine packages along as dependencies, but removing it will remove just the metapackage itself (as dependencies are one-way mechanism).

The actual package for Wine, at least in Ubuntu 14.10, is called "wine1.6"

Omg, how come i so dumb, yes u right. i did reinstall wine and i using kubuntu 14.04 and wine version is 1.6,
using command

```
sudo apt-get remove wine1.6
```

i get this

```
The following packages will be REMOVED:
  wine wine1.6 wine1.6-i386
```

thanks, case solved

---

