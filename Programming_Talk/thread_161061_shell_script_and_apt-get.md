---
title: "shell script and apt-get"
date: 2006-04-16
forum: Programming Talk
---

### Post by adam.tropics on 2006-04-16
I am unsure of how the sources.list is 'prioritized' when using apt-get install.

What I have within the script is a local cd added to the sources.list, having backed it up. Then there is an apt-get instal yadayadayada;how can I be sure that locally stored files will be used over having to download. I am a bit stuck, because not all the packages on the cd will be the newest versions, so the repos would still be needed for some of the packages. I am wondering if copying the packages directly to the cache before install, and forgetting messing with the sources.list altogether may be the way to go.??

---

### Post by nagilum on 2006-04-16
Priorities of which packages are to be installed from various sources defined in sources.list are set with what's called *Apt-Pinning*. Have a look at this little intro: [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by adam.tropics on 2006-04-16
Interesting, thanks. However (there's always a 'however'! ) I am a bit confused over it because I really don't want to alter which versions of packages are installed at all, just which sources for those packages are used. I am actually wondering if the answer could be to give all the repos the same pin-priority, as then one would expect the local files to preferred over remotely hosted ones?

---

### Post by nagilum on 2006-04-16
Yes, this is also possible. I thought it was mentioned in the article, although I must admit I didn't actually read it. My bad. ;)
Besides the "release" match that is used in the article there are also others, like "origin". To prioritize all packages from your local repository use something like this:
```

Package: *
Pin: origin your.server.hostname
Pin-Priority: 999

```
There's also some in detail information in the apt_preferences manpage (search for "Pin"), for example how the Pin-Priority is interpretated by Apt (specific ranges have specific meanings and such subtleties).

---

