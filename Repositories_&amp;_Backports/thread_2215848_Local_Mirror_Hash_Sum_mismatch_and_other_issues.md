---
title: "Local Mirror Hash Sum mismatch and other issues"
date: 2014-04-08
forum: Repositories &amp; Backports
---

### Post by Fatboy125 on 2014-04-08
Hello everyone, 
I am having some issues setting up a local mirror on one of my servers(obviously). I am setting up the mirror because I don't have very fast internet connection and don't want to wait 2+ hours for updates or network installs(exaggerated). I tried using apt-mirror but it wouldn't sync correctly for some reason, so I moved to using debmirror and as far as I can tell all the packages are synced like they are supposed to. The debmirror command I'm using is 

```
debmirror -a amd64 --nosource --progress -s main,multiverse,universe,restricted,main/debian-installer,universe/debian-installer,multiverse/debian-installer,restricted/debian-installer -h us.archive.ubuntu.com -d precise,precise-security,precise-updates,precise-backports -e rsync /srv/mirror/ubuntu
```

I have a symlink from /srv/mirror/ubuntu to /srv/html/ubuntu which is served with nginx. If I try using it on an existing server, after running apt-get update, I get 

```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatchW: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_restricted_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_main_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_multiverse_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_restricted_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise_universe_i18n_Index
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_restricted_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_main_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_multiverse_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_restricted_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-updates_universe_i18n_Index
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_restricted_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_universe_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_multiverse_binary-i386_Packages  Hash Sum mismatch
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_main_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_multiverse_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_restricted_i18n_Index
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/mirror1.domain.local_ubuntu_dists_precise-security_universe_i18n_Index
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

and if I use it for a network install I get to "Installing the base system" but it fails giving the following in syslog

```
base-installer: info: Found kernels ''
base-installer: error: exiting on error base-installer/kernel/no-kernels-found
```

One thing I noticed that was a little odd, but couldn't figure out was in the warnings I got after running apt-get update it was trying to download i386 Package files. In my debmirror command I specified only amd64.

If anyone needs more info please let me know I will be more than happy to get it. I have been working on this for 3 days and have ran out of things to search on google, any insight would be great. Thanks in advance.

PS 
I would like to only have the Precise 64-bit repo just to keep disk usage as low as possible but I do have a good bit of room to work with if needed.

---

### Post by Fatboy125 on 2014-04-09
Ok, the installer problem seems to have resolved itself. I guess it was just a bad sync or something, I don't know. I am still having the issue with apt-get update trying to get i386 Package files. It seems to work fine when I try to install packages.

Here is the output of apt-get update:
```
Hit http://mirror1.domain.local precise Release.gpgHit http://mirror1.domain.local precise-updates Release.gpg
Hit http://mirror1.domain.local precise-security Release.gpg
Hit http://mirror1.domain.local precise Release
Hit http://mirror1.domain.local precise-updates Release
Hit http://mirror1.domain.local precise-security Release
Hit http://mirror1.domain.local precise/main amd64 Packages
Hit http://mirror1.domain.local precise/restricted amd64 Packages
Hit http://mirror1.domain.local precise/universe amd64 Packages
Hit http://mirror1.domain.local precise/multiverse amd64 Packages
Ign http://mirror1.domain.local precise/main TranslationIndex
Ign http://mirror1.domain.local precise/multiverse TranslationIndex
Ign http://mirror1.domain.local precise/restricted TranslationIndex
Ign http://mirror1.domain.local precise/universe TranslationIndex
Err http://mirror1.domain.local precise/main i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise/restricted i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise/universe i386 Packages
  500  Internal Server Error
Hit http://mirror1.domain.local precise-updates/main amd64 Packages
Hit http://mirror1.domain.local precise-updates/restricted amd64 Packages
Hit http://mirror1.domain.local precise-updates/universe amd64 Packages
Hit http://mirror1.domain.local precise-updates/multiverse amd64 Packages
Ign http://mirror1.domain.local precise-updates/main TranslationIndex
Ign http://mirror1.domain.local precise-updates/multiverse TranslationIndex
Ign http://mirror1.domain.local precise-updates/restricted TranslationIndex
Ign http://mirror1.domain.local precise-updates/universe TranslationIndex
Err http://mirror1.domain.local precise/multiverse i386 Packages
  500  Internal Server Error
Hit http://mirror1.domain.local precise-security/main amd64 Packages
Hit http://mirror1.domain.local precise-security/restricted amd64 Packages
Hit http://mirror1.domain.local precise-security/universe amd64 Packages
Hit http://mirror1.domain.local precise-security/multiverse amd64 Packages
Ign http://mirror1.domain.local precise-security/main TranslationIndex
Ign http://mirror1.domain.local precise-security/multiverse TranslationIndex
Ign http://mirror1.domain.local precise-security/restricted TranslationIndex
Ign http://mirror1.domain.local precise-security/universe TranslationIndex
Err http://mirror1.domain.local precise-updates/main i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-updates/restricted i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-updates/universe i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-updates/multiverse i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-security/main i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-security/restricted i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-security/universe i386 Packages
  500  Internal Server Error
Err http://mirror1.domain.local precise-security/multiverse i386 Packages
  500  Internal Server Error
Ign http://mirror1.domain.local precise/main Translation-en_US
Ign http://mirror1.domain.local precise/main Translation-en
Ign http://mirror1.domain.local precise/multiverse Translation-en_US
Ign http://mirror1.domain.local precise/multiverse Translation-en
Ign http://mirror1.domain.local precise/restricted Translation-en_US
Ign http://mirror1.domain.local precise/restricted Translation-en
Ign http://mirror1.domain.local precise/universe Translation-en_US
Ign http://mirror1.domain.local precise/universe Translation-en
Ign http://mirror1.domain.local precise-updates/main Translation-en_US
Ign http://mirror1.domain.local precise-updates/main Translation-en
Ign http://mirror1.domain.local precise-updates/multiverse Translation-en_US
Ign http://mirror1.domain.local precise-updates/multiverse Translation-en
Ign http://mirror1.domain.local precise-updates/restricted Translation-en_US
Ign http://mirror1.domain.local precise-updates/restricted Translation-en
Ign http://mirror1.domain.local precise-updates/universe Translation-en_US
Ign http://mirror1.domain.local precise-updates/universe Translation-en
Ign http://mirror1.domain.local precise-security/main Translation-en_US
Ign http://mirror1.domain.local precise-security/main Translation-en
Ign http://mirror1.domain.local precise-security/multiverse Translation-en_US
Ign http://mirror1.domain.local precise-security/multiverse Translation-en
Ign http://mirror1.domain.local precise-security/restricted Translation-en_US
Ign http://mirror1.domain.local precise-security/restricted Translation-en
Ign http://mirror1.domain.local precise-security/universe Translation-en_US
Ign http://mirror1.domain.local precise-security/universe Translation-en
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main amd64 Packages
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/main/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/restricted/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/universe/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise/multiverse/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/main/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/restricted/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/universe/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/main/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/restricted/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/universe/binary-i386/Packages  500  Internal Server Error


W: Failed to fetch http://mirror1.domain.local/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  500  Internal Server Error


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

