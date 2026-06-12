---
title: "How to upgrade to 8.04.1 using CD?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by ARhere on 2008-08-05
Is it possible to upgrade from 8.04 to 8.04.1 using the install CD?  I have a PC with no/slow network connection.

-AR

---

### Post by st33med on 2008-08-05
8.04.1 is a stepping stone to prevent huge updates upon install of the CD. You should already have every update necessary for 8.04.1.

---

### Post by ARhere on 2008-08-05
> **st33med said:**
> 8.04.1 is a stepping stone to prevent huge updates upon install of the CD. You should already have every update necessary for 8.04.1.

I know, thats my point.  Lets say you buy a Dell with an early install of 8.04 on it and I have no internet or dial up.  Can I apply the updates using an 8.04.1 install CD???

-AR

---

### Post by ARhere on 2008-08-07
HELP!!!  Anyone?  I have had no luck.

-AR

---

### Post by finer recliner on 2008-08-07
if you already have 8.04 installed, you might as well just do the updates the old fashioned (update manager) instead of reinstalling the entire OS.

installing a 8.04.1 disc is optimal when starting from scratch.

---

### Post by Paqman on 2008-08-07
> **ARhere said:**
> I know, thats my point.  Lets say you buy a Dell with an early install of 8.04 on it and I have no internet or dial up.  Can I apply the updates using an 8.04.1 install CD???

-AR

Yes, if you put a disk in that contains package information, you'll get a popup asking if you want to use it as a repo. If it contained any packages that were a newer version than what you currently had, you'd be given the option to upgrade.

---

### Post by ARhere on 2008-08-07
> **finer recliner said:**
> if you already have 8.04 installed, you might as well just do the updates the old fashioned (update manager) instead of reinstalling the entire OS.

installing a 8.04.1 disc is optimal when starting from scratch.

You don't understand... I have several PC's at our church that have 8.04 and are fully configured with all of the software we need.  No one has been maintaining the updates since I have been gone, and now 500Mbs of update are waiting for them.  Since we are on a dialup, I figured downloading the updates are out of the question.

> Yes, if you put a disk in that contains package information, you'll get a popup asking if you want to use it as a repo. If it contained any packages that were a newer version than what you currently had, you'd be given the option to upgrade.

I tried that, and it did as you said.  However when I selected all updates and "apply", it still tried to connect to the internet for the updates.  I was unable to get apt-get to pull updates form the CD.

-AR

---

### Post by gjoellee on 2008-08-07
try it yourself...I am not really sure. If you have like 200 or more updates the live CD you downloaded wasn't 8.04.1

---

### Post by billgoldberg on 2008-08-07
> **ARhere said:**
> You don't understand... I have several PC's at our church that have 8.04 and are fully configured with all of the software we need.  No one has been maintaining the updates since I have been gone, and now 500Mbs of update are waiting for them.  Since we are on a dialup, I figured downloading the updates are out of the question.



I tried that, and it did as you said.  However when I selected all updates and "apply", it still tried to connect to the internet for the updates.  I was unable to get apt-get to pull updates form the CD.

-AR

Try unselecting all the repo's in "system -> administration -> synaptic package manager > settings > repositories" (also in third-party-software).

And only leaving the cd as a repo.

Press the reload button in synaptic.

Then run the update manager.

It should pull the updates from the cd and install them.

Afterwards restore the original repos you disabled and run the update manager again.

You should only have a fw mb of updates now since 8.04.1 came out.

--

I haven't tried this, but I'm pretty sure it will work.

---

