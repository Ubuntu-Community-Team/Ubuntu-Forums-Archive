---
title: "package manager : restoration"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by crackers_altitude on 2014-02-23
[ Ubuntu 12.04.4 LTS ]

this must already be explained, however, it is tricky to Google, thus my explanation here:

I have accumulated numerous libraries/software packages (as everyone has). I have used a combination of the Synaptic Package Manager gui, and apt-get command line interface commands on top of that. this has resulted in a bunch of repositories and perhaps other things in /etc/apt I think.

I would like to know if there are files/resources to copy ( perhaps cp /etc/apt backup_of_apt ) that will completely restore the default installation to what it is currently running with. I imagine there is some simple way to make an external resource that can be copied into a new Ubuntu installation - instead of getting each piece of software one at a time using Synaptic or apt-get.

---

### Post by deadflowr on 2014-02-23
Don't know if this helps, but whether you run synaptic, software center, or apt-get, you are using the same repositories.
You don't get new repos for each one, as in a sense, all three are doing the same thing and pulling from the same resource.

---

### Post by crackers_altitude on 2014-02-23
perhaps this scenario would illustrate:

step 1. system running with latest greatest Ubuntu. 
step 2. user installs lots of software with Synaptic or what-have-you, for many months or years. the list of software/libraries/etc grows so long as not to be remembered.
step 3. hard drive fails. install new hard drive, install Ubuntu.

now the user wants a fast and easy way to go through step 2. a "manual" way to do this would be to have a list of titles that is edited by hand every time a new install is done. however, we all know how that usually goes.

so if there's a list of not everything, but software/libraries/etc. that was added to a standard Ubuntu installation, so the package manager can get all of the titles in one go.

---

### Post by deadflowr on 2014-02-23
This will output a list of all installed packages t a text file
```
dpkg --get-selections > package.txt
```
by default it will put the file in the top level of the home folder(where the Downloads,Documents,Pictures folder are)
To reinstall you
```
sudo dpkg --set-selections < package.txt
```
changing package.txt to the location of the file.

I think on the new install you need to install the package dslect, first before running the set-selections command.
This is a better response on that
[http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)

---

### Post by crackers_altitude on 2014-02-23
ah, great - thanks a lot, this gets me going!

---

