---
title: "Screenshots scheme does not seem very &quot;Open&quot;"
date: 2011-06-01
forum: Packaging and Compiling Programs
---

### Post by windyweather on 2011-06-01
Where is the "open" in this process??

Ok Found the screenshots at [http://screenshots.debian.net/](http://screenshots.debian.net/)

But apparently this an "apple like" store where you must be "official" to have a screen shot of your application. Not an "Android" like store where you can be anybody to have a screenshot appear in the software center.

I'm very surprised by that.

With a few applications in source forge, I'm trying to make high quality packages for them including a screenshot. Is this the only way to get a screenshot to show up in the software center when my application is installed?

Just to be clear, when I go to the "upload" page, and begin to type in my package name, it refuses it. I presume this is because my application will be downloaded from Source Forge and is not in the "official" package list of the distros.

Not clear why, or whether, there is a way to put the screenshot in the package.

Anybody know if a poor, unofficial, software application developer like me can have a screen shot for his package?

boo hoo...

-ww

---

### Post by SevenMachines on 2011-06-03
To be honest, its not clear to me whether or not something like a ppa app can have its own screenshot. You might want to look at 
[https://wiki.ubuntu.com/PostReleaseApps](https://wiki.ubuntu.com/PostReleaseApps)
If your not looking to actually add the application officially you might want to look at the 'metadata' subsection of the above and see if you can fiddle with the 'XB-Screenshot-Url' section of your packaging control file to use an arbitrary url. I've never tried it, might work, might not. You might want to try ubuntu-motu on irc and see if they know

---

### Post by windyweather on 2011-06-03
Ok. First I've seen this. But wow.. .lots of new fields to fill out.

[https://wiki.ubuntu.com/PostReleaseApps/Metadata](https://wiki.ubuntu.com/PostReleaseApps/Metadata)

BUT WHERE"S THE BEEF???
Do I seem to be shouting?

What are the specs for the screenshot, and thumbnail?
Just drop some new names for some metadata fields and run shall we? We need max/min sizes, formats [PNG and what else or only that?]

Whatever happened to writing a spec and getting it out there for folks to find? I've been searching wikis and google and ubuntu docs and everything I could think of for packaging information and never seen this. Is this the spec, or does it assume we've seen the spec itself, but doesn't refer or link to the actual spec?

ANd I come back to my other comment about this being the Ubuntu Apple Store, rather than the Android store. Closed to normal folks who have published their applications in source forge, et al. Sure the web is cool and all of that, but this thing of screenshots being on the web means that if your system is offline at the moment installing packages from a disk then you don't have screenshots. They could have been in the package - at least optionally. That would have been open and would have worked when offline. Oh well, I guess this stuff was not widely reviewed by folks outside of the inner circle of folks with 24/7 internet access and accounts to build the system itself. They are talking about uploading the screenshot to the source control of the system. There are other folks who are making applications that do not live there, but live on source forge, or other source control systems.

> Create a bzr branch of lp:~commercial-ppa-uploaders/software-center/additional-screenshots 

I will test a package with this metadata pointing elsewhere for thumbnails and screenshots.

BTW, since software-center ignores Installed-Size as per this spec:
[http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Installed-Size](http://www.debian.org/doc/debian-policy/ch-controlfields.html#s-f-Installed-Size)

I'm still looking for the spec that says where software-center looks for the installed size of the app. I have put in a bug that calls out the fact that the sc ignores installed size.

Well at least I have a pointer to some new stuff.

- ww

---

### Post by windyweather on 2011-06-03
Here's the control file in the package:
```
Package: debipack
Version: 1.0
Architecture: amd64
Priority: optional
Section: devel
Installed-Size: 723
Depends: libqtcore4, libqtgui4
XB-AppName: DebiPack
XB-Icon: DebiPack
XB-Screenshot-Url: http://www.windyweather.net/wp/wp-content/uploads/2011/06/debipack-screenshot.png
XB-Thumbnail-Url: http://www.windyweather.net/wp/wp-content/uploads/2011/06/debipack-thumbnail.png
XB-Category: Development
Maintainer: Darrell Duffy < djduffy@windyweather.net >
Provides: debipack
Homepage: https://sourceforge.net/projects/debipack/
Description: DebiPack is a graphical front end for dpkg-deb package builder.
  DebiPack is a package builder that is designed to be easy to learn and
  easy to use. It saves a project file so that you can save the parameters 
  for rebuilding the package later, or save the project in source control.
  Debiback stores resized icons, and builds the desktop file so that your
  application appears in the menus of Ubuntu or other popular debian
  based Linux systems.
```

The software center on 11.04 does not display anything from the XB meta-data, including the Icon oddly enough. But it does display the installed size correctly now. I didn't see that this worked before. And there is a delay. If you run software center right away, then the application does not show up. but if you wait a few minutes and come back and check, it's there.

I'm still trying to figure out where the license and updates fields in software-center come from. They are not in this page:
[https://wiki.ubuntu.com/PostReleaseApps/Metadata](https://wiki.ubuntu.com/PostReleaseApps/Metadata)

So I'm not sure where that information is hiding.

Sigh.  ](*,)

-ww

---

