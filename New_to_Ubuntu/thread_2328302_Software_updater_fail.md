---
title: "Software updater fail"
date: 2016-06-19
forum: New to Ubuntu
---

### Post by Ron_Callison on 2016-06-19
Greetings all.  I've been using Ubuntu for a while but have run into a problem with the software updater.  I get the pop up window to update Chrome, Insyc, System Settings, Google Drive, and Google talk and after clicking "Install Now" a window comes up saying "Failed to Download Package Files".  I've tried several times over many days (even weeks) with always the same results.  What am I doing wrong.  (By the way, I think I have received Ubuntu updates and they downloaded successfully.)

---

### Post by &amp;KyT$0P# on 2016-06-19
In a terminal, what happens if you run this command?
```
sudo apt-get update
```

If that works without errors, what happens if you run this command (which will perform all the updates if successful)?
```
sudo apt-get dist-upgrade
```

---

### Post by Ron_Callison on 2016-06-19
Yes, I did that about a week ago but I just now did it again.  The very last entry for update is:

<E: Some index files failed to download. They have been ignored, or old ones used instead.>

The very last entries for upgrade are:

<E: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_5.41.3.0-1_amd64.deb](http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_5.41.3.0-1_amd64.deb)  Hash Sum mismatch


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?>


What do you think?

---

### Post by Impavidus on 2016-06-20
Could you post the *full* output of those commands? It may be good to know *which* index files failed to download. And can you tell which version of Ubuntu you run and whether it's 32 bit or 64 bit? If you're unsure, run these commands and post the output:```
uname -a
lsb-release -a
```

---

### Post by oldrocker99 on 2016-06-20
I've seen the Google repo fail an update command before, and my updates have worked fine.

**Some** repos seem to be incomplete, and it's a good idea to ping the available mirrors using Synaptic or the Software Updater to find the best and fastest. I'm having great results using tripadvisor.com (believe it or not).

---

### Post by Ron_Callison on 2016-06-20
I think I fixed it.  If you notice above there is a hyperlink in the notation at the end of the update/upgrade information.  I clicked on that hyperlink and I was asked to install a Google plugin, which I did.  After installation the update of all of the features was successful.  Thanks if you tried to help me.

---

### Post by vasa1 on 2016-06-20
> **Ron_Callison said:**
> ... Thanks if you tried to help me.
All the same, please remember to provide details people ask for. There have been at least two such pretty valid requests made in this thread :)

---

### Post by Ron_Callison on 2016-06-24
```
earl@earl-dell-e6400:~$ uname -a
Linux earl-dell-e6400 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
earl@earl-dell-e6400:~$ lsb-release -a
No command 'lsb-release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
lsb-release: command not found
earl@earl-dell-e6400:~$ lsb_release
No LSB modules are available.
earl@earl-dell-e6400:~$ 
```

