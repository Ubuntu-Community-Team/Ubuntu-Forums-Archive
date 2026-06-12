---
title: "Building a Meta-Package from multiple compiled sources"
date: 2015-06-27
forum: Packaging and Compiling Programs
---

### Post by actionmystique on 2015-06-27
Hello all MOTU :p,

I've downloaded the sources of some packages, compiled, made and packaged them into different deb files. 

How can I build a meta-package that includes all these deb files to be able to install it on a separate system, with all the dependencies being resolved like they are when we use a package installer such as synaptic for example?

---

### Post by ian-weisser on 2015-06-29
A 'metapackage' means something specific in Debian/Ubuntu.

Are you trying to create a dummy package that simply *refers* to subordinate packages, but relies on the online package manager to actually download and install the subordinate packages?
(Example: The 'ubuntu-desktop' metapackage, which by itself does nothing, but depends upon dozens of packages that together provide a complete desktop experience)

Or are you trying to hand-carry your custom-built debs, with all their dependencies, to an offline system?
(Example: An Ubuntu 'click' or 'snappy' package, or an OSX .dmg)

---

### Post by actionmystique on 2015-06-29
If we use my [**Qemu/KVM & its manager document**]("https://plus.google.com/+jeanchristophemanciot/posts/eX9SzfoiZ14") as an example, I would like to offer a public PPA allowing people who have subscribed to it to download an up-to-date "kvm-and-manager" meta-package that would actually include all the compiled "sub-packages" described in the document.
These packages already exist on the official Ubuntu repositories but are usually old. The meta-package would offer the latest versions.
All the dependencies would have to be solved at the package manager level.
Is it possible and how?

---

### Post by ian-weisser on 2015-06-29
Seems like a metapackage is not needed at all.

If your version numbers are correct, then anyone who adds your PPA/repo *and* uses those packages will automatically update to your PPA/repo versions.
Apt (with the default settings in Ubuntu) cares about the version number, regardless of the source.

Do be sure your version numbers are not too high - the user should be able to upgrade back to the official Ubuntu version during their next release upgrade. If they cannot, their upgrade may fail due to your packages.

---

### Post by actionmystique on 2015-06-30
OK, but I have no knowledge about setting a PPA up.
What is the simplest way to do that?

---

### Post by ian-weisser on 2015-06-30
> **actionmystique said:**
> OK, but I have no knowledge about setting a PPA up.
What is the simplest way to do that?

Create an account at Launchpad.net.
PPAs are included with Launchpad accounts.
Generally, you create a new project (or a branch of an existing project) for your source code. Anyone can see your project/branch.
Then you tell Launchpad to build and package from that source for your PPA.

If the Launchpad workflow is inappropriate for your project, then you set up and host a third-party debian-style repository (which has it's one arcane voodoo to learn).
Perhaps you might find it simpler to help maintain those packages in Debian...then Debian does all that repo hosting for you, and all your work goes into the *official* Debian and Ubuntu packages.

---

