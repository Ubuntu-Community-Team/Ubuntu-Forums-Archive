---
title: "Can't install Synaptic"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Nikhil1991 on 2012-02-17
I am new to Linux. I've installed Ubuntu 11.10 and since it doesn't have Synaptic Package Manager installed by default, i tried using 
 
**sudo apt-get install synaptic **from the terminal.

but i always keep getting this..

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
[/B]
what do i do? please help!

---

### Post by Cha0sBG on 2012-02-17
Try to install it from the Ubuntu Software center.

---

### Post by Nikhil1991 on 2012-02-17
I tried the Software Center too. I double-click on the Synaptic app there, it starts updating cache which never completes and i get this error message
**Failed to download repository information**
Check your Internet connection
 
and in the details..

W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_InRelease doesn't start with a clearsigned message, W:GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease: File /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_InRelease doesn't start with a clearsigned message, W:GPG error: [http://www.fbreader.org](http://www.fbreader.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5FC5445BA702101, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_i18n_Index
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Index](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-amd64_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Encountered a section with no Package: header
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.

It's not a network problem. I use a proxy and i'm sure i've configured it all right.

---

### Post by oldos2er on 2012-02-17
Have you tried running ```
sudo apt-get update
``` first?

---

### Post by Nikhil1991 on 2012-02-17
It seems my proxy was blocking some of Ubuntu's archives. I changed the address and it worked. thanks ppl.

---

