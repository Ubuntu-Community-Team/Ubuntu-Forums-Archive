---
title: "After sudo apt-get update"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by rossjohn07 on 2013-05-28
After recently installing vuze to my laptop and entering the ```
sudo apt-get update && sudo apt-get install vuze
```

The terminal displays this message:

```
W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'precise/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.
```


There is also a red triangle with an exclamation point in the middle of it stating, the update information is outdated. Then when I try to check updates, it displays the ```
Failed to download repository information
```

Then when I click for details it says:

```
W:Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, W:Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/precise/Release  Unable to find expected entry 'precise/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Any reason why this might be happening or suggestions. I've tried going to the Tweak App and using the janitor to possibly clean up the apps, but the red triangle still seems to emerge. And I still can't seem to search for anything using Vuze.

---

### Post by deadflowr on 2013-05-28
If in precise, open the update manager and click on the settings button.

Then go to other software and uncheck the pmcenery ppas, as there are no precise repos for those.

Then look for anything that says cdrom ( usually in the top) and uncheck those.

Then exit and click check to run updates again.

---

