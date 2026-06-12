---
title: "Search for apt-get installed programs!"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-12-01
Hello, there is a command like dpkg -l, to search all the programs installed with the apt-get command? or to find a file programa installed in the disk.. 
an option can be locate?
thanks

---

### Post by fr.theo on 2008-12-01
type this to find first:

sudo updatedb

locate (filename) "if you require a specific installed program"

then

sudo find / -name *.*>>(or the name of the file) -print

hope it helps

---

### Post by hellion0 on 2008-12-01
You can also get a list of all installed packages in Synaptic by opening it, then clicking on "Status", then selecting "Installed".

---

