---
title: "Need help migrating to Ubuntu"
date: 2016-08-30
forum: New to Ubuntu
---

### Post by Valrayne on 2016-08-30
Hello! 

I'm trying to migrate from Windows to Ubuntu but like everyone, I have certain applications and tools I need to be able to port over before I even bother trying. TBH i've been trying to move to Linux for ages but I always come up against deal-breaking lack of app support so i'm hoping this attempt will be successful this time. So far the requisite apps I require are:
[LIST]
[*]mkvtoolnix 
[*]firefox 
[*]keepass 
[*]plex 
[*]foobar2000 
[*]qbitorrent 
[*]sabnzbd 
[*]sonarr 
[*]vlc 
[*]couch potato 
[/LIST]

I've checked the above apps and it looks like some provide .deb's and others tar.gz's etc. which I can manually run from. So that's OK. But I also need to setup raid (2xraid 1's for 4 HDD's). At the moment I'm using Stablebit drivepool on Windows as it is basically raid but with a number of advantages (e.g. can survive both OS and hardware failure). However i've not found any equivalent for Linux. I guess I could switch to hardware raid via my mobo but if the mobo dies, than so too does my raid parity. I also need to be able to RDP from Windows machines (and idealy mobile as well) to this system as it will be headless (i.e. accessed entirely from a remote location - no peripherals will be attached). 

So i'm hoping I can get some advice on this.

---

### Post by grahammechanical on 2016-08-30
This any good

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Regards

---

### Post by ian-weisser on 2016-08-30
Migrating all applications and RAID at once without testing seems unwise.
Your Windows skills may lead you astray in ways you do not expect...particularly in Linux installs and upgrades.
Consider building a test system (often in a VM), adding one application at a time, and testing the workflow. Take copious notes. 

I found years ago that versioned backups, and good rebuild notes, provided uptime nearly as good as RAID. And much simpler.
VMs and snapshots are even easier, and trivial to restore for a mere torrent machine, media server, or backend fileserver.

---

