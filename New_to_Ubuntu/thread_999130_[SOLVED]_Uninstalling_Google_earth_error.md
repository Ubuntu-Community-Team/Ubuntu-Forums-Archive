---
title: "[SOLVED] Uninstalling Google earth error"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by PranaNZ on 2008-12-01
I am trying to uninstall a bad install of Google earth.  When I rty and use the Synaptic Package Manager to perform this, I get the following partial message. " E: googleearth-4.2: Package is in a very bad inconsistent state - you should "  That's all the message!
What should I do?
using 8.04x64

---

### Post by halitech on 2008-12-01
try doing it in a terminal

```
sudo apt-get remove googleearth
``` and see if it works or at least gives us more of the error message

---

### Post by Het Irv on 2008-12-01
in the terminal run ```
sudo dpkg --configure -a
```


See:
[http://ubuntuforums.org/showthread.php?t=324478](http://ubuntuforums.org/showthread.php?t=324478)

---

### Post by PranaNZ on 2008-12-01
Thanks halitech,

This is what I got,

chris@chris-desktop:~$ sudo apt-get remove googleearth
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package googleearth is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  googleearth-4.2: Depends: googleearth-4.2-data (= 4.2.205.5730-0medibuntu4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I ran the apt -get -f install  and it allowed the SPM to get beyond the error message and reload google earth and all is working fine again.
Thanks for the quick reply, much appreciated.

---

### Post by halitech on 2008-12-01
glad to hear its working for you :) please mark the thread as solved so others will know as well :)

---

