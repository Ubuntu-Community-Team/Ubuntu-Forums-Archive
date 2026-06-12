---
title: "Marking a package as not explicitly installed, but keep it as an installed dependency"
date: 2012-09-24
forum: Packaging and Compiling Programs
---

### Post by Zugzwang on 2012-09-24
Hi Everyone,

I've already posted the [following question]("http://ubuntuforums.org/showthread.php?t=2061851") in the "Installation & Upgrades" support category, but it might be going too much into the package-manager details so I'm trying here, too.

Due to a bad internet connection, I had to install a piece of software by downloading the two .debs and installing them with dpkg -i.

So I have a package A that depends on B, and I've installed them both by hand.

Now what I want is that if at some point, I remove A, then B gets flagged as a package that is no longer needed, and gets removed, too. How do I flag package B so that the package manager thinks that B is only installed because it is a dependency. Note that I don't want to remove A or B at this point, it is just that when I decide to remove A at some point, then B should be removed automatically as well (at least when I do apt-get autoclean).

Thanks!

---

### Post by tienlbhoc on 2012-09-24
[http://ubuntuofflineinstall.com/](http://ubuntuofflineinstall.com/)
or click to blog link.

---

### Post by SevenMachines on 2012-09-24
Have a look at 
```
$ apt-mark auto <package>
```or older apts use
```
$ apt-get markauto <package>
```Might be what you're looking for

---

### Post by Zugzwang on 2012-09-25
@SevenMachines: Thanks a lot. This is *exactly* what I was looking for.

@tienlbhoc: Thanks for your input. It was unfortunately a pay-for application from the pay-part of the Ubuntu software center that I was concerned with. Your solution thus wouldn't work. Also, it would mark all packages as manually installed, which was what I wanted to avoid (the dpkg option --force-depends might have fixed that, though - it is however undocumented, so I cannot check).

---

