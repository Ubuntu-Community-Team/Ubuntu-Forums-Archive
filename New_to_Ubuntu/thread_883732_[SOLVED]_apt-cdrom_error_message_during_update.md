---
title: "[SOLVED] apt-cdrom error message during update"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by andrewt522 on 2008-08-08
I am running Hardy 8.04.

Last night, I received notification that updates were available.  I clicked the red, down arrow on my panel, started to download the repositories and received an error with this detail:

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead. 

What is this and how do I fix?

---

### Post by markjensen on 2008-08-08
Not exactly sure what's going on, but fire up synaptic and check your repository sources through the menus.   See if the "cdrom" option is checked, which would incline synaptic/aptitude to check the cdrom for packages.  Generally you don't want to do this, as current versions are on the network.

---

### Post by drs305 on 2008-08-08
You will get this error if in Synaptic >Settings >Repositories you still have the cdrom option checked in the lower window. You must either uncheck the cdrom option or have the cd installed when you run synaptic. This will clear the message.

If you need to get the medibuntu key:
```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by andrewt522 on 2008-08-08
Outstanding!  Thanks drs305, it worked like a charm!

---

