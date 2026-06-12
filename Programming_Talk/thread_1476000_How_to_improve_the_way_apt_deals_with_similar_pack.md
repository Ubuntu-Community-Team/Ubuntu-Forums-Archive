---
title: "How to improve the way apt deals with similar packages in the post install config?"
date: 2010-05-07
forum: Programming Talk
---

### Post by calsaverini on 2010-05-07
There's something about how apt-get do things that bothers me. 

Suppose I want to install 20 different latex packages. Apt-get would download each .deb which would contain the files that must be copied to the adequate directories and the post-installation script. 

In the case of latex packages, the post-installation config must run *texhash* to update the database of files for latex to work. This takes almost half of the installation time on my pc. Apt-get does it once for each package I install - which is a very dumb thing to do, cause running this just one time after all packages are installed would suffice. 

The same would happen if I try to (un)install kernel images for different versions of the kernel. Each time apt-get will run the grub configuration script, which could also be done only once. 

I never developed anything closely as complicated as apt. But it doesn't feel difficult to add a tag to each package that would cause some script to run after all packages with the same tag are installed. I never looked into apt's source to have any idea if this is feasible, and I don't even know if this is a critical thing to do - nobody I know ever noticed this as a problem.

Is there a reason to be like it is now? Is it worth/feasible to change it?

---

### Post by soltanis on 2010-05-07
I agree with you on that. Unfortunately, what you're proposing would break backwards compatibility with older package formats, or at the very least it would take everyone updating their packages for the idea to work, am I right?

The way this usually works is someone proposes a new feature, someone implements it and submits it against the existing sources, and then the developers/maintainers choose whether or not to accept it...

---

### Post by slavik on 2010-05-08
> **calsaverini said:**
> There's something about how apt-get do things that bothers me. 

Suppose I want to install 20 different latex packages. Apt-get would download each .deb which would contain the files that must be copied to the adequate directories and the post-installation script. 

In the case of latex packages, the post-installation config must run *texhash* to update the database of files for latex to work. This takes almost half of the installation time on my pc. Apt-get does it once for each package I install - which is a very dumb thing to do, cause running this just one time after all packages are installed would suffice. 

The same would happen if I try to (un)install kernel images for different versions of the kernel. Each time apt-get will run the grub configuration script, which could also be done only once. 

I never developed anything closely as complicated as apt. But it doesn't feel difficult to add a tag to each package that would cause some script to run after all packages with the same tag are installed. I never looked into apt's source to have any idea if this is feasible, and I don't even know if this is a critical thing to do - nobody I know ever noticed this as a problem.

Is there a reason to be like it is now? Is it worth/feasible to change it?
but can you guarantee that installing two similar packages runs the same exact post-install script?

---

### Post by nvteighen on 2010-05-08
First, you know apt-get is being deprecated in favor of aptitude in Debian and possibly Ubuntu (and other Debian derivatives) could walk down that path too in time, so maybe the place to propose this is not apt-get's development team, but aptitude's. (IIRC, aptitude does the same thing).

My objection, similar to slavik, is about modularity. Ok, you could introduce a trigger that makes APT run a certain script just a single time; using a "tag" system could help avoiding conflicts by having a unique tag for each unique script (maybe using the md5 hash of the script's code?), but the issue is that currently packages work (and are mantained) in a modular fashion, such that all information needed to install a certain package is contained in itself. A tag system would mean you know what the tag for a certain group of packages is... therefore, adding information that's external to package itself. Not even dependencies work this way.

I also think there are some issues to solve regarding this. For example, whenever you install a font-related package, the font cache has to be updated and sometimes that can be a slow process.

---

