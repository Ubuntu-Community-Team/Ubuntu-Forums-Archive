---
title: "Ubuntu package versions - updating"
date: 2008-05-07
forum: Packaging and Compiling Programs
---

### Post by Outworlder on 2008-05-07
Hi guys,

I have a question regarding Ubuntu's policy for packaging and including newer versions of certain packages in the repository.

Of particular interest is the Chicken Scheme compiler. The version included in Hardy is the 2.5-1. That's really ancient - dozens of versions were released since then (currently 3.2.0).

The package says:

Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Davide Puricelli (evo) <evo@debian.org>

By that, I understand that the original version came from Debian (correct me if I am wrong). Launchpad's activity is really low for this package: almost non-existent.

So, what would it take to update this package? Are there any specific procedures that must be followed to get a newer version approved, or is this just a matter of lack of maintainers?

I am not sure forums are the correct way to address this, but wiki searches weren't very productive.

---

### Post by sas on 2008-05-10
> **Outworlder said:**
> Of particular interest is the Chicken Scheme compiler. The version included in Hardy is the 2.5-1. That's really ancient - dozens of versions were released since then (currently 3.2.0).

So, what would it take to update this package? Are there any specific procedures that must be followed to get a newer version approved, or is this just a matter of lack of maintainers?


Do you mean getting the package included in hardy or intrepid ?

For hardy:The stable release policy is here: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates). The package may be eligible for the backports repository, see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).

For intrepid then if the new version is in debian sid then it will be sync'd to intrepid, otherwise see [https://wiki.ubuntu.com/PackagingGuide/Complete#head-8cd153595a1a1369b0b65767a444e16b3036ff19](https://wiki.ubuntu.com/PackagingGuide/Complete#head-8cd153595a1a1369b0b65767a444e16b3036ff19) for a brief primer and join the #ubuntu-motu channel on freenode for help with that.

Generally if packages lag behind official releases it's down to not enough people caring about that package or due to the release date occuring when ubuntu is frozen.

---

### Post by Outworlder on 2008-05-13
> **sas said:**
> Do you mean getting the package included in hardy or intrepid ?

For hardy:The stable release policy is here: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates). The package may be eligible for the backports repository, see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).

For intrepid then if the new version is in debian sid then it will be sync'd to intrepid, otherwise see [https://wiki.ubuntu.com/PackagingGuide/Complete#head-8cd153595a1a1369b0b65767a444e16b3036ff19](https://wiki.ubuntu.com/PackagingGuide/Complete#head-8cd153595a1a1369b0b65767a444e16b3036ff19) for a brief primer and join the #ubuntu-motu channel on freenode for help with that.

Generally if packages lag behind official releases it's down to not enough people caring about that package or due to the release date occuring when ubuntu is frozen.

After reading some more about Ubuntu's policy, it seems that I'll have to get the package into Intrepid first. After it is included in Intrepid, then it is possible to ask for a backport into Hardy.

At least, that's how I understood the process.

I think it's not a matter of people not caring about Chicken - it is that many don't care about the package itself. When problems arise, the standard response in #chicken is to get the source and compile it. I think those people don't come back to report problems in the package.

---

