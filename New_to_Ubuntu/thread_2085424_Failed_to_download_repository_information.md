---
title: "Failed to download repository information"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by GothicCard on 2012-11-18
I done something wrong.

I was trying to get the old version of Skype, as I had installed the new version and it was not working for me.

I put this in (know it is for older version of Ubuntu, but thought it might work)

**Installing Skype**

 Since Ubuntu 10.04 (Lucid Lynx), Skype is part of the Canonical partner repository. To install Skype add the [Canonical Partner Repository]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories"). You can do this by running the command 

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
Now I get this when I check software update; Failed to download repository information

DETAILS: E:GPG error: [http://archive.cononical.com](http://archive.cononical.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

How do I fix this, and is it possible to get the old version of Skype on Ubuntu 12.04 LTS

---

### Post by nagubhai on 2012-11-18
Select the best downloading server and change it new one.
 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by GothicCard on 2012-11-18
> **nagubhai said:**
> Select the best downloading server and change it new one.
 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Thank you nagubhai for quick reply, and yes it has worked

---

