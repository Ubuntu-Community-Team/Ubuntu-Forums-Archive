---
title: "How to update Jenkins from war archive?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by bigblop on 2012-06-16
I have installed Jenkins ver. 1.424.6 using this guide:

[http://www.mabishu.com/blog/2012/04/17/setting-up-jenkins-in-ubuntu-precise-12-04-for-php-projects/](http://www.mabishu.com/blog/2012/04/17/setting-up-jenkins-in-ubuntu-precise-12-04-for-php-projects/)

but when I goto jenkins it says there is a new version:

"New version of Jenkins (1.447.2) is available for download (changelog)." 

If I press the download link it downloads a jenkins.war file approx. 46MB.

How do I update my current installation of Jenkins with that?

This page:

[https://wiki.jenkins-ci.org/display/JENKINS/Automated+Upgrade](https://wiki.jenkins-ci.org/display/JENKINS/Automated+Upgrade)

suggest to run:

aptitude update
aptitude install jenkins

but its seems a bit outdated. Is it not possible to update a Jenkins installation done with apt-get using a war file?

---

### Post by Frogs Hair on 2012-06-16
I don't know if you will be able to update using the newer version unless the application checks for and applies updates via the Ubuntu repository using the update manager.

If there is a maintained PPA that may be the way to go. Apt get has replaced aptitude, so the command is outdated unless aptitude is installed.

---

