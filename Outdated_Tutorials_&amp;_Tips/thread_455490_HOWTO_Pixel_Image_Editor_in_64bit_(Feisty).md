---
title: "HOWTO: Pixel Image Editor in 64bit (Feisty)"
date: 2007-05-26
forum: Outdated Tutorials &amp; Tips
---

### Post by BIGtrouble77 on 2007-05-26
[Pixel Image Editor]("http://www.kanzelsberger.com/pixel/?page_id=12") is commercial software developed as an alternative to Photoshop and Gimp.  At the moment it costs $38, but has not yet reached a stable 1.0 release.  According to the developer, when the 1.0 milestone is reached, the price will effectively double.  Since the software is near completion (and quite stable), now might be a good time to purchase a license.

Anyway, this HOWTO should work with the demo version, but I have not tested it yet so I can't say for sure.  

The problem I came accross to get Pixel fully working on my 64bit system had to do mostly with some extra 32bit libraries.  If you force install the 32bit Ubuntu build, Pixel should load and work, but several libraries will be disabled (color management, spellcheck, and openexr). As a result, I highly suggest using the standard linux build. The developer also recommends using this version.

It appears that the 64bit demo version is the full program.  The licensed version, on the other hand, requires you to download the 32bit version and copy over some 64bit files from the site.  If you do that properly then the About Pixel area in the program will tell you that you are running x86-64cmt.

**PIXEL DEMO HOWTO BEGINS HERE ______________________________**

**Make sure you have the 32bit compatibility libraries first:**
```
sudo apt-get install ia32-libs ia32-libs-gtk linux32
```

**Download the 64bit build:**
[http://www.kanzelsberger.com/pixel/?page_id=4%2F&os=a3fc72f9e89216dc2f7d038a80f4776a&mail=](http://www.kanzelsberger.com/pixel/?page_id=4%2F&os=a3fc72f9e89216dc2f7d038a80f4776a&mail=)

Just **extract the archive** to your desktop for now.  It should create a Pixel folder.  Try going to the folder via command line and type:
```
 ./pixel
```
You should get an error similar to the ones I got here: [http://lossofcontrol.com/images/pixel/cmd.png](http://lossofcontrol.com/images/pixel/cmd.png)

This screenshot actually shows you all of the dependency issues I had to resolve.  Each time I resolved a dependency I reran ./pixel and solved the next.

The best tool for resolving these dependenchies is [http://rpmfind.net](http://rpmfind.net).  Even though we are not going to install the RPMs, it's easy to extract the library required and copy it over to our lib32 directory.

So the first dependency I had to resolve is libsane.so.1.  **Simply put libsane.so.1 into the search field and let rpmfind return the rpm's with that library file.**  You should get a result like this (note that this screenshot is for a different library): [http://lossofcontrol.com/images/pixel/rpmfind.png](http://lossofcontrol.com/images/pixel/rpmfind.png)

I highlighted the package I used in orange.  Generally, I used the 64bit compatibility fedora packages.  I'm pretty sure any i386 or x86_64 versions will work.  **Download the RPM to your desktop.**

At this point you need to extract the needed files in the RPM and copy them to your /lib32 directory.  

First open nautilus as su so that you have the right permissions:
```
sudo nautilus
```

**Navigate to /lib32**

Now push that window aside and** double click on the rpm you downloaded on the desktop.**  You'll notice that it will open up with archive manager.  This is good because we can uncompress just the files we need.  No use running alien on the RPM to convert it to a .deb.  This is much easier.

**Navigate through the directories of the archive to the lib directory** (I think most are: ./usr/lib). 

When you are in the lib directory you should see the file you need.  In my first case it was libsane.so.1. 

Here an important detail... in many cases the library you are extracting may be a link to another file.  Generally, that other file is a slightly different version, but a link to it is created so that you know what version you are using and other programs know where to find that file.  

**Make sure you extract both the file you are looking for and any alternate versions that may reside in the same directory.**  If you extract the file and it has a big X on the icon, you know you are missing the file it links to.  

**I extracted these file to the desktop** to ensure that I didn't have the problem described above.  Once the files looked good, **I dragged them into my nautilus window opened to lib32 as administrator**.  

When the files are copied **try running ./pixel again**.  Most likely the library error you got previously has gone away and a new one has presented itself.  **You'll have to go through this procedure for every dependency that needs to be met. ** The screenshot of the commandline above shows you that I had to resolve 7 dependencies.

When all dependencies have been met Pixel should load and look like this: [http://lossofcontrol.com/images/pixel/works.png](http://lossofcontrol.com/images/pixel/works.png)

You'll also notice that there should be **no dependency issues** like the ones you get with the ubuntu build.

I highly suggest moving the Pixel directory somewhere permanent after you get it all working.  I generally like putting programs like this in /opt.

This howto is simple, but I made it pretty verbose so that you can use this procedure for installing other 32bit software the same way.

If there are any errors or questions here please let me know.  This is my first howto so I'm curious how it goes over.

---

