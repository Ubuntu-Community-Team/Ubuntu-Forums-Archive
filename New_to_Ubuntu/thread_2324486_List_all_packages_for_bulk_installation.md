---
title: "List all packages for bulk installation"
date: 2016-05-14
forum: New to Ubuntu
---

### Post by Jan_Pappert on 2016-05-14
Hey guys,

so I've grown fond of linux due to the sheer amount of customization that is possible. 
Thus naturally, the more I customize ubuntu to my needs, the more a dread a situation in which the system crashes and in which a would have to painstackingly put all pieces back together.
Or more simply: Transfer my configuration to my notebook.

So, does anyone know a quick way to list all packages that one has manually installed, including dependencies, and a way to quickly bulk install them to a new system?

Cheers,
Jan

---

### Post by buzzingrobot on 2016-05-14
Have a look here: [https://wiki.debian.org/ListInstalledPackages](https://wiki.debian.org/ListInstalledPackages)

Ubuntu uses the same package management tools.  I've used it, carefully, to restore a system after a re-install.  Some tweaks were needed.

I don't know how, or if, this handles Snap packages available in 16.04.

Really depends, though, on what "manually installed" means.

The package management system relies on software packaged in the correct ".deb" structure and looks for software/updates/dependencies only in the repositories in a list maintained on your system. It is unaware of anything not installed via a .deb. It won't record its presence or that of any of the files it installs, won't know if/when it should be update, and won't know if/when or where to find any updates or dependencies.

If something that is "manually installed" was not in .deb format and did not install a repository file, then the package manager can not determine and find needed dependencies or updates.

---

### Post by jim_deadlock on 2016-05-14
Save list on old system:

```
dpkg --get-selections > ~/my-packages
```

Install list on new system:

```
sudo dpkg --set-selections < ~/my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
```

However, most people's main concern is not losing the apps themselves but the custom configurations for each app. The configs are stored in the /home/user directory (the hidden directories with leading dots). For this reason it's a good idea to install Ubuntu in 2 partitions / and /home (and another for swap in you want). This makes it very easy to reinstall the system without losing any configs. Reinstalling apps is easy, and it's not a problem forgetting what you had because you only need an app when you need it if you see what I mean, and your software installer will usually install any dependencies automatically.

---