```
earl@earl-dell-e6400:~$ sudo apt-get update
sudo: unable to resolve host earl-dell-e6400: No such file or directory
[sudo] password for earl: 
Ign:1 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy InRelease
Ign:2 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy Release
Ign:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:5 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main all Packages
Ign:6 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign:7 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign:8 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted i386 Packages
Ign:12 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted all Packages
Ign:13 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign:15 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:5 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main all Packages
Ign:6 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign:7 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign:8 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted i386 Packages
Ign:12 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted all Packages
Ign:13 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign:15 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:5 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main all Packages
Ign:6 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign:7 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign:8 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted i386 Packages
Ign:12 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted all Packages
Ign:13 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign:15 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:5 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main all Packages
Ign:6 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign:7 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign:8 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted i386 Packages
Ign:12 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted all Packages
Ign:13 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign:15 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted DEP-11 64x64 Icons
Ign:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:5 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main all Packages
Ign:6 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en_US
Ign:7 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main Translation-en
Ign:8 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 DEP-11 Metadata
Ign:9 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main DEP-11 64x64 Icons
Ign:10 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 Packages
Ign:11 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted i386 Packages
Ign:12 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted all Packages
Ign:13 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en_US
Ign:14 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted Translation-en
Ign:15 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted amd64 DEP-11 Metadata
Ign:16 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/restricted DEP-11 64x64 Icons
Err:3 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign:4 cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy/main i386 Packages
Ign:17 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                 
Ign:18 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable InRelease              
Hit:19 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Hit:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease             
Get:22 [http://apt.spideroak.com/ubuntu-spideroak-hardy](http://apt.spideroak.com/ubuntu-spideroak-hardy) release InRelease [2,539 B]
Hit:23 [http://dl.google.com/linux/talkplugin/deb](http://dl.google.com/linux/talkplugin/deb) stable Release                
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]  
Ign:22 [http://apt.spideroak.com/ubuntu-spideroak-hardy](http://apt.spideroak.com/ubuntu-spideroak-hardy) release InRelease       
Hit:27 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy InRelease                     
Hit:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease          
Hit:29 [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) utopic InRelease         
Fetched 97.0 kB in 5s (18.0 kB/s)  
Reading package lists... Done
W: The repository 'cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1) saucy Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://apt.spideroak.com/ubuntu-spideroak-hardy](http://apt.spideroak.com/ubuntu-spideroak-hardy) release InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 573E3D1C51AE1B3D
W: The repository 'http://apt.spideroak.com/ubuntu-spideroak-hardy release InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.
earl@earl-dell-e6400:~$ 
```


```
earl@earl-dell-e6400:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host earl-dell-e6400: No such file or directory
[sudo] password for earl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gconf libcdaudio1 libdirectfb-1.2-9 libmpcdec6 libslv2-9
  linux-headers-4.4.0-21 linux-headers-4.4.0-21-generic
  linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  lshw python3-software-properties software-properties-common
  software-properties-gtk
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 291 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 lshw amd64 02.17-1.1ubuntu3.2 [215 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 software-properties-common all 0.96.20.1 [9,428 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 software-properties-gtk all 0.96.20.1 [47.2 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-software-properties all 0.96.20.1 [19.6 kB]
Fetched 291 kB in 0s (397 kB/s)                       
(Reading database ... 309909 files and directories currently installed.)
Preparing to unpack .../lshw_02.17-1.1ubuntu3.2_amd64.deb ...
Unpacking lshw (02.17-1.1ubuntu3.2) over (02.17-1.1ubuntu3.1) ...
Preparing to unpack .../software-properties-common_0.96.20.1_all.deb ...
Unpacking software-properties-common (0.96.20.1) over (0.96.20) ...
Preparing to unpack .../software-properties-gtk_0.96.20.1_all.deb ...
Unpacking software-properties-gtk (0.96.20.1) over (0.96.20) ...
Preparing to unpack .../python3-software-properties_0.96.20.1_all.deb ...
Unpacking python3-software-properties (0.96.20.1) over (0.96.20) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160523-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Setting up lshw (02.17-1.1ubuntu3.2) ...
Setting up python3-software-properties (0.96.20.1) ...
Setting up software-properties-common (0.96.20.1) ...
Setting up software-properties-gtk (0.96.20.1) ...
earl@earl-dell-e6400:~$ 
```


OK, there you go vasa1

---

### Post by Geoffrey_Arndt on 2016-06-24
OK Mr. Ron . . . there was/_**is**_ a very valid reason why Vasa asked for that output. 

Often, newish Linux users mix repositories from different versions of Ubuntu, along with different sources (including PPA's & out of date media devices).   IF a program cannot be installed directly from THE official repo for the current version, then the sources file in /etc  needs to be scrutinized carefully, as download/install issues can happen easily , and trying to update your system from one version to another will fail.    New developments in package management will mitigate this considerably (snappy core), but for now one needs to be careful.

---

