---
title: "Resigning .deb packages"
date: 2013-05-30
forum: Packaging and Compiling Programs
---

### Post by eswenson on 2013-05-30
I'd like to support the following workflow: 1) development group creates .deb package and signs with development gpg key.  2) development group can deploy to development APT repository.   3) QA group can test this package and if it passes tests can be "promoted" to production.  4) QA resigns the same .deb package (that has been installed on development machines from the development APT repository) with a "production" gpg key.  5) now, and only now, it can be deployed to a production APT repository and installed on production machines.  (In fact, the workflow would be more complex than this, but for the purpose of this forum post, this is sufficient).

I know how to create sign the package at debuild time.  How do you take an existing .deb package and resign with a different key?  

Also, when I build packages with debuild, I see output like the following:

     Finished running lintian.
     Now signing changes and any dsc files...
      signfile xxx_1.5.1758_i386.changes Eric Swenson (...) <...>


     Successfully signed changes file

Is the "signature" only in the changes file?  It looks like this is the case.  When the package is installed into the APT repository with a command like:

     reprepro -b /var/apt-repo includedeb xxx xxx_1.5.1758_all.deb

I'm able to install the package from the repo on other machines after having configured the signing key.  However, if the signature is in the changes file, and the changes file doesn't appear to be in the .deb archive, how is the signature being propagated to the repository with reprepro such that it is available at package installation time?

Any help would be appreciated.

---

