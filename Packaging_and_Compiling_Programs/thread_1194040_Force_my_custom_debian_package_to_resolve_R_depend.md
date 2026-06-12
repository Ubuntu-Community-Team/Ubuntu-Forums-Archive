---
title: "Force my custom debian package to resolve R dependency from specific repository"
date: 2009-06-22
forum: Packaging and Compiling Programs
---

### Post by paulig2001 on 2009-06-22
I've created a ubuntu/debian package that installs an application that depends on R. When installing I want the package to install R from the repository at:

deb [http://cran.uk.r-project.org/bin/linux/ubuntu](http://cran.uk.r-project.org/bin/linux/ubuntu) jaunty/

because this repository contains the up to date version of R, as opposed to the older version in the normal Ubuntu repositories. I've tried adding the package to the sources.list (see below) from the packages preinst script but it doesn't seem to work.

echo "deb [http://cran.uk.r-project.org/bin/linux/ubuntu](http://cran.uk.r-project.org/bin/linux/ubuntu) jaunty/" | sudo tee -a /etc/apt/sources.list
sudo apt-get update

Any ideas how I can force the use of this repository?

---

