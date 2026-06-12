---
title: "Problems while installing Compiz Fusion"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Fuser77 on 2012-12-22
Hi, There!

Here I go again asking for some help... Sorry for bugging you!

I installed Compiz Settings Manager and then I tried installing Compiz Fusion.
When clicking on the icon in the dash nothing happened.

Finally I uninstalled both applications, reinstalled Ubuntu, reintalled only Compiz Fusion. Nothing happened.

I removed Compiz Fusion and tried out the following procedure:

t=481615[http://ubuntuforums.org/showthread.php?t=481615]("http://ubuntuforums.org/showthread.php?t=481615")

This is what happened:

sudo apt-get update
replies
E: Some index files failed to download. They have been ignored, or old ones used instead.

sudo apt-get remove compiz-core desktop-effects
replies
E: Unable to locate package desktop-effects

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
replies
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get install compizconfig-settings-manager # compizconfig-backends-* ?!
replies
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

sudo apt-get install compiz-fusion-*
replies
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help, I have no idea!

(No way of going back to Windows!!!)

---

### Post by ikt on 2012-12-22
Hey,

Just to let you know Compiz merged all together years ago.

[http://en.wikipedia.org/wiki/Compiz#Merge_of_the_Compiz_branches](http://en.wikipedia.org/wiki/Compiz#Merge_of_the_Compiz_branches)

No need to install compiz fusion anyone, since pretty much all the features are in Compiz configuration settings manager (CCSM) anyway.

:)

---

### Post by Fuser77 on 2012-12-22
Yes!
I don-t know what I did but now the CSSM shows me all the options...

ikt, I suspected something like that, but you confirmed it.
Thanks for replying!

---

