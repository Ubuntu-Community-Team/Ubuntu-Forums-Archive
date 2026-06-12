---
title: "Repackaging Upstream Packages and its consequence on receiving updates"
date: 2008-06-03
forum: Packaging and Compiling Programs
---

### Post by udit99 on 2008-06-03
Ok
So I asked this question [before]("http://ubuntuforums.org/showthread.php?t=816578")  but I did not clarify it enough. So Im gonna ask again, this time with more details.

So I need to repackage upstream packages. For eg. FireFox. The one standard way I've seen this being done is to get the source package, make your changes to it, diff it with the original to get a patch and then repackage it into a deb.

Now lets say I modify FireFox and repackage it and install it. Now what happens when the original FireFox package gets an update. Will it update my package too? How will it handle the changes that I made and the custom patch that I applied ?

Or am I posting in the wrong forum ? :-)
Thanks

---

### Post by stari4ek on 2008-06-04
apt-get thinks that repository has newer package than installed (your custom) alltime. And propose to update it with default package.
I'm interested in right technic for rebuilding packages from source and storing them in local repository for automatic updates.

---

