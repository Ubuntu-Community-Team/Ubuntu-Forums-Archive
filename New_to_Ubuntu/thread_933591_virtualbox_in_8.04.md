---
title: "virtualbox in 8.04"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by mdraicch on 2008-09-29
Hi to all,

I have just got virtualbox going in 8.04 and loaded winXP, i'm not sure why the magazine writers write such good reviews about visualization, since nothing of any significance seems to work. But I have realized that the repository version is 1.5.6 and the current stable version for linux is 2.0.2.

Does anyone know if 8.04 will ever have this version?? or will I need to load ubuntu 8.10.

regards
muzza

---

### Post by lapubell on 2008-09-29
ubuntu does package freeze on their repos so most likley it won't have that version.

just add the virtual box repo to your package lists and install the same way you would normally (apt-get, synaptic, whatever...)

about halfway down: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
use the line for hardy.

---

### Post by mdraicch on 2008-09-30
> **lapubell said:**
> ubuntu does package freeze on their repos so most likley it won't have that version.

just add the virtual box repo to your package lists and install the same way you would normally (apt-get, synaptic, whatever...)

about halfway down: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
use the line for hardy.

Thanks lapubell, did as you said and all worked fine.

Regards
Muzza

---

### Post by Therion on 2008-09-30
Might be too late, but there are also two VERSIONS of Virtual Box.  One is the OSE (Open Source Edition (available in the repo)) and the other is the binary-version (NOT available in the repo).  The binary version is the one that supports using USB, so if that's important to you, you're going to want to download the .deb file for the binary version from the virtual box website.

Just tossin' that out there...

---

