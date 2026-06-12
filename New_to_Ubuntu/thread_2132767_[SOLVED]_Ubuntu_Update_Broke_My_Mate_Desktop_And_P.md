---
title: "[SOLVED] Ubuntu Update Broke My Mate Desktop And Package Manager??"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by Akacheebe on 2013-04-05
I posted this on the Mate forum but doesn't look like there's much help there.  What happened is that I did a Ubuntu update today around lunch time that was over 150MB in size and at the end it said there were errors and it couldn't complete them.  This is Ubuntu 12.04 with Mate 1.4 desktop and there were a BUNCH of Mate updates in that 150 MB download.  Now I have just the default Mate desktop background and some of the icons are missing or incomplete.  I've tried to fix it with the -f install command from terminal but it's a no go.  I also tried to "remove" one of the dependencies that is mentioned in the error message but can't do that either.  So I went into Ubuntu Software Center trying to install Synaptics so I could uninstall gstream but that won't work either and gives me error messages.  Tried the "repair" there but that didn't work either. Here's what I get from "upgrade" through the "-f install" in terminal.  

```
xxx@ubuntuYB:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mate-media-gstreamer : Depends: mate-media-common (= 1.4.0-1+precise) but 1.6.0-1+precise is installed
E: Unmet dependencies. Try using -f.
xxx@ubuntuYB:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  mate-window-manager
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mate-media-gstreamer
The following packages will be upgraded:
  mate-media-gstreamer
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
Need to get 0 B/405 kB of archives.
After this operation, 813 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 501491 files and directories currently installed.)
Preparing to replace mate-media-gstreamer 1.4.0-1+precise (using .../mate-media-gstreamer_1.6.0-1+precise_amd64.deb) ...
Unpacking replacement mate-media-gstreamer ...
dpkg: error processing /var/cache/apt/archives/mate-media-gstreamer_1.6.0-1+precise_amd64.deb (--unpack):
 trying to overwrite '/usr/share/omf/mate-mixer_applet2/mate-mixer_applet2-ko.omf', which is also in package mate-applets-common 1.4.0-1+precise
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/mate-media-gstreamer_1.6.0-1+precise_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
xxx@ubuntuYB:~$ 

```

---

### Post by Frogs Hair on 2013-04-05
If this was a partial update _you might want to wait for held packages_. You would likley have seen a message if it was. It is possible to force  package versions from synaptic to correct the problem but this is not to be taken lightly.

 When you look in package properties in synaptic select versions and if  there is more than one package listed that often indicates a conflict.Knowing which version to select is the hard part.  If you have uninstalled residual packages compare them to the installed version because they may offer clues. Look at the auto removable list also if there is one but don't remove them. You may have a situation where some ubuntu desktop packages are now auto removable.

---

### Post by Akacheebe on 2013-04-05
Can't install Synaptics as Ubuntu software center is broken and when I try to do it via terminal it won't install there either.  I've even tried to purge that mate-media file that's listed and it won't do that either???

---

### Post by Akacheebe on 2013-04-05
Just got this info after changing update servers:

```
The following packages have unmet dependencies:

mate-media-gstreamer: Depends: libatk1.0-0 (>= 1.12.4) but 2.4.0-0ubuntu1 is installed
                      Depends: libc6 (>= 2.2.5) but 2.15-0ubuntu10.3 is installed
                      Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is installed
                      Depends: libglib2.0-0 (>= 2.24.0) but 2.32.3-0ubuntu1 is installed
                      Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.10-0ubuntu6 is installed
                      Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-5.1ubuntu4.4 is installed
                      Depends: mate-media-common (= 1.4.0-1+precise) but 1.6.0-1+precise is installed
```

---

### Post by Akacheebe on 2013-04-06
Ok so no one else has any suggestions on this??

I got a response  from the mate board with the following procedure to fix my broken  package system, which is more a Ubuntu problem than a Mate problem and I'd like a second opinion on this before I use it as I really don't want to have to do another clean install!

> Ok. This, when done properly, will help you fix  your system. If not done properly you will cause further problems. I  make no promises, because I do not know your ability, that this will  work so you follow this at your own risk.

In order to fix this I  believe you will need to chroot into your system using the Live CD. To  do this please follow these commands. Do not worry about putting the  lines with a # at the beginning they are there to tell you, and anyone  else reading this, what you are doing.


```
#mounting. You may need to use sudo infront of these commands
mkdir /mnt/temp #makes a directory to mount your system into.
mount /dev/sda1 /mnt/temp #this mounts your system into that directory and this assumes your system is located on sda1
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i; done #this mounts various working locations
cp /etc/resolv.conf /mnt/temp/etc/resolv.conf #this gives you internet access assuming your LiveCD has it
chroot /mnt/temp #this takes you into your system so you can work on it to repair it
```

Now  you know how to mount your system using a LiveCD you also need to know  how to unmount it after you have done your repairs do this by following  this command in a terminal

```
#Unmounting
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/temp$i ; done
```

To  carry out repairs it is important you think before you do. If you just  do something without thinking about it you will most likely break  something so be very careful.

```
#Some repair commands, you must do the first two in order, the others are optional and are posted here as a guide only.
apt-get update
apt-get upgrade
apt-get  remove <packagename> # you will most likely need this in your  case considering you will want to remove mate-media-gstreamer
apt-get upgrade # this should finish off your previous upgrade after you have removed mate-media-gstreamer
apt-get  install <packagename> # if the apt-get upgrade worked properly  then reinstall mate-media-gstreamer. If it didn't you will want to  install mate-core or mate-desktop-environment
apt-get install -f #to force a package installation which is not advisable if you don't know what you are doing
dpkg --configure -a # reconfigures known packages
apt-get dist-upgrade # upgrades from one release of Ubuntu to another you wont need this at this time.
```

---

### Post by ilGuccino on 2013-04-06
sudo dpkg --force-all -P mate-applets-common
sudo apt-get -f install (maybe more than once)
then update, upgrade, dist-upgrade, as you want
it worked for me

---

### Post by Akacheebe on 2013-04-07
The procedure in post #5 worked to repair the broken package system.  All seems to be back to "normal" now.

---

