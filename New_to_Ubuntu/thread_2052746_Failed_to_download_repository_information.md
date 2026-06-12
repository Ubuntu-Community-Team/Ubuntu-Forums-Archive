---
title: "Failed to download repository information"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by spa21788 on 2012-09-03
W:GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I have made no changes to my settings, nor have I upgraded anything...
Suggestions...? :(

---

### Post by oldos2er on 2012-09-04
To add the spotify repository's key, run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
```

You can remove the cdrom from your sources with ```
gksudo software-properties-gtk
``` Other Software tab, untick the boxes next to cdrom:
When you're done, run ```
sudo apt-get update
``` and there shouldn't be any errors.

---

### Post by lunalui on 2012-10-27
hello everyone,
I have a similar problem. In my update manager I can read the following message: 
[IMG]https://lh3.googleusercontent.com/-ptD-Yu4NW-A/UIvQIdCt35I/AAAAAAAAAUY/IrsmEejvb-8/s393/Screenshot+from+2012-10-27+14%3A12%3A31.png[/IMG]

so I click on check and get the following error message:

[I]Failed to download repository information

Check your Internet connection.[/I]

although my internet connection is working fine.

Here are the details

W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I've tried what suggested above but the  sudo apt-get update command end with this:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

any ideas??? thanks

---

### Post by jerrrys on 2012-10-27
> **lunalui said:**
> hello everyone,
I have a similar problem. In my update manager I can read the following message: 
[IMG]https://lh3.googleusercontent.com/-ptD-Yu4NW-A/UIvQIdCt35I/AAAAAAAAAUY/IrsmEejvb-8/s393/Screenshot+from+2012-10-27+14%3A12%3A31.png[/IMG]

so I click on check and get the following error message:

[I]Failed to download repository information

Check your Internet connection.[/I]

although my internet connection is working fine.

Here are the details

W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I've tried what suggested above but the  sudo apt-get update command end with this:

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

any ideas??? thanks

Those sources are either no longer offered or down at the moment.  So just use your software sources and uncheck them.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by lunalui on 2012-10-27
thanks a lot for your reply, that indeed fixed the problem for me (to be honest, in the meantime I had also found this help page [http://maketecheasier.com/fix-the-package-information-was-last-updated-days-ago-error-in-ubuntu/2012/06/22](http://maketecheasier.com/fix-the-package-information-was-last-updated-days-ago-error-in-ubuntu/2012/06/22) )

---

