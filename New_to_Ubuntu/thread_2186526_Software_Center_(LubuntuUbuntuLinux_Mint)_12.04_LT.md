---
title: "Software Center (Lubuntu/Ubuntu/Linux Mint) 12.04 LTS"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by shabuboy on 2013-11-07
Since all systems are based on Ubuntu 12.04 LTS. Do all software centers contain the same programs? Or one has more options than the others?
I know who you can install Ubuntu software center on Lubuntu and Mint. But wonder why. Only explanations is if there is a difference somewhere. But even then, if you find it to install, it will also install all required packages.

Anyhow, a bit confused...

---

### Post by ian-weisser on 2013-11-07
> **shabuboy said:**
> Since all systems are based on Ubuntu 12.04 LTS. Do all software centers contain the same programs?

Yes. *buntu flavors all use the same repositories, so the contents of Software Center will be the same.

---

### Post by vasa1 on 2013-11-07
Considering the Ubuntu Software Center (USC), Synaptic Package Manager, and the Lubuntu Software Center (LSC), I'd say the first has more "entries" than the others. These entries include a variety of "apps" and even books and magazines that can be purchased using your Ubuntu One account (or whatever it's called now).
Both Synaptic and LSC are "lighter" and quicker to load than USC. It's unclear whether LSC is being actively developed. And then of course, there's apt-get.

Edit: there are some apps which cost $0.00 but still can only be purchased (for $0.00), IIRC. I don't know more about that.

---

### Post by mastablasta on 2013-11-08
> **vasa1 said:**
> Edit: there are some apps which cost $0.00 but still can only be purchased (for $0.00), IIRC. I don't know more about that.

yes there are some like that. i think some games among others. though i am not sure why this is good, since it only creates work for acocunting (all those free of charge invoices....)

---

### Post by shabuboy on 2013-11-08
Thank you for the input!

---

### Post by buzzingrobot on 2013-11-09
> **shabuboy said:**
> Since all systems are based on Ubuntu 12.04 LTS. Do all software centers contain the same programs? 



All the software is in repositories on servers that the different "software center" programs access.  Each generates a catalog of the available packages and displays that to the user. 

The specific servers accessed by each program are determined by the contents of files in the /etc/apt directory.  

Ubuntu flavors like Lubuntu, Kubuntu and Xubuntu also maintain repositories of the packages that are specific to their distributions.  An Ubuntu derivative like Mint does the same. Because they all contain the Ubuntu repositories in their list of sources in /etc/apt, they all provide access to those same packages.

---

### Post by vasa1 on 2013-11-12
> **mastablasta said:**
> yes there are some like that. i think some games among others. though i am not sure why this is good, since it only creates work for acocunting (all those free of charge invoices....)
There's a "papercut" bug over here: 
[Some free applications looks like paid applications with price 0.00 and with buy button]("https://bugs.launchpad.net/hundredpapercuts/+bug/968974"). I read it but don't understand the "technicalities".

---

### Post by VMC on 2013-11-13
Wow, what a "papercut" that "free" is! I never even used or "bought" anything free before. It just confusing at best.

---

