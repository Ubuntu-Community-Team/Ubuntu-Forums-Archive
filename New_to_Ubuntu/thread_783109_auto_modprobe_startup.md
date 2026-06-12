---
title: "auto modprobe startup"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Sim777 on 2008-05-05
I'd like to have following commands start automatically when system boots up. What file can I modify and add those to? 


sudo modprobe cpufreq_userspace
 sudo modprobe powernow-k8
 sudo modprobe cpufreq_ondemand
 sudo modprobe ndiswrapper


Thank you kindly. 

Sim.

(I searched...but didn't find)

---

### Post by otrojake on 2008-05-05
The file is /etc/modules.  Edit that with whatever editor you choose and add each of those modules to the file.  You don't need to put in "sudo modprobe" before them, just the name itself.  For example > # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
cpufreq_userspace
powernow-k8
cpufreq_ondemand
ndiswrapper

---

### Post by otrojake on 2008-05-05
The file is /etc/modules.  Edit it with the text editor of your choice (gedit for example)```
sudo gedit /etc/modules
```You don't need to put in sudo modprobe before the names of the module in the file.  Like this:> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
cpufreq_userspace
powernow-k8
cpufreq_ondemand
ndiswrapper

EDIT:  Whoops, double post.  Got a database error on the first one so I didn't think it went through.  Anyone know how I can delete the first one?

---

### Post by Promaster91 on 2008-05-05
```

sudo gedit /etc/modules

```

Then add these commands.
```

cpufreq_userspace
powernow-k8
cpufreq_ondemand
ndiswrapper

```

Don't take out any that were there already!
More info at: [http://ubuntuforums.org/showthread.php?t=734536](http://ubuntuforums.org/showthread.php?t=734536)

---

### Post by Sim777 on 2008-05-05
Thank you. :) That worked perfectly.

---

