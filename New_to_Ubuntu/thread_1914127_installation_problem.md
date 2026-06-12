---
title: "installation problem"
date: 2012-01-23
forum: New to Ubuntu
---

### Post by bob525 on 2012-01-23
Have installed wubi and tried to boot from HDD - following message "missing modules [cat/proc/modules: is/dev]"
What does this mean and how do I fix it please?

---

### Post by androssofer on 2012-01-24
> **bob525 said:**
> Have installed wubi and tried to boot from HDD - following message "missing modules [cat/proc/modules: is/dev]"
What does this mean and how do I fix it please?

got this info from this thread: [http://ubuntuforums.org/showthread.php?p=11512374](http://ubuntuforums.org/showthread.php?p=11512374)

> The disk file C:\ubuntu\disks\root.disk, the main disk used for the Wubi install does not exist. Uninstall Wubi:

Windows Vista/7:
Control Panel>Programs and Features>Ubuntu

Windows XP/earlier:
Control Panel>Add or Remove Programs>Ubuntu


then you do:

> Try this and let us know if it works:

Download the desktop ISO:
[ubuntu 11.10 desktop .iso]("http://releases.ubuntu.com/oneiric/ubuntu-11.10-desktop-i386.iso")

Download the executable:
[wubi.exe]("http://releases.ubuntu.com/oneiric/wubi.exe") 

Place them both in the same folder, e.g. on the Desktop, and then run the executable file.

***note: the iso and wubi.exe are for the latest ubuntu (11.10), not sure which one you wanted.

---

### Post by Rubi1200 on 2012-01-24
Other versions available here:


[LIST]
[*]For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 
[*]For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 
[*]For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/) 
[*]For 11.10 use [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)
[/LIST]

---

