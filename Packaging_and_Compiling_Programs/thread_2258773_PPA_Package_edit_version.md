---
title: "PPA Package edit version?"
date: 2014-12-30
forum: Packaging and Compiling Programs
---

### Post by shojiimatsuro on 2014-12-30
Forgive me if this is the wrong place to be asking something like this, but I couldn't find a better area to post this question.

I'm trying to get my feet wet with PPA's in launchpad, and I have successfully set up my own. My problem is that I want to copy a package from another PPA and publish it on my own for Utopic. I was able to figure that out through the copy option, and it was successfully built. My problem is that while it's built for Utopic the "version" still claims it as Trusty. I can't for the life of me figure out how I can change the actual version of the package so it shows that it's a Utopic package, and not Trusty.

Is there a way to download the proper files for the package, and change the versions to represent the right release? How can I go about fixing this?

Thanks for your input and advice!

---

### Post by slickymaster on 2014-12-30
*Moved to the ***Packaging and Compiling Programs*** sub-forum*

---

### Post by schragge on 2014-12-31
If [this](https://launchpad.net/~shojiimatsuro/+archive/ubuntu/snes9x-gtk) is the package you're talking about, I don't see where it claims to be built for trusty. It states utopic everywhere: in package version, in changelog, and in .changes.

---

