---
title: "Could not download all repository indexes"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by emil jho on 2012-02-09
Hi, 
 I was trying to install the **gnome global menu **in my** ubuntu 10.10 maverick meerkat.**
I added 
"deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu maverick main "]("http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu%20maverick%20main")
and " deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu maverick main]("http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu%20maverick%20main")"
into my ppa in synaptic.
Now when I reload I am getting 

"**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  **404  Not Found**
Failed to fetch [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  **404  Not Found**
Some index files failed to download, they have been ignored, or old ones used instead."


What does this error exactly mean. Does it mean the source of global menu cannot be added because they've removed support for "meverick" since it has become old? Do I need to upgrade to a new version in order to install the global menu? ;)

---

### Post by Krytarik on 2012-02-09
> **emil jho said:**
> Does it mean the source of global menu cannot be added because they've removed support for "meverick" since it has become old?
Actually, that PPA never built/provided packages for Maverick 10.10, but you could try using the packages built for Lucid 10.04; since the code base of those both Ubuntu versions is nearly the same, it should actually work. Therefore, just replace "maverick" with "lucid" in the source addresses, obviously (btw., you most probably won't need the "deb-src" source; it's for pulling the source packages).

> **emil jho said:**
> Do I need to upgrade to a new version in order to install the global menu? ;)
Although you don't necessarily need to upgrade right now (depending on if the Lucid packages work for you, or you can live without Global Menu for now), keep in mind that Maverick's End of Life is scheduled for April this year ;-) :

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Regards.

---

### Post by emil jho on 2012-02-10
Thanks Krytarik. 
That worked :)

---

