---
title: "Handling duplicate package names in multi-release repos?"
date: 2019-04-30
forum: Packaging and Compiling Programs
---

### Post by Moptop650 on 2019-04-30
Howdy,

I've been writing a tool for managing apt repositories and had a question about the organization of files within a repo. Looking at [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/), all of the .deb package files are placed somewhere under /pool/, regardless of what release or architecture they're associated with. How are duplicate names handled with this layout?

Let's use the following package URL as an example: **http ://archive.ubuntu.com/ubuntu/pool/main/n/nginx/nginx-core_1.16.0-0ubuntu1_amd64.deb**

This contains nginx 1.16.0's executable binaries. Obviously these binaries are linked against libraries from other packages and so forth, all the way down to libc. Theoretically, you can install this package if you have all the dependencies. BUT, in the real world this is not always so - if I am using a very old release of ubuntu, then I am probably stuck with some old release of libc and changing it would be difficult or break my system.

What happens if I create a package containing the same nginx binaries of the same version, but built against the very old dependencies of my very old distro? The package name would be identical since there is no reason for any of the fields to change. Uploading this package to the repo would replace the original and cause problems for people expecting it to work with their distros running newer libc and other dependencies. 

Or - a more realistic example - today, we have 19.04 Disco Dingo, and let's say dingo contains nginx 1.16.0 from above. Fast-forward to October, and the 19.10 release of Ubuntu is being released. Obviously, it should have an nginx package available too. Nginx is a separate project from libc (or another dep), so let's say this new release will contain a different libc version. Nginx (hypothetically) hasn't released a new version so the newest nginx would still be 1.16.0. A new package would have to be built with the contained binaries linked against the new libc (or some other dependency). Same problem as above - the nginx package name doesn't change since nothing about nginx changed. How is this package distributed without breaking 19.04 in this hypothetical example?

To bring things home: I ask because I'm trying to determine how the repo management tool I've been writing should handle this sort of conflict. I suspect that Ubuntu uses a development process to circumvent this issue, but I can't rely on such things when writing a generic tool. I need to handle odd situations such as distributing the same version of a piece of software packaged for a dozen different ubuntu releases.

Having the single pool of packages makes sense for packages that are actually compatible with multiple releases; it promotes deduplication. Siloing them such that each release has a separate pool would not be difficult to implement, but I'd like to hear the hivemind's thoughts on the matter.

---

### Post by mc4man on 2019-05-05
> How are duplicate names handled with this layout?
By who?
Users of any particular Ubuntu release only see in their package manager packages targeted to their release, this is determined in most cases by the /debian/changelog entry at time of package creation.
(some rare packages are copied from one release to the next, see below

As far as package names, most times they are different per release, certainly if Ubuntu has patched the Debian source (package name will have ubuntuX in it). 
There are likely some rare cases where the source is the same, unpatched and package name remains the exact same. In such cases the deps are the same.. Example gdebi is the same package for 18.10 and 19.04.
Notice the changelog is the same for both cosmic and disco.
[https://packages.ubuntu.com/disco/gdebi](https://packages.ubuntu.com/disco/gdebi)

---

### Post by Moptop650 on 2019-05-06
> **mc4man said:**
> By who?

By the maintainers of the repo itself.

> **mc4man said:**
> =There are likely some rare cases where the source is the same, unpatched and package name remains the exact same. In such cases the deps are the same.. 

I'm asking about this, though in the scenario that the deps are *not* the same (and would conflict with the base system).

Anyhow, I did some hacking this weekend. It appears that as long as your Filename path in a repo's metadata is relative to the root of the repo, Apt doesn't care. So, I can solve my problem by using a path like "pool/bionic/f/foobar_1.0_amd64.deb" instead of "pool/f/foobar_1.0_amd64.deb" to separate the dists.

---

