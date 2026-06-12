---
title: "Note about CRAN mirror and Hash Sum error"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by brewbuntu on 2012-05-04
Fixed a problem I was having today, and I thought that it might be helpful to post it for anyone else with a similar problem.

When running this line
```
sudo apt-get update && sudo apt-get upgrade
```

I got an Hash Sum error from one of my software sources. A lot of posts I've seen said to delete any addresses that give you this error from your list of software sources, but if the address for the software source has just been changed, then you can simply edit it in **Software Sources**. Keep reading if you want more detail.

The warning/error message in the terminal showed me the particular ftp address was a CRAN mirror. If you use the statistical programme R then you may be familiar with these... but it doesn't really matter if you don't know what this is. Basically, it's a repository (repo) that keeps that programme up to date. I WANT to keep that! 

I tried cutting and pasting the ftp address into Google. Turns out, that mirror slightly changed it's web address from 

[http://ftp.heanet.ie/mirrors/cran.r-project.org/bin/linux/ubuntu](http://ftp.heanet.ie/mirrors/cran.r-project.org/bin/linux/ubuntu)

to 

[http://ftp.ipv4.heanet.ie/mirrors/cran.r-project.org/bin/linux/ubuntu](http://ftp.ipv4.heanet.ie/mirrors/cran.r-project.org/bin/linux/ubuntu)

In other words, they added the "ipv4" between "ftp" and "heanet" in the address. I just opened **Software Sources**, clicked on **Other Software**, clicked on the two entries for the ftp address, click **Edit**, and added the ".ipv4." where it belonged. Problem solved, and I keep my CRAN mirror!

---

