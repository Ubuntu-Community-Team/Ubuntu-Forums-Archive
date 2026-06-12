---
title: "I've found dependancy hell - Help?"
date: 2014-12-23
forum: New to Ubuntu
---

### Post by Perry_Lloyd on 2014-12-23
Hi.
Im running 64bit Ubuntu (well, Xubuntu), and... im not sure what else you need to know.

Okay, last night i tried to use Parole Media Player to play a .flv, and it said that it needed to install some dependancies to do that. So... i figured since im using the program a plugin for it couldnt possibly break anything.

So, after it uninstalled Parole and Audacity whilst failing to install the plugin for some reason (no idea why it removed audacity), it isnt letting me install *anything* now.
Ive tried installing through the terminal as well, and it just wont do it. Ive also done all sorts of updating to see if that helped.

I get two things:
```
Package dependancies cannot be resolved.
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:
parole: Depends: libc6 (>= 2.4) but 2.19-0ubuntu6.4 is to be installed
        Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1 is to be installed
        Depends: libdbus-1-3 (>= 1.0.2) but 1.6.18-0ubuntu4.3 is to be installed
        Depends: libdbus-glib-1-2 (>= 0.88) but 0.100.2-1 is to be installed
        Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.30.7-0ubuntu1 is to be installed
        Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed
        Depends: libgstreamer-plugins-base1.0-0 (>= 1.0.0) but 1.2.4-1~ubuntu1 is to be installed
        Depends: libgstreamer1.0-0 (>= 1.0.0) but 1.2.4-0ubuntu1 is to be installed
        Depends: libgtk-3-0 (>= 3.1.6) but 3.10.8-0ubuntu1.3 is to be installed
        Depends: libnotify4 (>= 0.7.0) but 0.7.6-1ubuntu3 is to be installed
        Depends: libtagc0 (>= 1.5) but 1.9.1-2 is to be installed
        Depends: libxfce4ui-2-0 (>= 4.11.0) but 4.11.1-2ubuntu1 is to be installed
        Depends: libxfce4util6 (>= 4.9.0) but 4.10.1-1ubuntu1 is to be installed
        Depends: libxfconf-0-2 (>= 4.6.0) but 4.10.0-2ubuntu1 is to be installed

```
The application Ubuntu Software Center has experienced an internal error.
There was an error submitting the transaction

I dont wanna have to reinstall Xubuntu from scratch - Help?

---

### Post by westie457 on 2014-12-23
Hi Perry_Lloyd welcome to the Forum

In a terminal give these two commands a go ```
sudo apt-get -f install
sudo dpkg --configure -a
``` if they fail post the output from both. If possible post the output between [code] brackets by clicking on the # in the advanced reply window.

Hopefully either or both will fix things otherwise it will get technical very quickly.

edit: in the terminal highlight text to copy (easiest with a mouse) and paste between the {code] brackets. This makes the output very easy to read.

---

### Post by Perry_Lloyd on 2014-12-23
I think ive broken something pretty righteously :/

```

psxhomepc@psxhomepc-System-Product-Name:~$ sudo apt-get -f install
[sudo] password for psxhomepc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  audacity-data hyphen-en-us kde-l10n-engb libbaloocore4 libbaloofiles4
  libbalooxapian4 libepub0 libflac++6 libgsm1 libid3tag0
  libkactivities-models1 libkidletime4 libmp3lame0 libnepomukcleaner4
  libnepomukcore4abi1 libopencore-amrnb0 libopencore-amrnb0:i386
  libopencore-amrwb0 libopencore-amrwb0:i386 libportsmf0 libqmobipocket1
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libsbsms10 libschroedinger-1.0-0 libsoundtouch0
  libsoxr0 libtwolame0 libva1 libvamp-hostsdk3 libvo-aacenc0
  libvo-aacenc0:i386 libvo-amrwbenc0 libvo-amrwbenc0:i386 libwxbase2.8-0
  libwxgtk2.8-0 libx264-142 libxvidcore4 libzip2 linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-headers-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  linux-image-generic mythes-en-au mythes-en-us nepomuk-core-data
  nepomuk-core-runtime openoffice.org-hyphenation shared-desktop-ontologies
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
psxhomepc@psxhomepc-System-Product-Name:~$ sudo dpkg --configure -a
psxhomepc@psxhomepc-System-Product-Name:~$ 

```

Im guessing that the second command not doing anything is bad.

EDIT: Also, thanks for the welcome :)

---

### Post by westie457 on 2014-12-23
Which plug-in were you trying to install? On the surface there would appear to be nothing wrong with your system.
Try to install audacity again, post the output if it fails. ```
sudo apt-get install --reinstall audacity
```The --reinstall is there just in case apt-get says it is already installed.
If that goes okay try to ```
sudo apt-get install --reinstall parole
```

Usually when a command returns straight to a clear line it has worked properly or there was nothing to be done. In this case there was nothing to be done. if there was a problem there would have been lots of output as dpkg tried to resolve all dependencies and broken packages. The same is true for apt-get -f install. All the first command did was list the no longer needed parts of an app (possibly Audacity) that are no longer needed. Having said that **do not run**&#8203; apt-get autoremove just yet because in that list might be something the system really needs.

---

### Post by Perry_Lloyd on 2014-12-23
No dice. I hope this information helps:

```
psxhomepc@psxhomepc-System-Product-Name:~$ sudo apt-get install --reinstall audacity
[sudo] password for psxhomepc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 audacity : Depends: libavcodec54 (>= 6:9.1-1) but it is not going to be installed or
                     libavcodec-extra-54 (>= 6:9.13) but it is not going to be installed
            Depends: libavformat54 (>= 6:9.1-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
psxhomepc@psxhomepc-System-Product-Name:~$ 


```

It was some flash plugin for Parole - I cant remember what it was called, and i dont know how i can check without being able to reinstall it and repeat what i was trying to do.
...maybe its that libavcodec stuff?

Incase it helps,

```

psxhomepc@psxhomepc-System-Product-Name:~$ sudo apt-get install --reinstall parole
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 parole : Depends: gstreamer1.0-libav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by mc4man on 2014-12-24
Please post the results of this - 
```
apt-cache policy libavcodec*
```

---

### Post by Impavidus on 2014-12-24
> **westie457 said:**
> Having said that **do not run**&#8203; apt-get autoremove just yet because in that list might be something the system really needs.

There is one for sure: linux-image-generic. Without that package you won't get kernel upgrades. When your current issue has been fixed, don't forget to reinstall **linux-generic**, which will prevent linux-image-generic from automatic removal.

---

