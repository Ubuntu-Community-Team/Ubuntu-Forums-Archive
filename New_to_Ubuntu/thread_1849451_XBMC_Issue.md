---
title: "XBMC Issue"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by linuxaspirer on 2011-09-24
I am trying to install xmbc on my linux computer..

this is the error message I am getting

Fetched 16.5 kB in 3s (4,401 B/s)
W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


that does this mean?

---

### Post by papibe on 2011-09-24
Check this [thread]("http://ubuntuforums.org/showthread.php?t=1766855&highlight=xbmc"). You have 2 options: to do the 'maverick' trick or use the unstable  ppa.

Regards.

---

### Post by Lisiano on 2011-09-24
To answer the OPs question what it means, XBMC for some reason didn't add a Natty repo to their PPA, so yea, try using the Maverick one for now.

---

### Post by linuxaspirer on 2011-09-24
> **papibe said:**
> Check this [thread]("http://ubuntuforums.org/showthread.php?t=1766855&highlight=xbmc"). You have 2 options: to do the 'maverick' trick or use the unstable  ppa.

Regards.

Can you please explain me, I did not understand, linux is very new to me.

thanks

---

### Post by Lisiano on 2011-09-24
As said on that thread.
[quote="That thread"]Go to the Package Manager. Click Settings -> Repositories. Under “Other Software”, highlight the XBMC PPA and click Edit. For the distribution, change it to maverick.[/quote]

---

### Post by linuxaspirer on 2011-09-24
> **Lisiano said:**
> As said on that thread.

i am sorry I dont want to be redundant, I have change the repositories for both of them to maverick, then how can i install them, using software manager ?

---

### Post by papibe on 2011-09-24
Yes, although if you open the software center it takes a few seconds for the XBMC ppa to appear and be available for installation.

You can speed up the process a little bit if you run this before:
```
sudo apt-get update
```
Hope it helps,
Regards.

---

### Post by linuxaspirer on 2011-09-24
> **papibe said:**
> Yes, although if you open the software center it takes a few seconds for the XBMC ppa to appear and be available for installation.

You can speed up the process a little bit if you run this before:
```
sudo apt-get update
```Hope it helps,
Regards.


great worked out  very well thanks for every one.............

---

### Post by papibe on 2011-09-24
:p Great! Mark the thread solved when you have the chance.
Regards.

---

