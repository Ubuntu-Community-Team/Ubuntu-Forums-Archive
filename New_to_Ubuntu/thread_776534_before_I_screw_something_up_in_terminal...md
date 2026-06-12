---
title: "before I screw something up in terminal.."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by phoenix180 on 2008-04-30
Greetings all! I have finally installed kubuntu after hours of getting error messages but I would like to install ubuntu because that's what I was really trying to install(7.10 because 8.04 wouldn't work) and so I entered the following into the terminal: sudo aptitude get ubuntu-desktop  This is what I received as a response:

 Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
maunykah@maunykah-linuxdesktop:~$ install
install: missing file operand
Try `install --help' for more information.
maunykah@maunykah-linuxdesktop:~$


What should I do next? Thanks for your time!!

---

### Post by stalkier on 2008-04-30
Personally I would just download the ISO of 7.10. It is still available thru Ubuntu.com. It will also allow you to run it via LiveCD which is really good as a "just in case".

---

### Post by llamakc on 2008-04-30
You're typing the wrong command.

It is:

```

sudo aptitude install ubuntu-desktop

```

Good luck!

---

### Post by volkswagner on 2008-04-30
I do.n't often use aptitude.  So not sure your syntax error.

I would use apt-get.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by stalkier on 2008-04-30
> **volkswagner said:**
> I do.n't often use aptitude.  So not sure your syntax error.

I would use apt-get.

```
sudo apt-get install ubuntu-desktop
```

I agree with you. atp-get is the better way to go (from what I hear...).

---

### Post by llamakc on 2008-04-30
> **stalkier said:**
> I agree with you. atp-get is the better way to go (from what I hear...).

I am an old Debian user and quite familiar with apt-get. This page does a good job of explaining why aptitude should be used on the command line, and definitely if you're not going to be running all of the ancillary apt-get commands to keep your system trim.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by phoenix180 on 2008-04-30
Thanks for the responses everyone! While I was waiting I sort of just tried what is posted above without reading anything: sudo aptitude install ubuntu-desktop.  Did I do a horrible thing by choosing aptitude instead of apt-get?  I read in a thread that can be found here(I was searching for it but I couldn't find it yet) that it's better to use aptitude to get full updated packages or something of that nature..

---

### Post by martrn on 2008-04-30
> **phoenix180 said:**
> Thanks for the responses everyone! While I was waiting I sort of just tried what is posted above without reading anything: sudo aptitude install ubuntu-desktop.  Did I do a horrible thing by choosing aptitude instead of apt-get?  I read in a thread that can be found here(I was searching for it but I couldn't find it yet) that it's better to use aptitude to get full updated packages or something of that nature..

no apt-get manages the apt packages and is pretty similar to apttitude.  The only benifit of using one or the other is if you only use aptitiude perminantly and it will manage dependences a little better (by removing them).  

I think it is better to use apt-get as it is only 7 letters to type aptitide is 8 I think, and I can't spell apttitude anyways.

---

### Post by abhiroopb on 2008-04-30
and instead of typing "get" you should use "install"

---

