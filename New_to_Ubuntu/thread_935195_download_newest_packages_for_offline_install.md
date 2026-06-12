---
title: "download newest packages for offline install"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by nutpants on 2008-10-01
is it possible to download the newest packages for an offline install?

i have to reinstall my Ubuntu 8.04 
and i would like to build a disk with the newest packages
of everything i have installed
so how do i do this?

how do i find out everything that i need
is there a script that will download all 4gigs of what i need
effortlessly?

this is for a laptop that i dont connect to the internet often at all.

or do i have to just do a install and then update for an hour or more..

nutz

---

### Post by wolfen69 on 2008-10-01
there is always [www.getdeb.net](www.getdeb.net) and [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by bhadotia on 2008-10-01
[l]("http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html")> **nutpants said:**
> is it possible to download the newest packages for an offline install?

i have to reinstall my Ubuntu 8.04 
and i would like to build a disk with the newest packages
of everything i have installed
so how do i do this?

how do i find out everything that i need
is there a script that will download all 4gigs of what i need
effortlessly?

this is for a laptop that i dont connect to the internet often at all.

or do i have to just do a install and then update for an hour or more..

nutz
You can use the 'APTonCD' package to create a disk of your cached packages. Also select the create a metapackage option when your creating a disk using this program as this will create a package in the disk called aptoncd metapackage which will depend on all the other packages on the disk and will thus make installing all the packages easier.
Also if some of the cached files are removed you can still install the packages that you installed in your previous install.Have a look at [this.]("http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html")

Hope that helps.
Abhishek

EDIT: I recommend using the above two methods combined as the packages in cache (/var/cache/apt/archives) may also belong to programs that you have uninstalled. So go like this:
1. Install aptoncd package:
```
sudo apt-get install aptoncd
```2 Create a DVD using the System>Administration>Aptoncd program.
3 Follow the steps in the howto ([html]http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html[/html]), I pointed you to, particularly:
```
sudo dpkg --get-selections > package.selections
```this will create a file called 'package.selections' in your Working directory (this means if you open a terminal and copy-paste the above command you will find the file in your home directory)
4 After reinstalling Copy the above file to the /etc directory:
```
sudo cp path_to_your_packages.selection /etc
```5 Put the Aptoncd disk in the drive and you will be automatically prompted to start the package manager (synaptic)- do so and this will add the disk to your list of repos.
6 Finally connect your laptop to internet (this is required to get some missing packages which were not cached or were removed from there), close synaptic and run:
```
sudo dpkg --set-selections < /etc/package.selections && apt-get dselect-upgrade
```Good Luck:popcorn:

---

### Post by hyper_ch on 2008-10-01
Hmmm, everything you have additionally installed is in
```
/var/cache/apt/archives
```

So, basically burn all those files to a cd or put them on a thumb drive or external drive... then reinstall the system... put those files back... and start installing all the apps again. It will then not download those .deb files again but directly install them.

Furthermore you could also create a list of packages installed and then have all those package to install again.

If you ever run
```

sudo apt-get clean

```
tehn you have deleted the downloaded .deb files...

---

