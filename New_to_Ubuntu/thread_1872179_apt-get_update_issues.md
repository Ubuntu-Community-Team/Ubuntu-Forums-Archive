---
title: "apt-get update issues"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by pierreyy on 2011-10-30
hey guy, every time i attempt to update my system these issues come up :


W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_atareao_atareao_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_atareao_atareao_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

any suggestions as to how i could fix this issue...

---

### Post by JRV on 2011-10-30
The PPA is not there.
Use synaptic and remove it.
open synaptic, click Settings=>Repositories then uncheck the PPA.
Next run:```
sudo apt-get update
```

---

### Post by pierreyy on 2011-11-06
thank you!

---

