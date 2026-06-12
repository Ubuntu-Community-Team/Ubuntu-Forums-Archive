---
title: "Oneiric Ocelot changelogs?"
date: 2011-08-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by aka120 on 2011-08-02
I've been testing out some of the Oneiric Ocelot daily builds in Virtualbox lately. Apart from the well known reported bugs most of it is working rather nicely so far.

I'm just curious if there are any change logs for these daily builds.

I've searched around for a while but couldn't come up with a changelog. The only thing remotely related to changes that I could find was here:
[https://lists.ubuntu.com/archives/oneiric-changes/](https://lists.ubuntu.com/archives/oneiric-changes/)

---

### Post by jbicha on 2011-08-02
No, the daily builds do not have changelogs. You'll just have to look at the changelogs for the individual software you are interested in.

---

### Post by aka120 on 2011-08-02
Oh ok, a bit of a dumb question but I thought I would ask anyways.

Thanks

---

### Post by jbicha on 2011-08-02
No, not a dumb question.

The daily builds are generally automated (although they can be stopped or extra builds can be pushed manually) and I don't think there's been an attempt to isolate out the changelogs for packages on the CDs.

---

### Post by meborc on 2011-08-03
you probably already know this, but for me the best way to get to changelogs is to go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and after searching for the software you are interested in (and in the correct source - oneiric in this example) click on changelog link on the right column

---

### Post by Starks on 2011-08-03
or use synaptic's changelog feature which is faster

---

### Post by meborc on 2011-08-04
> **Starks said:**
> or use synaptic's changelog feature which is faster

true, I forgot that still exists :)

---

### Post by MadCow108 on 2011-08-04
or zless /usr/share/doc/<package>/changelog.Debian.gz
or apt-listchanges

---

