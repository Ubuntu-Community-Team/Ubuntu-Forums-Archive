---
title: "Basic repository questions"
date: 2005-01-17
forum: Repositories &amp; Backports
---

### Post by mcollins on 2005-01-17
I had a couple questions regarding how repositories work. I read about the differences between the main, universe, and multiverse. Should I keep them all enabled in my sources.list file? When I install a package, I hope it installs the latest version that it can. I was worried that 2 different versions could exist, say one in the main and another in the universe or multiverse. If that was the case then I'd have to uncomment the repository with the version I didn't want, before I did my apt-get update. But hopefully just for those 3 repositories, this isn't an issue.

Another question is about dependent packages, for an application. I never install those dependent files. Yet when I install a package using apt-get install, the install goes smooth and the program functions fine! Does it actually install those dependent files automatically? If that's the case that's awesome.

In my sources.list I have:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

I commented the CD one out, and the source repositories too, since I don't plan on compiling my own packages, at least for now. Does that seem good?

Matt

---

### Post by valadil on 2005-01-18
What you've done so far is fine, although you can unclutter sources.list a little.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

That ought to work fine.  The url points to where the files live.  The next word is the distribution, usually it will be hoary or warty, and after that are different groups of packages.  I'm not totally sure what the difference between having multiverse instead of universe is, but both have packages the others don't so its generally a good idea to use both.

The reason apt-get is cool is because it downloads and installs all dependencies needed to get a package to work.  Other systems like rpm would tell you to manually install other packages, which in turn would give oyu more packages to locate and isntall.  This was called dependency hell.

---

