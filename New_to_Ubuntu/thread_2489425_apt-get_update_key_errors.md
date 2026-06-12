---
title: "apt-get update key errors"
date: 2023-07-29
forum: New to Ubuntu
---

### Post by brian120 on 2023-07-29
I am trying to address these apt-get update issues to no avail.   I have removed the tor browser yet still it prompts that the key could not be updated.  I have tried to manually add the key server failure output.   Can someone point me in the right direction?

**bc@BC-Lair:~$ sudo apt-get update**
**Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease**
**Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                               **
**Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                                          **
**Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]                                                                                                                 **
**Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]                                                                                                                    **
**Ign:6 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable InRelease                                                                                                                                   **
**Hit:7 [https://repo.vivaldi.com/stable/deb](https://repo.vivaldi.com/stable/deb) stable Release                                                                                                                                     **
**Hit:8 [https://packages.microsoft.com/ubuntu/16.04/prod](https://packages.microsoft.com/ubuntu/16.04/prod) xenial InRelease                                                                                                           **
**Ign:9 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  InRelease                                                                                                                   **
**Get:10 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Release [1,487 B]**
**Get:11 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Release.gpg [287 B]**
**Ign:11 [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Release.gpg **
**Get:13 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease [2,812 B]**
**Err:13 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease**
**  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810**
**Reading package lists... Done**
**W: GPG error: [http://download.videolan.org/pub/debian/stable](http://download.videolan.org/pub/debian/stable)  Release: Detached signature file '/var/lib/apt/lists/partial/download.videolan.org_pub_debian_stable_Release.gpg' is in unsupported binary format**
**E: The repository 'http://download.videolan.org/pub/debian/stable  Release' is not signed.**
**N: Updating from such a repository can't be done securely, and is therefore disabled by default.**
**N: See apt-secure(8) manpage for repository creation and user configuration details.**
**W: GPG error: [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810**
**E: The repository 'https://deb.torproject.org/torproject.org focal InRelease' is not signed.**
**N: Updating from such a repository can't be done securely, and is therefore disabled by default.**
**N: See apt-secure(8) manpage for repository creation and user configuration details.**


Attempt to address they key.

**c@BC-Lair:~$ sudo apt-key adv --recv-keys --keyserver keys.ubuntu.com 74A941BA219EC810**
**Executing: /tmp/apt-key-gpghome.fIyNDJaZNt/gpg.1.sh --recv-keys --keyserver keys.ubuntu.com 74A941BA219EC810**
**gpg: keyserver receive failed: No name**

---

### Post by Xian on 2023-07-30
You do have some cross-release entries in your repo source list that need pruning. 
However, to answer to the error message directly ..... 

That VLC repo has not been updated since 2016.
It should be considered obsolete & removed from your source list.

For VLC install on Focal: [https://linuxconfig.org/ubuntu-20-04-vlc-installation](https://linuxconfig.org/ubuntu-20-04-vlc-installation)

---

### Post by ActionParsnip on 2023-07-31
```

sudo apt-key adv --recv-keys --keyserver keys.gnupg.net  74A941BA219EC810

```

---

### Post by brian120 on 2023-08-06
c@BC-Lair:~$ sudo apt-key adv --recv-keys --keyserver keys.gnupg.net 74A941BA219EC810
[sudo] password for bc: 
Executing: /tmp/apt-key-gpghome.NjITfZeIim/gpg.1.sh --recv-keys --keyserver keys.gnupg.net 74A941BA219EC810
gpg: keyserver receive failed: Server indicated a failure

---

### Post by brian120 on 2023-08-06
I addressed the majority of the errors by reinstalling gpg...however I still recevie the tor public key error.   I uninstalled Tor and I do not see this key in my 'other software' source list.

c@BC-Lair:~$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease          
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease         
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease       
Get:5 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease [2,812 B]
Err:5 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
Reading package lists... Done
W: GPG error: [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
E: The repository 'https://deb.torproject.org/torproject.org focal InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by brian120 on 2023-08-06
I also don't see the tor key  ring in the default key ring locations

[email]c@BC-Lair:/etc/apt/trusted.gpg[/email].d$ dir
google-chrome.gpg   ubuntu-keyring-2012-archive.gpg  ubuntu-keyring-2018-archive.gpg   vivaldi-33EAAB8E.gpg  vivaldi-C27AA466.gpg
microsoft-prod.gpg  ubuntu-keyring-2012-cdimage.gpg  videolan_ubuntu_stable-daily.gpg  vivaldi-4218647E.gpg
[email]bc@BC-Lair:/etc/apt/trusted.gpg[/email].d$ cd /usr/share/keyrings/
bc@BC-Lair:/usr/share/keyrings$ dir
ubuntu-advantage-cc-eal.gpg    ubuntu-advantage-esm-infra-trusty.gpg  ubuntu-advantage-ros.gpg	       ubuntu-cloudimage-keyring.gpg
ubuntu-advantage-cis.gpg       ubuntu-advantage-fips.gpg	      ubuntu-archive-keyring.gpg       ubuntu-cloudimage-removed-keys.gpg
ubuntu-advantage-esm-apps.gpg  ubuntu-advantage-realtime-kernel.gpg   ubuntu-archive-removed-keys.gpg  ubuntu-master-keyring.gpg

---

### Post by IcemanV9 on 2023-08-07
Since the Tor browser was uninstalled, then you need to edit the sources.list to remove "https://deb.torprojects.org/torproject.org" and save. It will not look for Tor signature anymore when you run "sudo apt update" command.

---

### Post by ActionParsnip on 2023-08-07
Seems you need to install the tor project keyring package
[https://ubuntuhandbook.org/index.php/2021/01/install-tor-tor-browser-ubuntu-20-10-20-04/amp/](https://ubuntuhandbook.org/index.php/2021/01/install-tor-tor-browser-ubuntu-20-10-20-04/amp/)

---

### Post by brian120 on 2023-08-07
Nothing looks to be tor related in my sources.list file.



 *deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted*

*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe*

*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse*
*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse*

*deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse*


*deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted*
*deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe*
*deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse*

---

### Post by brian120 on 2023-08-07
I just stumbled upon the key.

/etc/apt/sources.list.d  contained a list of files which I just had to remove 'tor' files from that directory.   Until now I had just been referencing sources.list file.   Ubuntu is now allowing me to peform the upgrade to 22.04.

---

### Post by ActionParsnip on 2023-08-08
Is the issue solved? If so then please mark as solved

---

