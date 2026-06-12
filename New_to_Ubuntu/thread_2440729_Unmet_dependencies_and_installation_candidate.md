---
title: "Unmet dependencies and installation candidate"
date: 2020-04-14
forum: New to Ubuntu
---

### Post by eddyarthur on 2020-04-14
Hello,

I'm trying to install Nord VPN and am met with the following problems as shown here:

The following packages have unmet dependencies.
 nordvpn : Depends: ipset but it is not installable
           Depends: xsltproc but it is not installable
           Recommends: gawk but it is not installable
E: Unable to correct problems, you have held broken packages.
eddy@eddy-ThinkPad-X220:~$ sudo apt get install ipset
E: Invalid operation get
eddy@eddy-ThinkPad-X220:~$ sudo apt install ipset
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ipset is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ipset' has no installation candidate


I have unmet dependencies: Ipset, xsltproc and gawk, but when trying to install them I'm told 'ipset', for exampke, has no installation candidate.

The command sudo apt update does not help.

Any help would be appreciated.

thanks,

E

---

### Post by Frogs Hair on 2020-04-14
It could be that  Nord vpn is not be compatible with the RC and you may have wait for Nord to update their package. This could happen sometime after the final release.

---

### Post by deadflowr on 2020-04-14
Run 
```
sudo apt update
```
post the results.

A quick guess, It would seem like the proper repositories aren't enabled, somehow.
ipset and gawk should be in the main repository, regardless of which Ubuntu release.

The output from the above command should give us a better idea of what's happening.

---

### Post by eddyarthur on 2020-04-15
Thanks, here they are when I run: sudo apt update:

```
Get:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [3,316 B]
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease                        
Hit:3 [https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable InRelease       
Err:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4773BD5E130D1D45
Reading package lists... Done
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4773BD5E130D1D45
E: The repository 'http://repository.spotify.com stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by deadflowr on 2020-04-15
Seems like Spotify and Ubuntu have a recurring key issue.
See: [https://community.spotify.com/t5/Desktop-Linux/Expired-Key-Signature/td-p/4534638]("https://community.spotify.com/t5/Desktop-Linux/Expired-Key-Signature/td-p/4534638")
[https://community.spotify.com/t5/Desktop-Linux/Repository-http-repository-spotify-com-stable-InRelease-is-not/td-p/4532249]("https://community.spotify.com/t5/Desktop-Linux/Repository-http-repository-spotify-com-stable-InRelease-is-not/td-p/4532249")

---

