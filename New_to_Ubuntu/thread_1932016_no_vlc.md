---
title: "no vlc"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-02-26
Hi, I uninstalled libqt from synaptic, and now i no longer have vlc. When I try installing vlc, it does not show up in the search results of synaptic.


When i try reloading package information, I get the following after some downlaods...

```
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFB4FA7E41D78D0CFailed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources  Hash Sum mismatch
Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages  Hash Sum mismatch
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_i18n_Index
Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources  Hash Sum mismatch
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Index](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index
Some index files failed to download. They have been ignored, or old ones used instead.
```

How do i fix these problems?

---

### Post by Gremlinzzz on 2012-02-26
try 

sudo apt-get update
sudo apt-get upgrade

and then

sudo apt-get install vlc

If you're getting any dependencies problem then run sudo apt-get -f install

---

### Post by Gremlinzzz on 2012-02-26
[http://blog.sudobits.com/2011/09/12/how-to-install-vlc-player-on-ubuntu-11-10/](http://blog.sudobits.com/2011/09/12/how-to-install-vlc-player-on-ubuntu-11-10/)



[http://wiki.videolan.org/Documentation:Play_HowTo/Installing_VLC#Debian](http://wiki.videolan.org/Documentation:Play_HowTo/Installing_VLC#Debian)

:popcorn:just in case

---

### Post by Gremlinzzz on 2012-02-27
Hi, I uninstalled libqt from synaptic, and now i no longer have vlc. When I try installing vlc, it does not show up in the search results of synaptic.

or reinstall  libqt:popcorn:

---

