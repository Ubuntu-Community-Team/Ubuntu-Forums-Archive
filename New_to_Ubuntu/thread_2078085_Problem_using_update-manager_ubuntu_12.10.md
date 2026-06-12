---
title: "Problem using update-manager ubuntu 12.10"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by flavio_ on 2012-10-30
Hi guys. I try to update ubuntu 12.10 via update-manager, and the following error message pops-up:

Failed to download repository information

Check your Internet connection.

In detail, this is message: 

[HTML]W:Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/HTML]

Someone could help me with that. And yes, I'm a newbie.

---

### Post by newb85 on 2012-10-30
Why do you have the Ubuntu-X PPA set up?  The Ubuntu-X PPA isn't available for Quantal.  (In fact, there hasn't been any activity on that PPA since March.)

You can stop the error message by removing the PPA. Click the "Settings..." button in Update Manager.  Go to the "Other Software" tab.  Find the three entries with addresses matching the ones in your error message and either un-check or remove them.

---

### Post by NikTh on 2012-10-30
Correct. 

The x-swat ppa have no support yet for Quantal (12.10). 

So remove it , until the maintainers fix this. 

Thanks

---

### Post by flavio_ on 2012-10-30
> **NikTh said:**
> Correct. 

The x-swat ppa have no support yet for Quantal (12.10). 

So remove it , until the maintainers fix this. 

Thanks

Thanks, guys. "Problem" solved.

---

