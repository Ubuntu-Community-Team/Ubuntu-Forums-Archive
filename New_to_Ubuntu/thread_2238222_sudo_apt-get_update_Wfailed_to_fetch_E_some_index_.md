---
title: "sudo apt-get update W:failed to fetch E: some index files failed to download"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by william44 on 2014-08-06
Hi, 

Very new to Ubuntu. Currently running 14.04 and whenever I input 

sudo apt-get update

W: Failed to fetch [http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

From my understanding 404  Not Found means the packages no longer exist. Can someone tell me what I can do to retrieve these packages and give me a 'Barney-Style' break down of these messages so i can learn more about the way ubuntu operates as a system (ha...see what I did there)

---

### Post by Bashing-om on 2014-08-06
william44; Hi !

Welcome to system management ..In particular 3rd party software that your 'buntu has no control over.
Yep, that software does not exist - to this time - for trusty .
Paste into your browser address bar:
[http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/](http://ppa.launchpad.net/noobslab/apps-dependencies/ubuntu/dists/)
See, no listing for 'trusty' .

Disable that fetch source, and await for the author to catch up.

[INDENT][INDENT]all in the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-08-06
Software in Linux comes in packages. It does not matter if the software is a system library or an application it is a package as far as the developers are concerned. Packages depend on the existence of other packages in order to work. All these packages are held in archives called repositories. Each version of Ubuntu has its own set of repositories. The images in this link are very old but the content is relevant.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

When we open the Ubuntu Software Centre or open the Update Manager the utilities connect to the Ubuntu repositories of the version of Ubuntu that we are using. The packages in these repositories are trusted packages because the code has been audited to determine if the code is safe to run in Ubuntu.

Another way to install software in Ubuntu is for a developer to create a Personal Package Archive (PPA). If we install software from a PPA then we take responsibility for installing that software. When we set up a PPA Update Manager creates the URL address to link to the developer's archive or repository. If we add a PPA as a software source in Ubuntu 12.04 (code name Precise Pangolin) then Update Manager will create a URL address with the word *precise* in the address. If we add that PPA in Ubuntu 14.04 (code name Trusty Tahr) then the URL will have the word *trusty* as part of the address.

If the developer has created a PPA for 14.04 then we should not have a problem in installing the software. But if the PPA was created for Ubuntu 12.04 and has not been provided as a 14.04 PPA then we hit the problem that you have experienced because there is not a folder in the *trusty* repositories containing that package.

When we run Update Manager to check if there are updates to Ubuntu the utility will scan our list of software sources or repositories and then scan the repositories to identify which packages have replacements available in the archives. Then with our consent Update Manager will download and install the replacement packages. Unless we have URL addresses in our sources list that do not match a location on the server hosting the Ubuntu repositories.

If we choose to use a PPA as a software source or repository and the installation is successful then it is best if we then disable the PPA as it may interfere with Update Manager's attempts to establish a connection with all the locations on the server that are listed as Ubuntu software sources or repositories.

Regards.

---

