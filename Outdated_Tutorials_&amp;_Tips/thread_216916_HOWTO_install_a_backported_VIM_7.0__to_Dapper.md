---
title: "HOWTO: install a backported VIM 7.0  to Dapper"
date: 2006-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2006-07-16
**[COLOR="Red"]NOTE: these packages are for Ubuntu 32bit[/COLOR]**

Download the following packages which I backported from Edgy:

[http://www.webalice.it/albertomilone/ubuntu/Vim/vim_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-common_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-common_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-doc_7.0-017+8_all.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-doc_7.0-017+8_all.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-full_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-full_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gnome_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gnome_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gtk_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gtk_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gui-common_7.0-017+8_all.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-gui-common_7.0-017+8_all.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-lesstif_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-lesstif_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-perl_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-perl_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-python_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-python_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-ruby_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-ruby_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-runtime_7.0-017+8_all.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-runtime_7.0-017+8_all.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-tcl_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-tcl_7.0-017+8_i386.deb)
[http://www.webalice.it/albertomilone/ubuntu/Vim/vim-tiny_7.0-017+8_i386.deb](http://www.webalice.it/albertomilone/ubuntu/Vim/vim-tiny_7.0-017+8_i386.deb)

then:

Uninstall VIM
```
sudo apt-get remove --purge vim
```

Install VIM 7
```
cd folder_in_which_you_put_the_files
sudo dpkg -i *.deb
```

---

### Post by ZonedOut on 2006-07-16
I tried to follow the how-to but ran into a problem.  When I tried the command ```
sudo apt-get source -b vim
``` I got this error: ```
dpkg-checkbuilddeps: Unmet build dependencies: dpkg-dev (>= 1.13.19)
``` This is true because I have version 1.13.11ubuntu6 in the repository.  What can I do to fix the dependency problem?

---

### Post by tseliot on 2006-07-16
> **ZonedOut said:**
> I tried to follow the how-to but ran into a problem.  When I tried the command ```
sudo apt-get source -b vim
``` I got this error: ```
dpkg-checkbuilddeps: Unmet build dependencies: dpkg-dev (>= 1.13.19)
``` This is true because I have version 1.13.11ubuntu6 in the repository.  What can I do to fix the dependency problem?

Didn't you do "sudo apt-get build-dep vim" ?

---

### Post by ZonedOut on 2006-07-16
It appears there was an error there that I originally did not notice ```
zonedout@TheZone:~$ sudo apt-get build-dep vim
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for vim cannot be satisfied because no available versions of package dpkg-dev can satisfy version requirements
```

---

### Post by tseliot on 2006-07-16
> **ZonedOut said:**
> It appears there was an error there that I originally did not notice ```
zonedout@TheZone:~$ sudo apt-get build-dep vim
Reading package lists... Done
Building dependency tree... Done
E: Build-Depends dependency for vim cannot be satisfied because no available versions of package dpkg-dev can satisfy version requirements
```

Can you post the content of your /etc/apt/sources.list ?

---

### Post by ZonedOut on 2006-07-16
Here it is: ```
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
```

---

### Post by tseliot on 2006-07-17
> **ZonedOut said:**
> Here it is: ```
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
```

Try adding:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
```

then:
```
sudo apt-get update
```

and try again

---

### Post by ZonedOut on 2006-07-17
I tried adding those but it didn't change anything.  I think I already had those repos with: ```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
``` in the middle of the file.

---

### Post by tseliot on 2006-07-17
> **ZonedOut said:**
> I tried adding those but it didn't change anything.  I think I already had those repos with: ```
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
``` in the middle of the file.

It's universe and not universe multiverse

---

### Post by ZonedOut on 2006-07-17
I looked on [http://packages.ubuntu.com](http://packages.ubuntu.com) and it lists dpkg-dev (1.13.11ubuntu6) for dapper which is the current package that I have.  This version is not high enough to satisfy the dependency dpkg-dev (>= 1.13.19).  Are you saying that there's an update in the universe that I'm missing?  And can you explain why adding the multiverse would make any difference?  I thought having universe and multiverse just adds them both.  Thanks for the help.

---

### Post by tseliot on 2006-07-17
> **ZonedOut said:**
> I looked on [http://packages.ubuntu.com](http://packages.ubuntu.com) and it lists dpkg-dev (1.13.11ubuntu6) for dapper which is the current package that I have.  This version is not high enough to satisfy the dependency dpkg-dev (>= 1.13.19).  Are you saying that there's an update in the universe that I'm missing?  And can you explain why adding the multiverse would make any difference?  I thought having universe and multiverse just adds them both.  Thanks for the help.

If the version of dpkg-dev is the latest, then they might have changed the source code of Vim for Edgy. I'll suspend this guide, at least for now

---

### Post by tseliot on 2006-07-18
When I find a better way to backport VIM I'll post my guide again.

Until then you can try the packages I backported sometimes ago

---

### Post by FredB on 2006-07-18
Thanks for your how-to, but I think I will wait for the "official" backport version of VIM 7.0 and use my homemade version for now :p

---

### Post by dante.regis on 2006-11-15
I believe the problem is that vim 7 may use a new version of the gcc libraries that is not a simple release, but probably a new minor version or something. So, probably, they did not release the package to dapper because it could lead to compatibility problems with the current software (and cannonical has it's long term support term).

That's my theory :)

---

### Post by LeeU on 2007-05-30
Have you got this worked out yet? I started using the tutorial over at: [http://doc.gwos.org/index.php/Backport_VIM7]("http://doc.gwos.org/index.php/Backport_VIM7"). Everything was fine until I got to download the source code and complie it. I then got:
```

dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
Build command 'cd vim-7.0 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

```

Any ideas?

Even though I tried to go on, it couldn't read the packages:
```

sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
```

---

