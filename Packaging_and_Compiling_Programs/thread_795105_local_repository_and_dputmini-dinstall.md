---
title: "local repository and dput/mini-dinstall?"
date: 2008-05-15
forum: Packaging and Compiling Programs
---

### Post by pablaasmo on 2008-05-15
I am trying to use pbuilder to build for different versions and got most of it working. But I have a small problem moving packages into my local repository. 

I have a local repository and in  [https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)
it says:

"For example if you set in your <app>-version/debian/changelog as distribution "hoary" the package will be moved into the hoary distribution."

In The policy manual it says that the "distribution" filed is a space separated list of distributions. 

But when using dput to install the newly created package it gives an error on the distribution value.

What I would like it to have a general changelog file that can be used to build for all dists without having to change the value in the changelog file before running 'pdebuild'. The dput should put it in the local repository based on the distribution value in changelog and a DIST environment value.

Does any one have an idea how I can do this without changing the changelog file before running 'pdebuild'.

I could of course have script change it using sed, but I would like to know of any one have another idea to solve this?

Per A.

---

