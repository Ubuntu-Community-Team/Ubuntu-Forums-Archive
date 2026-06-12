---
title: "Samba share access"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-01-30
Hi friends,

Iam using ubuntu 10.04.
Iam having four systems, all are ubuntu 10.04.
I created a share folder, while creating, it asked to install samba service. I installed and run the following command "apt-get upgrade". after restarting system, i tried to access that folder. but i got the following error mes
"Cannot display location "smb://10.0.1.30/" "
"Failed to retrieve share list from server"
But i created a share folder in another system in same way, i could access that folder in all other 3 systems.
i checked, its all under WORKGROUP and i could ping.

Kindly  help me to solve friends!

---

### Post by pmohankumar on 2012-01-30
Hi,

I itself solved.
I stopped firewall, now its working.

---

