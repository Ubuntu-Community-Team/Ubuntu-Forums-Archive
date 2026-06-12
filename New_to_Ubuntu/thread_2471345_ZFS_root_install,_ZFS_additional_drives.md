---
title: "ZFS root install, ZFS additional drives"
date: 2022-01-27
forum: New to Ubuntu
---

### Post by snewby on 2022-01-27
I wanted to install 20.04 LTS zfs root on 2x nvme  striped but the installer currently only supports single disk so I installed on an SSD and created my nvme striped pool after the fact; no problems.

Is there a better way to do this that integrates this pool into the desktop environment?  The desktop has no problem showing the SSD capacity/file system but the nvmes 'do not exist' and the pool/datasets are only exposed as a folder mount.  I've seen guides on forcing a multidisk install but I imagine the outcome would be the same.

As a more general question, has anyone considered makings zfs datasets 'look different' both on the CLI and GUI?   ie with some special character prefix/suffix and/or different color in GUI.  It would be nice to see better zfs integration ie right-click 'add/delete dataset'.  As an experiment, I created a dataset from CLI then tried to delete it in destktop; it disappeared in the folder/gui but did nothing at the zfs level and reappeared after reboot.

Thanks

---

### Post by TheFu on 2022-01-27
I'm just brainstorming here ... 

All ZFS commands require root.
Desktop tools don't use root - or if they do, the pkexec and polkit gets involved ... which might not be the best idea.  
From earlier this week: [https://arstechnica.com/information-technology/2022/01/a-bug-lurking-for-12-years-gives-attackers-root-on-every-major-linux-distro/](https://arstechnica.com/information-technology/2022/01/a-bug-lurking-for-12-years-gives-attackers-root-on-every-major-linux-distro/)

In the current LTS, ZFS is marked as "experimental" for the OS and boot setup.  That might change in the next LTS. I don't know.  Without knowing for certain, I'd only use ZFS for data, not the OS and not booting. I'm not into experimenting with my production systems that have real data on them.

---

