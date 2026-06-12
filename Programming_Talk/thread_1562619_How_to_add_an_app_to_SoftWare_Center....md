---
title: "How to add an app to SoftWare Center...?"
date: 2010-08-27
forum: Programming Talk
---

### Post by hakermania on 2010-08-27
Ok, let's say you, or a friend of yours has created a really cool app.
Where c an he send it in order to be added to the list of the apps in the Ubuntu SoftwareCenter?

---

### Post by tgm4883 on 2010-08-27
Once the app is packaged, it would need to be submitted to revu. (see both links below) Once it gets into the repositories, it would show up in the app center


[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)
[http://revu.ubuntuwire.com/](http://revu.ubuntuwire.com/)

---

### Post by hakermania on 2010-08-28
Ok, thx for the answer. And once the package is approved it goes into the Software Center?

---

### Post by nvteighen on 2010-08-28
> **hakermania said:**
> Ok, thx for the answer. And once the package is approved it goes into the Software Center?

Hm... only the most popular apps go there. It may go into the repos, though. 

(I assume when you say "Software Center" you mean "Software Center", the Ubuntu-specific UI interface used to add/remove programs easily and not Synaptic or aptitude or the repos in general)

---

### Post by Bachstelze on 2010-08-28
> **hakermania said:**
> Ok, thx for the answer. And once the package is approved it goes into the Software Center?

Not until at least the next release, and that's only if it is accepted before the feature freeze deadline.  A package that gets accepted now would not go into Maverick.

---

### Post by geirha on 2010-08-28
Put the package(s) in a [PPA](https://help.launchpad.net/Packaging/PPA). Then whoever wants to try it out, can add that repository to their list of repositories, and it'll be available in the software center.

---

### Post by Bachstelze on 2010-08-28
> **geirha said:**
> Put the package(s) in a [PPA](https://help.launchpad.net/Packaging/PPA). Then whoever wants to try it out, can add that repository to their list of repositories, and it'll be available in the software center.

And the we'll have [people complaining it is not in the repos]("http://ubuntuforums.org/showthread.php?t=1562895"). ;)  Unless there is a good reason not to, new packages should eventually be added in the repos, that's what they're for.  PPAs are only for packages that, for whatever reason, cannot get added to the repos.  They are surely a nice way to test a package, until it has been tested enough to get approved to the repos, but the package shouldn't stay in a PPA forever.

---

### Post by geirha on 2010-08-28
> **Bachstelze said:**
> And the we'll have [people complaining it is not in the repos]("http://ubuntuforums.org/showthread.php?t=1562895"). ;)  Unless there is a good reason not to, new packages should eventually be added in the repos, that's what they're for.  PPAs are only for packages that, for whatever reason, cannot get atted to the repos.  They are surely a nice way to test a package, until it has been tested enough to get approved to the repos, but the package shouldn't stay in a PPA forever.

So you mean users who want to try the package in 10.04 (or older releases) should go to the homepage and download unsigned debs manually?

---

### Post by Bachstelze on 2010-08-28
> **geirha said:**
> So you mean users who want to try the package in 10.04 (or older releases) should go to the homepage and download unsigned debs manually?

Read what I wrote before answering, please.

---

### Post by geirha on 2010-08-28
> **Bachstelze said:**
> Read what I wrote before answering, please.

I did, but your response was confusing, which is why I wanted a little clarification. The best way to provide the package for older releases (if that is wanted) is to use a PPA imo. Maybe my initial response was ambiguous too.

---

### Post by Bachstelze on 2010-08-28
> **geirha said:**
> I did, but your response was confusing, which is why I wanted a little clarification. The best way to provide the package for older releases (if that is wanted) is to use a PPA imo. 

Of course, that's what I meant when I said "PPAs are only for packages that, for whatever reason, cannot get added to the repos." Because the packages are for an older release is one of those reasons.

---

### Post by hakermania on 2010-08-28
> **Bachstelze said:**
> Not until at least the next release, and that's only if it is accepted before the feature freeze deadline.  A package that gets accepted now would not go into Maverick.
**before the feature freeze deadline**
What do you mean?

---

### Post by Bachstelze on 2010-08-28
> **hakermania said:**
> **before the feature freeze deadline**
What do you mean?

For each Ubuntu release, there is what is called a "Feature Freeze", usually about two months before release, after which development is focused on fixing bugs and no new features (like new packages) are added, because that would potentially create even more bugs (when the goal is to reduce them).

[https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)

For Maverick, the Feature Freeze was August 12th.

---

### Post by tgm4883 on 2010-08-28
FWIW, packages in PPA's are signed as well by the person who uploaded it. If you can't trust the person who put it on the PPA (usually the developer), you probably shouldn't be installing the package in the first place.

---

### Post by hakermania on 2010-09-10
Ok, so, I have fully build my .DEB package and has no errors with lintian. No .diff or .dsc file was generated. How do I generate them?

---

### Post by tgm4883 on 2010-09-11
> **hakermania said:**
> Ok, so, I have fully build my .DEB package and has no errors with lintian. No .diff or .dsc file was generated. How do I generate them?

you would use debuild -S -sa in the source package directory

---

### Post by fallenshadow on 2010-09-11
I know this might sound like a bit of a noob question... but what is the point of a .diff file?

or .dsc file?(whatever that is)

I have built .deb packages before but without using these things.

---

### Post by hakermania on 2010-09-11
Mee too, I've no idea what these are, but I'm not a pc-noob, just packaging noob --_--

In the source package directory? What do you mean? In the folder <package_name_1-1.0> or in th DEBIAN folder? Or am losing something?

---

### Post by tgm4883 on 2010-09-12
> **hakermania said:**
> Mee too, I've no idea what these are, but I'm not a pc-noob, just packaging noob --_--

In the source package directory? What do you mean? In the folder <package_name_1-1.0> or in th DEBIAN folder? Or am losing something?

You build inside the package name directory, not the debian direcory.  You don't want to change the upstream source (contained in the orig.tar.gz), but you may want to add patches to it. That is what the diff file is for. If you are building packages locally, you likely won't deal with the dsc nor diff files, but if you are pushing the source packages to a build server (like LP), then you will.

---

### Post by hakermania on 2010-09-12
When I give **debuild -S -sa**
it has the output error:
[B]root@MaD-pc:/home/alex/test/some_1.0-1# debuild -S -sa
debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
[/B]
But the changelog is over here
[B]root@MaD-pc:/home/alex/test/some_1.0-1/usr/share/doc/some# ls
AUTHORS  _*changelog.Debian.gz*_[/B]    **_*changelog.gz*_  copyright  wallpaper.png**

---

### Post by tgm4883 on 2010-09-12
> **hakermania said:**
> When I give **debuild -S -sa**
it has the output error:
[B]root@MaD-pc:/home/alex/test/some_1.0-1# debuild -S -sa
debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
[/B]
But the changelog is over here
[B]root@MaD-pc:/home/alex/test/some_1.0-1/usr/share/doc/some# ls
AUTHORS  _*changelog.Debian.gz*_[/B]    **_*changelog.gz*_  copyright  wallpaper.png**

inside the source folder you will need a debian folder. Inside that you will need a few files necessary for building the package.

I suggest you read the packaging guide  [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

---

