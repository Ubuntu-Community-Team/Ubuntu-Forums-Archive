---
title: "apt-get 404 errors"
date: 2005-03-15
forum: Repositories &amp; Backports
---

### Post by ke han on 2005-03-15
when running apt-get update, I get the following errors:

[FONT=Lucida Console]...
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
  404 Not Found
...
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  404 Not Found
...
[/FONT]

My sources.list is from the posting at [http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary)
I copy/pasted the lines from this wiki posting exactly...I'm guessing the error has to do with the following piece of my sources.list:
[FONT=Lucida Console]
## Uncomment after release to continue getting updates:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
[/FONT]

However, this is just as shown in the wiki page, so I'm at a loss...
any advice on the latest and greatest sources.list???

thanks, ke han

---

### Post by mike998 on 2005-03-15
Hoary isn't in release as far as I know.  Try commenting the line again and uncommenting when Hoary is officially released.
I'm not at home, so I can't tell you what my apt.sources list looks like.

---

### Post by lao_V on 2005-03-15
[QUOTE=ke han][font=Lucida Console]
## Uncomment **after** release to continue getting updates:
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary-updates main restricted[/font]
[/QUOTE]

You need to comment that line until hoary is relased, then uncomment to get the updates!!

---

