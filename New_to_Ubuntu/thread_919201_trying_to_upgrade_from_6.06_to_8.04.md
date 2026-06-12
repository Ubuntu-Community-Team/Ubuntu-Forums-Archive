---
title: "trying to upgrade from 6.06 to 8.04"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fignig on 2008-09-13
trying to upgrade my system back to hardy heron. having a bit of a problem. when i'm upgrading thru update manager this error keeps popping up

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed

not really sure what that means, but it keeps happening. any suggestions?

---

### Post by aysiu on 2008-09-13
Have you tried pasting these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
sudo dpkg --configure -a
gksu "update-manager -d" &
```

---

### Post by fignig on 2008-09-13
i think it would be something to do w/ the repositories b/c it keeps saying that some of the programs are not covered.

---

### Post by fignig on 2008-09-13
Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed


is what it keeps saying, and i did do those commands btw.

---

### Post by Perfect Storm on 2008-09-13
```
sudo dpkg --configure -a
```

---

### Post by mkvnmtr on 2008-09-13
My experience may not apply to you because I am on a powerpc Mac but I could never upgrade from 6.06. It seemed to be a lack of the right packages in the repositories. I finally had to do a clean install of 8.04.1.

---

### Post by shulmice on 2008-09-28
When I upgrade the install script cycles through the (en) fonts over and over again. If I shut it down my fonts are squares and I have to do a clean install of 6.06.1 from a live CD, the 8.04.1 alternative  upgrade does not work. I have tried sudo update-manager -d .
Any suggestions?

---

