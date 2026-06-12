---
title: "Difference between installing over apt-get or over ppa ?"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-05
Hi,

I had installed a while back Mercurial on my Lucid ubuntu server like ```
sudo apt-get install
```.

When I did today a ```
sudo apt-get update 
```
and also ```
sudo apt-get upgrade
```

the version was still 1.4.3.  

When I checked their [website]("https://launchpad.net/~mercurial-ppa/+archive/releases?field.series_filter=lucid") though, I was surprised to see version 2.2.1.

I was badly out of date. Its also quite scary thinking about all security holes.

Is it therefore recommended to add their ppa to my server and this would enforce getting the latest update?

Thanks,

---

### Post by 2F4U on 2012-06-05
The Ubuntu repositories are not always up-to-date and have the latest software in it. It is common, that only bug and security fixes are added, but not major version updates.
If you added this third party ppa you would get the verion in the ppa, except that there are dependencies that cannot be fulfilled. However, keep in mind that third-party software may damage your server.

---

### Post by DingusFett on 2012-06-05
Yeah, I've noticed that too. The canonical repositories seem to just get security updates and not a lot else. A lot of things I have, I have added the dev's PPA so I get all the updates for them.

---

### Post by cortman on 2012-06-05
Keep in mind that part of the reason it uses older packages is because those older packages, 9 times out of 10, are more stable than the latest iteration. That's why Debian Stable is so rock solid, and by some standards, uses old software.

---

### Post by forrestcupp on 2012-06-05
Since you're using Lucid, you need to make sure they cover all their dependencies in their PPA. Most PPAs include all the necessary dependencies, but not all of them do. 

Before Gimp 2.8 came out and we were using a PPA for the 2.7 development version, their PPA didn't work with Ubuntu 11.10 unless you also added a couple of Gnome3 PPAs. It's usually not a problem, but since you're using a pretty old version of Ubuntu, you should check into the dependencies before you add the PPA.

---

### Post by Frogs Hair on 2012-06-05
Personal package archives are created by a user or group with a specific need who them shares the new or modified software with others. The software may not be stable and there is always some risk involved in using PPAS. I have had good luck with some of more well known and highly visible PPAS.

---

### Post by Houmie on 2012-06-05
Thanks for clarification guys. Now I understand how this works.

The best thing is picking the latest 12.04 version and create a new server on Amazon AWS, then I can add the PPA and have a peace of mind.

At the end of the day 12.04 is LTS for a reason and its time to update.


Thanks,

---

