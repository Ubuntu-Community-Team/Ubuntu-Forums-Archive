---
title: "selective apt-get upgrade package"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by LRT on 2008-11-14
i want to upgrade a package (backuppc). but it tells me its also going to upgrade the samba packages. its ok if it upgrades everything else just not the samba packages...

how do i prevent apt-get from doing this???

---

### Post by igknighted on 2008-11-14
[http://packages.ubuntu.com/intrepid/utils/backuppc](http://packages.ubuntu.com/intrepid/utils/backuppc)

Backuppc depends on samba, so I doubt you can update without the samba packages as well.

---

### Post by LRT on 2008-11-14
i should clarify, i already have samba 3.0.28a installed. this is what i don't want upgraded

---

### Post by igknighted on 2008-11-14
> **LRT said:**
> i should clarify, i already have samba 3.0.28a installed. this is what i don't want upgraded

How did you install samba?  And backuppc?

EDIT: Why do you not want to update samba?

---

### Post by LRT on 2008-11-14
i'm running into weird errors with samba 3.2.3 and backuppc 3.1. i know that samba 3.0.28a and backuppc 3.1 work good together because this is what i'm currently running. 

i currently have samba 3.0.28a and backuppc 3.0 on another machine. this is where i want to upgrade backuppc to 3.1 without upgrading samba. 

so i would like to know how i can use apt-get to upgrade backuppc 3.0 to 3.1 and not upgrade samba.

---

### Post by jamesrl on 2008-11-14
Try using synaptic, instead of apt-get.  You can select which packages to upgrade and also force versions (Ctrl-E)

---

### Post by igknighted on 2008-11-14
> **LRT said:**
> i'm running into weird errors with samba 3.2.3 and backuppc 3.1. i know that samba 3.0.28a and backuppc 3.1 work good together because this is what i'm currently running. 

i currently have samba 3.0.28a and backuppc 3.0 on another machine. this is where i want to upgrade backuppc to 3.1 without upgrading samba. 

so i would like to know how i can use apt-get to upgrade backuppc 3.0 to 3.1 and not upgrade samba.

Ok... download the .deb of 3.1.  Install all the dependencies of backuppc.  Then use dpkg to install the .deb with this command: ```
sudo dpkg --install --force-all <packagename>
```

---

### Post by LRT on 2008-11-14
> **jamesrl said:**
> Try using synaptic, instead of apt-get.  You can select which packages to upgrade and also force versions (Ctrl-E)

unfortunately, i'm not running a gui. so i can't use synaptic. i wonder if there is a command-line version of synaptic??? that would be nice.

---

### Post by LRT on 2008-11-14
> **igknighted said:**
> Ok... download the .deb of 3.1.  Install all the dependencies of backuppc.  Then use dpkg to install the .deb with this command: ```
sudo dpkg --install --force-all <packagename>
```

that makes sense, i'll try this, thanks!

---

### Post by LRT on 2008-11-14
i can't imagine there isn't a better way of doing this...

---

### Post by brycenesbitt on 2010-02-04
sudo apt-get update
sudo apt-get -u upgrade
(get list of packages then hit 'no')
sudo apt-get install xxxx yyyy zzzz

---

### Post by leorolla on 2010-05-20
I was looking for the same thing, an apt-get option to upgrade just one package.

There is a workaround though: sudo aptitude gives a terminal GUI.

---

### Post by Paqman on 2010-05-20
> **LRT said:**
> i can't imagine there isn't a better way of doing this...

You can set a hold on a package in APT, so that it won't be upgraded.
```
sudo echo packagename hold | dpkg --set-selections
```

---

### Post by leorolla on 2010-05-20
Setting holds is not really robust because different APT frontends may or may not respect it. If there are a few packages you don't want upgraded, the safest way is to set a pinning. ;)

But there may be another situation: you want to upgrade only a few packages from the -proposed or -backports repository and ignore all the others. For this situation I haven't found a command-line solution yet. :(

---

### Post by Nap_BlownApart on 2012-08-03
> **leorolla said:**
> 
But there may be another situation: you want to upgrade only a few packages from the -proposed or -backports repository and ignore all the others. For this situation I haven't found a command-line solution yet. :(

This is exactly what I want to do to update my ClamAV anti-virus database and engine

---

### Post by Elfy on 2012-08-03
Please start your own thread. 

Closed

---

