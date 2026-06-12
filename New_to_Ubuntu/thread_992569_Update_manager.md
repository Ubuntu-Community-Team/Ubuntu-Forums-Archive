---
title: "Update manager"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Ross Copeland on 2008-11-24
I recently upgraded from Ubuntu 8.04 to 8.1.  I now get a "warning" symbol in my toolbar re updates, the text of which starts "The update information is outdated.  ......"

[INDENT][/INDENT]When I run check for updates at the end I get a message:
Could not download all repository indexes 

[INDENT]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

[INDENT]Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

Can someone suggest how I can correct this please - in simple, plain english terms please, not too technical for a non-nerd like me.

---

### Post by drs305 on 2008-11-24
Open synaptic, settings, repositories, third-party software, and untick the ubuntu CDrom. If this is checked, the original cd with which ubuntu was first installed must be in the machine or an 'failed to fetch' message will be generated. Unticking this will allow ubuntu to search other repositories without looking for the cd.

---

### Post by Bucky Ball on 2008-11-24
Could you go to

System->Administration->Software Sources->Third Party Sources,

... and see if you can find the culprits. They will probably be ticked. Untick 'em. This error is occurring as machine is looking for your 8.04 cd as a source. I'm guessing you upgraded to 8.10 inside 8.04 rather than re-installed the operating system from disk and this is left over.

---

### Post by Ross Copeland on 2008-11-24
Thanks drs305 & Bucky Ball
That seems to have solved the problem

---

