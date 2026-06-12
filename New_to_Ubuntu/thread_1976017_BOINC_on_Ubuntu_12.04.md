---
title: "BOINC on Ubuntu 12.04"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by afz12 on 2012-05-08
I have 12.04 running on this notebook and going well. However BOINC doesn't seem to work on this version - I suspect BOINC is at fault not Ubuntu! However is there a work around?

---

### Post by oldos2er on 2012-05-08
I'm running v7.0.25 from [http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php) and it's working fine.

---

### Post by kmanley57 on 2012-06-12
I also had problems getting the Ubuntu package Boinc to run, but after I installed the shell script version from Boinc.berkeley.edu. I then replaced the executables/programs that were installed by the Ubuntu package, with the ones from the Boinc script install directory and the permissions errors I kept getting from the Ubuntu package was resolved!

So it looks like the Ubuntu package has a permissions problem and can not write into the /var/lib/boinc-client data directory.

Or at least the version I got did!! Two different installs both did this.

---

### Post by yyyc186 on 2012-06-16
Supposedly there is an updated boinc client which fixes the SETI computational errors among other things.  Is the newest version of boinc available in a PPA?  More importantly, has it been tested with SETI and 64-bit AMD?

---

