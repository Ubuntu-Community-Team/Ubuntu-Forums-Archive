---
title: "What is post installation size of ubuntu 14.04.1 LTS"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by jatin2 on 2014-08-16
i want to know how much size does ubuntu 14.04.1 LTS take after installation. Please give me almost exact figure.
Thank you

---

### Post by yancek on 2014-08-16
That information was available to you when you installed, telling you that you need a certain amount of free disk space.  I believe 14.04 was 6.3GB when I installed.

---

### Post by sotiris2 on 2014-08-16
Keep in mind that updates will also take up space. (packages are downloaded on disk and then uncompressed and copied to other places on disk)

---

### Post by coffeecat on 2014-08-16
A fresh install with no updates takes up about 3.3Gib, but that will grow rapidly as soon as you apply updates, install applications, and store data if you do not have a separate /home partition. Over and above the 3.3Gib you will need room for expansion and also consider that an installation in a partition more than about 90% full slows down and files will be subject to significant fragmentation. Why do you ask the question?

---

### Post by monkeybrain20122 on 2014-08-16
You can shrink by more than 0.5 G if you get rid of unneeded localizations(language packs)

---

### Post by uRock on 2014-08-16
In most of my installs I give the / partition 15GB. I don't have a whole lot of extra applications installed and the / partition is using 6.4GB. That is with me regularly removing outdated kernels.

---

