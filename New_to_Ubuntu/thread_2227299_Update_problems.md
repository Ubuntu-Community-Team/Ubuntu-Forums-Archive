---
title: "Update problems"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by Al_Burke on 2014-06-01
I've been getting a little red triangle in the top right corner, which says the update information is outdated. My system switches between saying there are updates and saying it is up to date. When I run "sudo apt-get update" I get this:

Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

Thoughts please?

---

### Post by farrinux on 2014-06-01
My guess is that those PPA's do not exist for your version of Ubuntu. I would check those PPA's to see if they have valid packages for your version.  If not then go to "Software Sources" and either remove them or uncheck them. If you are using a fairly recent version of Ubuntu when you close Software Sources it will update the package list.  If not you can do it from terminal with...........
```
sudo apt-get update
```

---

### Post by coffeecat on 2014-06-01
Did you only recently add the doctormo ppa to your sources? Have a look at these:

[http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/)

[https://launchpad.net/~doctormo/+archive/ppa](https://launchpad.net/~doctormo/+archive/ppa)

Not a single version of Ubuntu since Natty/11.04 and all of those listed are obsolete versions. According to the launchpad page the latest update to a package was 174 weeks ago - that's over 3 years. It sounds like an abandoned ppa.

---

### Post by Al_Burke on 2014-06-01
Yes to both of you. I guess we have to be careful with those PPAs... :)

Thanks for your help, problem appears to be solved!

---

### Post by DoctorMO on 2014-06-02
> **coffeecat said:**
> that's over 3 years. It sounds like an abandoned ppa.

That's not abandoned, just asleep and resting for 16.04 ;-) actually no one's been asking for updated packages so I'm thinking everyone's happy with their built-ins.

---

