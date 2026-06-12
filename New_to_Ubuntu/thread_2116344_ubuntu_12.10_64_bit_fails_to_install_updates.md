---
title: "ubuntu 12.10 64 bit fails to install updates"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by camarodemon on 2013-02-15
hey guys im new to ubuntu  i didnt like windows 8 so i erased it and installed ubuntu.... f
im getting this error code when i try to install the updates that it has sorry if there is a thread already for this problem i just couldnt find it                       a
I says Failed to download repository information check your internet connection... i clearly am connected to the internet plz help thank you.


       W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs 
 , E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cariboo on 2013-02-15
Go to System Settings->Software Sources, and uncheck the CD-Rom entry, like in the screenshot.

Your error messages clearly states that it is trying to download the updates from the CD-Rom.

---

### Post by camarodemon on 2013-02-15
Thank you very much

---

