---
title: "PSPP installation problem in Lubuntu"
date: 2018-04-22
forum: New to Ubuntu
---

### Post by panoskanellopoulos1 on 2018-04-22
Hey guys,

I'm trying to install PSPP but I can't find it neither in Lubuntu Software Center or Synaptic Package Manager. I tried this [https://www.youtube.com/watch?v=uoGFLWuDuYs](https://www.youtube.com/watch?v=uoGFLWuDuYs) but the research returned no results. $ sudo apt-get install pspp returns this: [B]Package pspp is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'pspp' has no installation candidate[/B]. :confused:

Any recommendations?

Thanks.

---

### Post by Holger_Gehrke on 2018-04-22
A search on packages.ubuntu.com shows that PSPP is only available on LTS releases (14.04, 16.04 and the upcoming 18.04). There is a PPA at [https://launchpad.net/~adamzammit/+archive/ubuntu/pspp](https://launchpad.net/~adamzammit/+archive/ubuntu/pspp) which offers PSPP for other versions of Ubuntu.

Holger

---

### Post by panoskanellopoulos1 on 2018-04-22
Thank you Holger. I will give it a try.

---

