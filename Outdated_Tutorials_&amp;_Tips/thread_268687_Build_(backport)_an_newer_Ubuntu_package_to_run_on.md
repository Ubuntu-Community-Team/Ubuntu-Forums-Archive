---
title: "Build (backport) an newer Ubuntu package to run on an older Ubuntu version"
date: 2006-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-09-30
You are running the tried-and-true Dapper stable release. You notice that Edgy has a newer version of a package you want. What do you do? Well, prior to this, your would head over to the Backports folks and ask for the package. Some packages are deemed by Backporters to be too bleeding-edge or incompatible to be considered for backporting to Dapper. Now what? Welcome prevu! prevu is like your personal Backports developer, building backports with just a single command.

This is a quick guide to using prevu. We will use **gdebi** as an example package.


**1. Get Prevu!** Debs are available at [http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140)

**2. Edit your /etc/apt/sources.list**. You need a deb-src line for the development distro of Ubuntu, such as:
```

deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
```

Of course, run apt-get update afterwards.

**3. Initialize prevu.** You need to run **sudo prevu-init** when you install prevu for the first time. You don't need to run this again -- only the first time.

**4. Build package.** Run **prevu gdebi**
**5. Wait patiently.** Sit and twiddle your thumbs while your machine compiles away.

**6. When completed, look in /var/cache/prevu/edgy-debs**. There, you will find freshly generated deb packages! This location is also an APT repository, which can be added to your sources.list like so:
```

deb file:/var/cache/prevu/edgy-debs ./

```
Replace edgy with whatever distro you are running.


Note that not all packages will build. If you don't know how to fix it to build, you probably shouldn't try to do it, because chances are you'll screw up your computer :)

Also, note that building our own backports is an unsupported thing to do. Please do not bug Ubuntu developers about your broken system or packages if prevu could be the cause.


By default, prevu will build debs for the current distro version you are running. If you would like to build for another distro, just run, for example, DIST=breezy prevu gdebi. Note you need to run DIST=breezy prevu-init first.


**Filing bugs**
Prevu is hosted on Launchpad. Please file bugs to launchpad, product 'prevu'.

-----

Uninstallation:

Prevu does take up some space. Mine takes up around 100MB of space. Depending on how many packages you have, /var/cache/pbuilder/aptcache might be quite full, too. To remove prevu:

1. Uninstall the prevu package
2. Run **sudo rm -rf /var/cache/prevu**
3. Run **sudo rm /var/cache/pbuilder/aptcache/***

---

### Post by matthew on 2006-09-30
When I have free time I'll play around with it and will file any bugs I find on Launchpad. Thanks for doing this!

---

### Post by jdong on 2006-09-30
I have uploaded a new version of prevu that does not need the build command to be executed as root. This prevents malicious build scripts from screwing with your system.

Note the new .deb download link. After installing the update, run **sudo prevu-update** to effect the changes. Now, you can just do **prevu gdebi**, no sudo, but you need to be in the admin group.

Note that sudo is _still_ used to enter the build environment, but root access is dropped as soon as it's possible.

---

### Post by domino on 2006-09-30
Thanks for this tut! I was able to build gdebi but I'm not sure I got it to build correctly. Can anyone provide the MD5 for the two?

```
dcdd3ff33fd849bb2f2aca62a4772695  gdebi_0.1.6ubuntu1~6.06prevu1.tar.gz

f57d9a92178be9683ff4fe3bea3d7c2c  gdebi_0.1.6ubuntu1~6.06prevu1_all.deb
```

I'm also try to build the Edgy version of firefox-themes-ubuntu (2.0b2) but it keeps building the older firefox version. Any clue?

---

### Post by jdong on 2006-09-30
I get:
```

e32a3c1206811bdbb57276b066e7db03  gdebi_0.1.6ubuntu1~6.06prevu1_all.deb

```

As far as building firefox-themes-ubuntu, it seems like it first needs human-icon-theme. This is a two-step backport, and prevu 0.2.1 and below do not support it yet. Please wait for prevu 0.2.2 to be released.

Subscribe to bug [https://launchpad.net/products/prevu/+bug/63255](https://launchpad.net/products/prevu/+bug/63255) for notification.

**When upgrading prevu, you need to run "sudo prevu-update"**. You also need to run this command between two-step backports for the debs repository to refresh.

---

### Post by domino on 2006-09-30
Thanks for the prompt reply. It looks like I'm not building correctly since our checksum don't match. I'm thinking I'll need to retry the steps again. Thanks for the heads up on firefox-themes-ubuntu and I'll wait for an updated prevu version.

---

### Post by jdong on 2006-09-30
Our checksums don't have to match. The timestamps on all the files and changelogs are likely different, which will throw off your MD5. With prevu, I don't think you can do it wrong!

0.2.2 has been released, debs @ sourceforge. After installing, do prevu-update as described.


Note that firefox-themes-ubuntu still doesn't build, with error:
```

Fatal error: default theme source directory /usr/share/firefox/chrome/classic not found
make[1]: *** [all] Error 1
make[1]: Leaving directory `/tmp/buildd/firefox-themes-ubuntu-0.5.3~6.06prevu1/src'

```

This looks like a packaging bug. I will investigate.

---

### Post by domino on 2006-09-30
yea I updated prevu the second I saw the new build.

I can't seem to find your fatal error on my build. I had to pick a package that takes 15min to build ](*,) Anyway, after installing the theme package, firefox and swiftfox still does not support the theme.

If I can be of any help, just holler. I'm already running edgy on another box and I don't plan on upgrading this box any time soon.

> I don't think you can do it wrong!
So glad to hear that. :cool:

---

### Post by foxy123 on 2006-10-01
Hi jdong, it is very cool! Now I am thinking about staying with Dapper a wee longer. 

What about packages which are not in Dapper? I am trying to build brasero/bonfire and have the following error:
```
:~$ prevu brasero
Package brasero:
0.4.4-0ubuntu1 ==> 0.4.4-0ubuntu1~6.06prevu1
Continue? [Y/n]
Preparing source package for build...
Reading package lists... Done
Building dependency tree... Done
Need to get 1009kB of source archives.
Get: 1 http://archive.ubuntu.com edgy/universe brasero 0.4.4-0ubuntu1 (dsc) [1711B]
Get: 2 http://archive.ubuntu.com edgy/universe brasero 0.4.4-0ubuntu1 (tar) [1004kB]
Get: 3 http://archive.ubuntu.com edgy/universe brasero 0.4.4-0ubuntu1 (diff) [2729B]
Fetched 1009kB in 8s (115kB/s)
dpkg-source: extracting brasero in brasero-0.4.4
dpkg-source: unpacking brasero_0.4.4.orig.tar.gz
dpkg-source: applying ./brasero_0.4.4-0ubuntu1.diff.gz
dch warning: new version (0.4.4-0ubuntu1~6.06prevu1) is less than
the current version number (0.4.4-0ubuntu1).
W: /home/alex/.pbuilderrc does not exist
dpkg-checkbuilddeps: Unmet build dependencies: cdbs gnome-pkg-tools libnautilus-burn-dev (>= 2.14.0) libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libtotem-plparser-dev libgdl-1-dev libnotify-dev
W: Unmet build-dependency in source
dpkg-buildpackage: source package is brasero
dpkg-buildpackage: source version is 0.4.4-0ubuntu1~6.06prevu1
dpkg-buildpackage: source changed by alex <alex@localhost>
 fakeroot debian/rules clean
debian/rules:5: /usr/share/cdbs/1/rules/debhelper.mk: No such file or directory
debian/rules:6: /usr/share/cdbs/1/rules/simple-patchsys.mk: No such file or directory
debian/rules:7: /usr/share/cdbs/1/rules/utils.mk: No such file or directory
debian/rules:8: /usr/share/cdbs/1/class/gnome.mk: No such file or directory
debian/rules:9: /usr/share/gnome-pkg-tools/1/rules/uploaders.mk: No such file or directory
make: *** No rule to make target `/usr/share/gnome-pkg-tools/1/rules/uploaders.mk'.  Stop.
Traceback (most recent call last):
  File "/usr/bin/prevu", line 75, in ?
    do_build()
  File "/usr/bin/prevu", line 50, in do_build
    raise ValueError("Build failed.")
ValueError: Build failed.

```

---

### Post by jdong on 2006-10-01
To build that particular package, you need to have "cdbs" installed on your machine.

---

### Post by matthew on 2006-10-01
I have successfully packaged Liferea 1.0.23 as well as liferea-mozilla and liferea-gtkhtml. If you want I would be happy to send them to you to be uploaded...I don't have any place to post them myself.

BTW, liferea names the other two as dependencies and the other two each name liferea as a dependency. I couldn't install them using gdebi, but "sudo dpkg -i liferea*.deb" in the /var/cache/prevue/debs folder installed them all quickly and perfectly. Should I file this as a bug and if so against gdebi or prevue?

---

### Post by foxy123 on 2006-10-01
> **jdong said:**
> To build that particular package, you need to have "cdbs" installed on your machine.

Thanks a lot for your response. I got cautious about this tool. SOme Edgy packages have dependencies which are not met in Dapper. Other may require packages, which are in Dapper but not installed. Many people like myself may rush to compile all these from Edgy source as well rather than install them in a usual way. I am not sure if it is safe frankly speaking. Maybe you should put some warning in the howto, explain how to meet the dependencies and list packages which should not be updated?

---

### Post by jdong on 2006-10-01
This tool is fairly safe. As long as the package builds in the prevu environment, it should run in Dapper, unless there were Edgy-specific changes to the package. Don't pull any system administration tools or core system libraries, as those are often customized per-distribution.

If you find there are additional dependencies that you need after building the packages, use prevu to compile them. Don't just head over to packages.ubuntu.com and download an Edgy deb. NEVER EVER install an Edgy deb -- it's ok to compile from Edgy sources. It's NOT ok to install Edgy binaries.



Matthew, the problem you noted is indeed a gdebi bug. It's been filed, but no resolution yet. I personally recommend you add /var/cache/prevu/debs as an APT repository, such as:
```

deb file:/var/cache/prevu/debs ./

```

Then, you can use apt-get to install your newly prevu'ed packages. I uploaded a new 0.2.2-2 release today, which updates the Packages index on successful builds. Otherwise, you needed to run the time-consuming prevu-update for APT to see new packages.

---

### Post by foxy123 on 2006-10-01
I am trying to build a new Thunar and it complains about libexo being too old. Trying to build libexo complains about debhelper:
```
 -> Considering  debhelper (>= 5.0.37.2)
      Tried versions: 5.0.7ubuntu13
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
E: pbuilder-satisfydepends failed.

```

Trying to build a new debhelper gives me that:
```
Fetched 274kB in 2s (112kB/s)
dpkg-source: extracting debhelper in debhelper-5.0.37.3ubuntu1
dpkg-source: unpacking debhelper_5.0.37.3ubuntu1.tar.gz
cat: write error: Broken pipe
dch warning: new version (5.0.37.3ubuntu1~6.06prevu1) is less than
the current version number (5.0.37.3ubuntu1).
dch warning: your current directory has been renamed to:
../debhelper-5.0.37.3ubuntu1~6.06prevu1
W: /home/alex/.pbuilderrc does not exist
dpkg-buildpackage: source package is debhelper
dpkg-buildpackage: source version is 5.0.37.3ubuntu1~6.06prevu1
dpkg-buildpackage: source changed by alex <alex@localhost>
 fakeroot debian/rules clean
./run dh_testdir
./run dh_testroot
./run dh_clean *.1 *.7 *-stamp Debian/Debhelper/Dh_Version.pm
po4a --rm-translations --rm-backups man/po4a/po4a.cfg
make: po4a: Command not found
make: *** [clean] Error 127
Traceback (most recent call last):
  File "/usr/bin/prevu", line 75, in ?
    do_build()
  File "/usr/bin/prevu", line 50, in do_build
    raise ValueError("Build failed.")
ValueError: Build failed.

```

---

### Post by jdong on 2006-10-01
I don't recommend backporting debhelper -- that could lead to issues.

You've run into a package that won't easily backport to Dapper. You can try stripping the version requirement off debhelper (apt-get source libexo, cd into source, edit debian/control, run **prevu** with no arguments), no guarantees if that'll work or not :D

---

### Post by matthew on 2006-10-01
> **jdong said:**
> If you find there are additional dependencies that you need after building the packages, use prevu to compile them.I may try that this evening. I attempted to backport the newest Rhythmbox but it had a dependency issue. I don't recall what it is, but if it's something minor I'll play with it tonight.
> **jdong said:**
>  Matthew, the problem you noted is indeed a gdebi bug. It's been filed, but no resolution yet. I personally recommend you add /var/cache/prevu/debs as an APT repository, such as:
```

deb file:/var/cache/prevu/debs ./

```Then, you can use apt-get to install your newly prevu'ed packages. I uploaded a new 0.2.2-2 release today, which updates the Packages index on successful builds. Otherwise, you needed to run the time-consuming prevu-update for APT to see new packages.That's a great idea. Why didn't I think of it?

---

### Post by foxy123 on 2006-10-01
OK I am trying to build a new f-spot and ran into cli-comon-dev dependancy. I built cli-common-dev from Edgy souce and installed it:
```
:~$ apt-cache showpkg cli-common-dev
Package: cli-common-dev
Versions:
0.4.3ubuntu1~6.06prevu1(/var/lib/dpkg/status)

```

But f-spot still complains about dependency:

```
 -> Considering  cli-common-dev (>= 0.2.0)
W: Unable to locate package cli-common-dev
E: No packages found
      Tried versions:
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
E: pbuilder-satisfydepends failed.

``` :(

---

### Post by jdong on 2006-10-01
1) I would advise against mono backports, unless you intend on backporting all of mono (which would work). The mono packaging style completely changed from dapper to edgy to more match Debian's packaging, rendering the two incompatible.

2) You need to run sudo prevu-update after your cli-common-dev compile for prevu to realize the new package exists. Installing it on your system does no good, because prevu builds its packages in an isolated, clean environment.

---

### Post by foxy123 on 2006-10-01
> **jdong said:**
> 1) I would advise against mono backports, unless you intend on backporting all of mono (which would work). The mono packaging style completely changed from dapper to edgy to more match Debian's packaging, rendering the two incompatible.

2) You need to run sudo prevu-update after your cli-common-dev compile for prevu to realize the new package exists. Installing it on your system does no good, because prevu builds its packages in an isolated, clean environment.

thanks, noted. a new f-spot will wait until I upgrade to Edgy then.

Do you think I will be able to upgrade XFCE from beta to RC using prevu or it is too complicated?

---

### Post by xXx 0wn3d xXx on 2006-10-01
This is really cool. I have compilied and installed the following programs:

Prelink
Preload
Readahead
Sysv-rc-conf
Pbuilder
Gdebi

This is a very useful utility. I was windering if it would be possible to build gnome 2.6.16 with prevu or is it too risky/impossible ?

---

### Post by jdong on 2006-10-01
To answer the question about backporting entire desktop environments (GNOME, XFCE), I will lean on the pessimistic side and say that it likely won't work. XFCE has a better chance of working... you can try it :) .. but if you try to backport GNOME, following the dependency stack will more or less you resulting with a 75% "edgy", 25% dapper system, in which case you might as well upgrade to Edgy :)

---

### Post by foxy123 on 2006-10-01
> **jdong said:**
> To answer the question about backporting entire desktop environments (GNOME, XFCE), I will lean on the pessimistic side and say that it likely won't work. XFCE has a better chance of working... you can try it :) .. but if you try to backport GNOME, following the dependency stack will more or less you resulting with a 75% "edgy", 25% dapper system, in which case you might as well upgrade to Edgy :)

thanks for that. I also think  that xfce won't be a problem, though I guess it may be faster to upgrade to Edgy rather than compile all xfce packages :)

I am trying to backport banshee and run into this problem. The compiling stops with this:
```
//usr/lib -Wl,--rpath -Wl,//usr/lib
cc: //usr/lib/libsgutils.so: No such file or directory
make[3]: *** [hal-ipod-info] Error 1
make[3]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0'
make: *** [debian/stamp-makefile-build] Error 2

```

I've got libsgutils installed and I did prevu-update after that. However since this is a make error and as I understand the compiling happens in a separate clean environment I guess libsgutils are not present there. Ids there any way to get them into it? BTW, I am compiling libipoddevice-dev, which is a dependency for libipod-cil, which is a dependency for banshee :)

---

### Post by jdong on 2006-10-02
> **foxy123 said:**
> thanks for that. I also think  that xfce won't be a problem, though I guess it may be faster to upgrade to Edgy rather than compile all xfce packages :)

I am trying to backport banshee and run into this problem. The compiling stops with this:
```
//usr/lib -Wl,--rpath -Wl,//usr/lib
cc: //usr/lib/libsgutils.so: No such file or directory
make[3]: *** [hal-ipod-info] Error 1
make[3]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/tmp/buildd/libipoddevice-0.5.0'
make: *** [debian/stamp-makefile-build] Error 2

```

I've got libsgutils installed and I did prevu-update after that. However since this is a make error and as I understand the compiling happens in a separate clean environment I guess libsgutils are not present there. Ids there any way to get them into it? BTW, I am compiling libipoddevice-dev, which is a dependency for libipod-cil, which is a dependency for banshee :)
This is bug 62323 ([https://launchpad.net/products/dapper-backports/+bug/62323](https://launchpad.net/products/dapper-backports/+bug/62323)) in Dapper. A backport is in progress to fix this. You can do the backport using prevu yourself to speed up the process :D

P.S. "deb [http://apebox.org/badgerexplosion](http://apebox.org/badgerexplosion) ./" is a dapper repository with Edgy's mono stack, along with up-to-date versions of most mono apps. You can save some time by using that repository :)

---

### Post by jdong on 2006-10-02
> **xXx 0wn3d xXx said:**
> 
Readahead


Friendly reminder that after backporting readahead to do a profile boot, because readahead in Edgy is shipped with an Edgy list, which won't do you much good on Dapper!

---

### Post by StickyStyle on 2006-10-02
I need to make prevu use our local apt-proxy repo to get around our  slow internet pipe, what would be the proper way to get prevu setup this way?
Just looking at the way its working i would think i could un-tgz the base.tgz and edit the sources.list file in there and zip it back up.  But I am getting "tar: Error exit delayed from previous errors" when i try to un tgz the file ($tar zxvf base.tgz) and  If i just ignore the error, make my change and zip it back up i get dependency errors that i was not getting before.

Any hints?

---

### Post by jdong on 2006-10-02
My best recommendation is to edit the prevu-update script (/usr/bin/prevu-update), the line
```

pbuilder update --basetgz /var/cache/prevu/base.tgz --buildplace /var/cache/prevu/builds --distribution dapper --override-config --othermirror "deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse | deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse | deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse | deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse | deb file:/var/cache/prevu/debs ./" --bindmounts /var/cache/prevu/debs --distribution dapper

```

Replace the archive.ubuntu.com instances with your repository. Save this and remember to do this every time you install a new prevu update.

---

### Post by StickyStyle on 2006-10-02
Worked perfectly, thank you.
Just for the people who miss the obvious (like myself :-) ), you need to run prevue-update after making the changes and before trying to run prevue. Akin to doing an apt-get update after modifing your sources.list.

---

### Post by Hawkwind on 2006-10-02
Very nice work on this app.  I can see where it will make life easier for a lot of people, especially myself.

I currently run the largest 3rd party rpm repo for Mandriva and have been using Kubuntu since June 1st.  I have started adding stuff to my repo for Ubuntu, especially a big E17 repo.  I also have a contrib repo as well that I want to fill up.  

My main thing with the Mandriva stuff was just this, backporting from Cooker(their unstable/beta tree) to the latest stable version of the OS.  The site gets over 2 million hits a month and is very popular indeed.  I really want to increase the size of the Ubuntu stuff and this looks like a perfect way to do it.  A nice 3rd party backports repo that can be trusted :)  My repo can be found here:  [http://seerofsouls.com](http://seerofsouls.com)  It will hopefully be listed on easyubuntu or source-o-matic very soon if all goes as planned.

Now, my question is with the name tag of the final .deb package.  Here is an example of what it looks like when you finish building a package. I've used xchat in this example:

```
xchat_2.6.6-0ubuntu3~6.06prevu1_i386.deb
```

Is there anyway of shortening that ?  I understand that the 0ubuntu3~6.06 needs to be there due to the fact it needs to show as a backport and that's fine.  What I'm wondering is, is the 'prevu1' part something that can be customized ?  For example, when I build Mandriva rpm's for my SoS repo, the look something like this:

```
xchat-2.6.6-1.SoS.2006.0.i586.rpm
```

Is there a way I could replace the prevu1 part with .SoS or something of my own ? 

Also, is there a chance of getting that as an option to pass immediately after you run prevu xchat in this case ?  When it asks you to hit Y/N if everything is ok.  Would be kewl for the user to provide a label of their own.

Matthew - I think it was you who said you had built some stuff that you would like to have hosted somewhere.  Would you mind sending me all the stuff on a regular basis that you build ?  I'd love to put that stuff onto SoS as long as they are tested to work properly.  I of course would need the .deb files, the .dsc, .changes file and the .orig.tar.gz files for each app since I host both source and binary on my repo.  Maybe we could setup an rsync between us or something.  Feel free to email what you have now or just an email to discuss what we can do to get the files from you to me.  Email me at:  hawkwind AT gmail DOT com

---

### Post by jdong on 2006-10-02
The "~" tag is required for noting that the new version number is LESS than the original. This is required for successful future dist-upgrades.

The 6.06 is necessary so that in the even that a package is not updated from Edgy to Edgy+1, the backport still upgrades.


So unless you have a good reason for shortening the versions, I wouldn't recommend doing so.

Remember that the prevu script is done in Python. If you want it to use a different version tag, just load up the script in a text editor and do a replace-all :)


A more elaborate command-line parser with support for command-line arguments is certainly possible. I'll take a look at writing it.

---

### Post by foxy123 on 2006-10-03
> **Hawkwind said:**
> Very nice work on this app.  I can see where it will make life easier for a lot of people, especially myself.

I currently run the largest 3rd party rpm repo for Mandriva and have been using Kubuntu since June 1st.  I have started adding stuff to my repo for Ubuntu, especially a big E17 repo.  I also have a contrib repo as well that I want to fill up.  

My main thing with the Mandriva stuff was just this, backporting from Cooker(their unstable/beta tree) to the latest stable version of the OS.  The site gets over 2 million hits a month and is very popular indeed.  I really want to increase the size of the Ubuntu stuff and this looks like a perfect way to do it.  A nice 3rd party backports repo that can be trusted :)  My repo can be found here:  [http://seerofsouls.com](http://seerofsouls.com)  It will hopefully be listed on easyubuntu or source-o-matic very soon if all goes as planned.

Now, my question is with the name tag of the final .deb package.  Here is an example of what it looks like when you finish building a package. I've used xchat in this example:

```
xchat_2.6.6-0ubuntu3~6.06prevu1_i386.deb
```

Is there anyway of shortening that ?  I understand that the 0ubuntu3~6.06 needs to be there due to the fact it needs to show as a backport and that's fine.  What I'm wondering is, is the 'prevu1' part something that can be customized ?  For example, when I build Mandriva rpm's for my SoS repo, the look something like this:

```
xchat-2.6.6-1.SoS.2006.0.i586.rpm
```

Is there a way I could replace the prevu1 part with .SoS or something of my own ? 

Also, is there a chance of getting that as an option to pass immediately after you run prevu xchat in this case ?  When it asks you to hit Y/N if everything is ok.  Would be kewl for the user to provide a label of their own.

Matthew - I think it was you who said you had built some stuff that you would like to have hosted somewhere.  Would you mind sending me all the stuff on a regular basis that you build ?  I'd love to put that stuff onto SoS as long as they are tested to work properly.  I of course would need the .deb files, the .dsc, .changes file and the .orig.tar.gz files for each app since I host both source and binary on my repo.  Maybe we could setup an rsync between us or something.  Feel free to email what you have now or just an email to discuss what we can do to get the files from you to me.  Email me at:  hawkwind AT gmail DOT com

a community backport repo is what we need. Ubuntu security team is focused on security backports and Ubuntu backporting team on other critical backports, then a community backport repo could provide other less essential packages, which would be nice to have for many people.

I am going to backport xfce as it is a RC version in Edgy and I am not sure if xubuntu team has time to do it, they are pretty busy preparing the Edgy release. So I could put xfce debs in your repo if you do not mind. Though I am not sure when I will finish it. Maybe by the end of this week...

---

### Post by Hawkwind on 2006-10-03
> **foxy123 said:**
> a community backport repo is what we need. Ubuntu security team is focused on security backports and Ubuntu backporting team on other critical backports, then a community backport repo could provide other less essential packages, which would be nice to have for many people.

I am going to backport xfce as it is a RC version in Edgy and I am not sure if xubuntu team has time to do it, they are pretty busy preparing the Edgy release. So I could put xfce debs in your repo if you do not mind. Though I am not sure when I will finish it. Maybe by the end of this week...

That is great.  All I ask is that the packager tests them and verifies they work and tries to get a couple of others to test if possible.  I personally will test them as well before actually uploading them to SoS.  

Like I said, my repo has been very well trusted over the last 2 - 3 years with Mandriva and it seems a couple of the MOTU/Core-dev guys for Ubuntu like it as well which is why it's hopefully going to be added to source-o-matic soon.  The more packages I can get there, the better.  It only benefits all of us :)

Just email me when you have it ready and let me know how I can get them from you and we'll go from there.

---

### Post by jdong on 2006-10-03
A piece of advice to you, Hawkwind, from my personal experience with managing 3rd party repostories (backports up to hoary), continue to keep that link with Ubuntu devs (MOTU, etc). Adapt a packaging policy (i.e. look at the Backports policy) and make it known, and stick with it.


I'd like to see community backports allow the possibility of source modifications, namely debian/control to loosen build dependencies.

---

### Post by Hawkwind on 2006-10-03
> **jdong said:**
> A piece of advice to you, Hawkwind, from my personal experience with managing 3rd party repostories (backports up to hoary), continue to keep that link with Ubuntu devs (MOTU, etc). Adapt a packaging policy (i.e. look at the Backports policy) and make it known, and stick with it.

Where exactly can I find the backports policy ?  

I have strictly followed the Mandriva build policy from day one, so my plans are to do the very same with Ubuntu backports by all means.  IMO...it's the only way to do backports.  If you can't do them correctly, don't waste time :)

---

### Post by jdong on 2006-10-03
[https://launchpad.net/products/dapper-backports](https://launchpad.net/products/dapper-backports)

---

### Post by foxy123 on 2006-10-03
is there a prevu option to clean /var/cache? it is already over 500Mb...

---

### Post by jdong on 2006-10-03
Not currently, but it's simple to do by hand. Simply empty out /var/cache/prevu/builds/*, /var/cache/prevu/debs/* (if you don't want them anymore), /var/cache/prevu/src/*, and /var/cache/**pbuilder**/aptcache/*. That should bring you down to around 80MB of space usage.

Note that your next build (after emptying your aptcache) will have to re-download its dependencies from the web, which shouldn't matter that much, but will take a bit longer because of it :)

I am toying with the idea of joining pbuilder's apt cache with /var/cache/apt/archives, but I'm not sure if that's a good idea or not. I'll have to think that through.

---

### Post by foxy123 on 2006-10-03
> **jdong said:**
> Not currently, but it's simple to do by hand. Simply empty out /var/cache/prevu/builds/*, /var/cache/prevu/debs/* (if you don't want them anymore), /var/cache/prevu/src/*, and /var/cache/**pbuilder**/aptcache/*. That should bring you down to around 80MB of space usage.

Note that your next build (after emptying your aptcache) will have to re-download its dependencies from the web, which shouldn't matter that much, but will take a bit longer because of it :)

I am toying with the idea of joining pbuilder's apt cache with /var/cache/apt/archives, but I'm not sure if that's a good idea or not. I'll have to think that through.

cheers a lot

---

### Post by foxy123 on 2006-10-03
> **jdong said:**
> You can try stripping the version requirement off debhelper (apt-get source libexo, cd into source, edit debian/control, run **prevu** with no arguments), no guarantees if that'll work or not :D

will apt-get source get a Dapper rather than Edgy source?

EDIT: ok, it's Edgy. Could you be a bit more specific about editting the source. It's download in my /home. Should untar it, edit  and tar again? Also how will I make prevu to use the source from /home?

---

### Post by jdong on 2006-10-03
example:

apt-get source foo
cd foo-1.2/
vi debian/control


at this point, look for the Build-Depends line. For the offending build dependency, take off the specified version that's in parentheses. for example, "libbar-dev (>= 1.2.3-4)" becomes "libbar-dev".

save, then

prevu



Prevu will automatically use the extraced and modified sources to build.

---

### Post by foxy123 on 2006-10-04
> **jdong said:**
> example:

apt-get source foo
cd foo-1.2/
vi debian/control


at this point, look for the Build-Depends line. For the offending build dependency, take off the specified version that's in parentheses. for example, "libbar-dev (>= 1.2.3-4)" becomes "libbar-dev".

save, then

prevu



Prevu will automatically use the extraced and modified sources to build.

cheers, though I have to do
```
sudo prevu
```

Though my troubles did not end here :(

The next dependency is python-central as dh_pycentral is required to build libexo. I though that Dapper alternative is python-minimal but it is apparently not. Any idea what package provides dh_pycentral?

---

### Post by jdong on 2006-10-04
Hmm, run a sudo prevu-update, and then after that you won't need sudo to use prevu anymore (except for the prevu-update command... that still needs sudo)

---

### Post by foxy123 on 2006-10-04
> **jdong said:**
> Hmm, run a sudo prevu-update, and then after that you won't need sudo to use prevu anymore (except for the prevu-update command... that still needs sudo)

Thanks a lot. Any idea about python-central equivalent in Dapper?

---

### Post by jdong on 2006-10-04
I am not quite sure. That's probably why it build-depends on the newer debhelper, which has dh_pythoncentral.... I don't think Dapper has a python-central equivalent; that's a new style introduced in Edgy.

---

### Post by foxy123 on 2006-10-04
> **jdong said:**
> I am not quite sure. That's probably why it build-depends on the newer debhelper, which has dh_pythoncentral.... I don't think Dapper has a python-central equivalent; that's a new style introduced in Edgy.

does it mean that it is not possible to backport libexo-0.3 to Dapper?

---

### Post by jdong on 2006-10-04
Not without significant modifications to the packaging, no.

As I've said before, not everything backports :)

---

### Post by foxy123 on 2006-10-04
> **jdong said:**
> Not without significant modifications to the packaging, no.

As I've said before, not everything backports :)

it's a pity... I guess I will switch to Edgy then. I was toying with idae to stay with Dapper longer... But if xfce is not to be backported I'd rather change to Edgy. Frankly speaking I do not understand one thing. If Dapper is a "long time support" release, what is the point to change so many important things in Edgy that a lot of stuff is not easy to backport. How would want the long time support if a lot of apps are not possible to upgrade :-k

---

### Post by jdong on 2006-10-04
Well, dapper-backports is not a Canonical-supported repository anyway, so LTS really doesn't apply to -backports. LTS simply means the included packages get bugfix and security updates for a much longer period of time than the typical 18 months.

Backporting newer versions of applications to the release was never an intended goal of LTS.

---

### Post by foxy123 on 2006-10-06
I have managed to build exo after building python-central. My research has shown that it is separate package, sort of alternative to python-support and both happily live together in Edgy.

The question now is that to build python-central I had to backport po4a. Should I have instead tried to downgrade the version requirement in debian/control first? What is the proper way?

---

### Post by jdong on 2006-10-06
It all depends on why there is a tight build dependency on the package. Sometimes it's to fix a bug, or a new feature used during building. In that case, your build will fail if you push on without it.
Other times it's just to rebuild against something newer in Edgy. In that case, it's safe to take out the build dependency.

Sometimes digging through the package changelog (debian/changelog) is a good way to answer this questions. Other times, you just need to try :)

---

### Post by foxy123 on 2006-10-06
> **jdong said:**
> It all depends on why there is a tight build dependency on the package. Sometimes it's to fix a bug, or a new feature used during building. In that case, your build will fail if you push on without it.
Other times it's just to rebuild against something newer in Edgy. In that case, it's safe to take out the build dependency.

Sometimes digging through the package changelog (debian/changelog) is a good way to answer this questions. Other times, you just need to try :)
hi jdong, thanks for the answer. But if there are teo options available, which is preferable if any?

---

### Post by jdong on 2006-10-28
New -4 release posted for Dapper branch... It adds a new command, "prevu-chroot", which logs into a build environment and bind-mounts /tmp. In other words, you can run X11 programs from within a clean environment. For example, if I just backported gedit and want to test it, I'd do:

(1) sudo prevu-chroot
(2) apt-get install gedit
(3) gedit



Upon exiting, this test environment will destroy itself and life goes on :)

---

### Post by Angafirith on 2006-11-01
When Feisty development gets underway, will we be able to use the current version of prevu to backport from Feisty to Edgy? If not, will a new one be released for Edgy?

---

### Post by jdong on 2006-11-01
I am planning to make a Feisty version of prevu soon... basically all that's involved is replace all occurrences of dapper in the prevu scripts to edgy, and all edgy to feisty.

I'm considering making one version of prevu (likely gonna be 0.3 or 0.4) that is capable of taking in a -t flag for specifying which distro on the fly, but that adds more complexity to prevu than I'd like.

---

### Post by jdong on 2006-11-05
New prevu release 0.3, original post updated with new information. Basically, what's new is the ability to build against different versions of Ubuntu. By default, it'll build packages for your current version of Ubuntu, but that can be overridden with the DIST environment variable.


For example: You are running Edgy. All the prevu commands will be for building Edgy backports by default. However, you have a Dapper system you want to build packages for. You can run:
```

DIST=dapper sudo prevu-init
DIST=dapper prevu packagename

```
Then, Dapper packages will show up in /var/cache/prevu/dapper-debs. Note that you only need to run prevu-init once per distro version.


The /var/cache/prevu directory layout has changed slightly to accomodate this new feature, so if you're upgrading, you're recommended to **delete /var/cache/prevu** and re-initialize prevu.

---

### Post by jdong on 2006-11-06
Follow-up 0.3.2 released;

The notable new feature is the ability to specify a .dsc file to build. This can either be a local file (i.e. you downloaded the .dsc, .orig.tar.gz, and the .diff.gz from somewhere) or a URL (such as the .dsc links you find on packages.ubuntu/debian.org when you search for a source package) to the .dsc file.

---

### Post by zenrox on 2006-11-08
and you have 4.1 ver that does what now

---

### Post by jdong on 2006-11-08
[https://launchpad.net/people/ubuntu-backporters/+branch/prevu/dev](https://launchpad.net/people/ubuntu-backporters/+branch/prevu/dev)

Usually the bzr branch changelog can answer those questions....

It's a non-important upgrade to users, the internal code was rewritten to be more organized for easier maintainability.


BTW, prevu will be entering Universe soon :)

---

### Post by zenrox on 2006-11-08
sweet

---

### Post by jdong on 2006-11-08
I rebuilt and re-posted version 0.4.1-0ubuntu1 on Sourceforge. This new release fixes two significant issues, and users are encouraged to upgrade:

(1) Prevu always copies the sources to a temporary working directory. Any sources you unpack will not be modified (this prevents prevu from inserting unwanted changelog entries into your own work)

(2) Prevu now invokes pdebuild differently, which prevents some erroneous build failures due to build-deps not being present on the host. (for example, the absence of cdbs causes lots of packages to fail backporting even though they backport fine)

---

### Post by foxy123 on 2006-11-10
I've got a problem with version 0.4.1. It works fine and reports building a package:
```
dpkg-deb: building package `dvd+rw-tools' in `../dvd+rw-tools_6.1-2ubuntu1~6.06prevu1_i386.deb'.
 dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/src/5849 filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/5929 and its subdirectories
** Success!. You can find source packages and .debs at /var/cache/prevu/dapper-debs **

```
but /var/cache/prevu/dapper-debs is empty :(

I tried a couple of times and even removed /var/cache/prevu and reinitialised prevu, still no avail. Should I file a bug?

---

### Post by jdong on 2006-11-10
That is a known and fixed bug with the initial 0.4.1 release. It's been fixed, and the 0.4.1 package has been re-released. Please re-download the package from Sourceforge.

---

### Post by foxy123 on 2006-11-11
> **jdong said:**
> That is a known and fixed bug with the initial 0.4.1 release. It's been fixed, and the 0.4.1 package has been re-released. Please re-download the package from Sourceforge.

thanks a lot, it fixed it!

---

### Post by dcstar on 2006-11-18
I've just tried a backport build of Evolution, but I get the following which stops it:
```
 -> Considering  cdbs (>= 0.4.37)
      Tried versions: 0.4.34ubuntu4
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.

```
Now, I actually built (and installed) a cdbs backport which is now 0.4.46ubuntu7~6.06prevu1, but I still get this error.

It's probably something obvious, but can someone let me know?

---

### Post by foxy123 on 2006-11-18
> **dcstar said:**
> I've just tried a backport build of Evolution, but I get the following which stops it:
```
 -> Considering  cdbs (>= 0.4.37)
      Tried versions: 0.4.34ubuntu4
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.

```
Now, I actually built (and installed) a cdbs backport which is now 0.4.46ubuntu7~6.06prevu1, but I still get this error.

It's probably something obvious, but can someone let me know?

I am not sure whether you manage to backport Evolution because as I understand it is very much integrated in Gnome. Anyway, you may try.

First of all, make sure that you use a local repository for your backported packages. To do it you need to put 
```
deb file:/var/cache/prevu/dapper-debs ./
```
in your source list, if you are on Dapper. I am not 100% sure that it is needed but to be on the safe side it's worth doing.

Then after building a new package you have to run
```
sudo prevu-update
``` to add newly built library/development package in you building environment. After that you should be fine.

---

### Post by foxy123 on 2006-11-18
I have another problem. I am trying to backport dvd::rip, but prevu builds a Dapper version instead of Edgy:
```
:~$ prevu dvdrip
I: Building against currently running distro: dapper
Reading package lists... Done
Building dependency tree... Done
Need to get 526kB of source archives.
Get: 1 http://gb.archive.ubuntu.com dapper/multiverse video-dvdrip 1:0.52.5-0.0 (dsc) [591B]
Get: 2 http://gb.archive.ubuntu.com dapper/multiverse video-dvdrip 1:0.52.5-0.0 (tar) [520kB]

```
While in Edgy packages:
```
dvdrip (1:0.98.1-0.1ubuntu1) [multiverse] perl front end for transcode
```
I wonder if the name has been changed in some way? Any idea? I tried to comment out Dapper source repo, but then prevu cannot find dvd::rip
```
~$ prevu dvdrip
I: Building against currently running distro: dapper
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for video-dvdrip
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 83, in backport
    self.prepare_sources()
  File "/usr/bin/prevu", line 104, in prepare_sources
    raise ValueError("Fetching source package failed. Are you sure it exists?")
ValueError: Fetching source package failed. Are you sure it exists?

```

---

### Post by jdong on 2006-11-18
Do you have deb-src lines for Edgy or Feisty Multiverse?

---

### Post by foxy123 on 2006-11-18
> **jdong said:**
> Do you have deb-src lines for Edgy or Feisty Multiverse?

yes, I do:

```
##EDGY SOURCE
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
```

---

### Post by foxy123 on 2006-11-18
For some reason it cannot get sources for multiverse, while it fetches main and universe all right - NO IT IS NOT TRUE...

it happens only with dvdrip :(

---

### Post by jdong on 2006-11-18
Try using feisty as your source instead of edgy.... This would not be a prevu bug though, more of an apt problem if anything else. Prevu uses "apt-get source <packagename>" to fetch source packages.

---

### Post by foxy123 on 2006-11-18
> **jdong said:**
> Try using feisty as your source instead of edgy.... This would not be a prevu bug though, more of an apt problem if anything else. Prevu uses "apt-get source <packagename>" to fetch source packages.

I tried feisty with the same result :(

---

### Post by dcstar on 2006-11-18
> **foxy123 said:**
> I am not sure whether you manage to backport Evolution because as I understand it is very much integrated in Gnome. Anyway, you may try.
.....
Then after building a new package you have to run
```
sudo prevu-update
``` to add newly built library/development package in you building environment. After that you should be fine.

Thanks, having to run that update command again did the trick.

There are a lot of "brick walls" in trying to get Evolution backported.....  :-?

---

### Post by jdong on 2006-11-18
I don't think there's any trivial way to backport Evolution back... there's a lot of new components of the GNOME subsystem required.

And foxy123, I honestly have no clue what on earth is happening on your system... I can't reproduce it on my Dapper or Edgy boxes. It's clear that apt-get source is fetching the wrong source packages, which is not controlled in any way by prevu.

---

### Post by dcstar on 2006-11-19
> **jdong said:**
> I don't think there's any trivial way to backport Evolution back... there's a lot of new components of the GNOME subsystem required.
......

I tend to agree now, I keep finding more components that cascade into even more components that have to be upgraded, and my attempt at backporting libselinux1-dev fails when it gets to the stage of building the deb, so at the moment I'll wait until the (apparently) many 6.10 problems reduce to a level I'm comfortable with before I upgrade.

Still, I have the prevu infrastructure set up and working, and the experience of building some backports.

---

### Post by foxy123 on 2006-11-19
> **jdong said:**
> I don't think there's any trivial way to backport Evolution back... there's a lot of new components of the GNOME subsystem required.

And foxy123, I honestly have no clue what on earth is happening on your system... I can't reproduce it on my Dapper or Edgy boxes. It's clear that apt-get source is fetching the wrong source packages, which is not controlled in any way by prevu.

i will try on a different PC then... thanks anyway...

---

### Post by foxy123 on 2006-11-19
> **foxy123 said:**
> i will try on a different PC then... thanks anyway...

ok, I tried on another PC and had the same results. I guess it's apt-get or repository bug, because it happens only to this particular package and I tried 'apt-get source dvdrip' and still got the source only from Dapper. :(

---

### Post by jdong on 2006-11-19
Have you tried using a different mirror, to see if that clears anything up?

---

### Post by foxy123 on 2006-11-19
> **jdong said:**
> Have you tried using a different mirror, to see if that clears anything up?

I tried
```
##EDGY SOURCE
deb-src http://us.archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
``` but it did not change a thing...

---

### Post by dcstar on 2006-11-20
Just out of interest, I backported the **partimage** package and the new version seems to have fixed the bug where restoring a compressed package doesn't work in the Dapper version.

---

### Post by jdong on 2006-11-20
Interesting... please file a dapper-backports bug in Launchpad if that partimage package works well for you.

---

### Post by dcstar on 2006-11-20
> **jdong said:**
> Interesting... please file a dapper-backports bug in Launchpad if that partimage package works well for you.

I don't know if I should now, I just tried a save/restore with the old version - with compression - and it worked!

I also booted off the 6.06 install disk and installed partimage and tried it again - and it worked again!

I'm not the only one who previously experienced the partimage compression bug, but one my system it seems solved.

---

### Post by edeca on 2006-11-21
I am trying to backport ircd-hybrid, which works fine using simply

$ prevu ircd-hybrid

However I would like to enable SSL, too, so I tried the following:

$ USE_OPENSSL="1" prevu ircd-hybrid

This does not work though, giving the following error:

dpkg-checkbuilddeps
dpkg-checkbuilddeps: Unmet build dependencies: libssl-dev
make: *** [configure-stamp] Error 1

I have libssl-dev installed on the actual machine so I assume that this is a problem within the build environment.  No version numbers are mentioned so I assume that any version would do.

Is it possible to tell prevu to install the dependency inside the build environment?  Or is there another problem that I have missed?

Thanks!

---

### Post by jdong on 2006-11-21
To tell a build dependency to install, you must unpack the source archive for your package, edit debian/control, and add the name of the package to the Build-Depends: list.

---

### Post by edeca on 2006-11-22
> To tell a build dependency to install, you must unpack the source archive for your package, edit debian/control, and add the name of the package to the Build-Depends: list.

Thanks for this, that makes it build fine.  I used apt-get source ircd-hybrid, edited debian/control then ran USE_OPENSSL="1" prevu in the build directory.  The compile goes fine, but then this error occurs:

```
dpkg-deb: building package `ircd-hybrid' in `../ircd-hybrid_7.2.2.dfsg.1-2~6.06prevu1.ssl1_i386.deb'.
 dpkg-genchanges
dpkg-genchanges: error: cannot open .dsc file ../ircd-hybrid_7.2.2.dfsg.1-2~6.06prevu1.ssl1.dsc: No such file or directory
```

Is there anything that can be done to fix this?

Thanks.

---

### Post by foxy123 on 2006-11-24
I tried to backport libnfnetlink from Feisty but it failed to build a debian package:
```
mkdir /var/cache/prevu/src/20898/libnfnetlink-0.0.16/debian/tmp/usr/lib/pkgconfig
 /usr/bin/install -c -m 644 libnfnetlink.pc /var/cache/prevu/src/20898/libnfnetlink-0.0.16/debian/tmp/usr/lib/pkgconfig/libnfnetlink.pc
make[3]: Leaving directory `/var/cache/prevu/src/20898/libnfnetlink-0.0.16'
make[2]: Leaving directory `/var/cache/prevu/src/20898/libnfnetlink-0.0.16'
make[1]: Leaving directory `/var/cache/prevu/src/20898/libnfnetlink-0.0.16'
touch install-stamp
dh_testdir -i
dh_testdir: I have no package to build
make: *** [binary-indep] Error 1
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/src/20898 filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/20976 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

Any idea, why it fails?

---

### Post by dcstar on 2006-11-25
If us people out in user land are able to build successful backported packages, would it be possible to upload them to a central location somewhere so others could get access to them?

It seems a bit wasteful to have other people going through the same build process that someone else has already done.

---

### Post by foxy123 on 2006-11-25
someone earlier in the thread mentioned having a repository...

---

### Post by jdong on 2006-11-25
I personally don't recommend starting a repository of prevu'ed packages. Instead, if a package properly prevu builds, submit it as a backport request.

The trouble with repositories, is you get far far more people who will install packages from it in a knee-jerk reaction. The Backports team tries hard to make sure its packages are safe enough for the general user to install. If a package is not fit as a Backports package, then it's not fit for the general user to use, and it's a better idea for users to build it themselves.


With the majority of PC's, building a package is not that intensive a process.

---

### Post by xopher on 2006-11-26
I get this error when trying to prevu libhal-dev, is there an easy solution for this? Thanks

Im on edgy amd64 using prevu 0.4.1-0ubuntu1

[HTML]xopher@xopher:~$ sudo prevu libhal-dev
I: Building against currently running distro: edgy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 1813kB of source archives.
Get:1 http://archive.ubuntu.com feisty/main hal 0.5.8.1-3ubuntu5 (dsc) [984B]
Get:2 http://archive.ubuntu.com feisty/main hal 0.5.8.1-3ubuntu5 (tar) [1749kB]
Get:3 http://archive.ubuntu.com feisty/main hal 0.5.8.1-3ubuntu5 (diff) [62.6kB]
Fetched 1813kB in 15s (120kB/s)                                                
gpg: WARNING: unsafe ownership on configuration file `/home/xopher/.gnupg/gpg.conf'
gpg: Signature made Thu 23 Nov 2006 12:57:53 PM EET using DSA key ID C978C8AE
gpg: Can't check signature: public key not found
dpkg-source: extracting hal in hal-0.5.8.1
dpkg-source: unpacking hal_0.5.8.1.orig.tar.gz
dpkg-source: applying ./hal_0.5.8.1-3ubuntu5.diff.gz
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
dch warning: new version (0.5.8.1-3ubuntu5~6.10prevu1) is less than
the current version number (0.5.8.1-3ubuntu5).
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/edgy.tgz]
 -> creating local configuration
 -> copying local configuration
 -> mounting /proc filesystem
 -> mounting /dev/pts filesystem
-> Mounting /home/xopher/pbuilder/result
-> Mounting /var/cache/prevu/edgy-debs
-> Mounting /var/cache/prevu/src/2048
 -> policy-rc.d already exists
Obtaining the cached apt archive contents
W: no hooks of type F found -- ignoring
Using: : pdebuild-internal,v 1.12 2006/06/05 11:39:04 dancer Exp $
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debootstrap wget
Recommended packages:
  fakeroot devscripts
The following NEW packages will be installed:
  debootstrap pbuilder wget
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.8kB/371kB of archives.
After unpacking 2757kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy-backports/main debootstrap 0.3.3.0ubuntu8~edgy1 [49.8kB]
Fetched 49.8kB in 6s (7566B/s)                                                 
Selecting previously deselected package wget.
(Reading database ... 11893 files and directories currently installed.)
Unpacking wget (from .../wget_1.10.2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package debootstrap.
Unpacking debootstrap (from .../debootstrap_0.3.3.0ubuntu8~edgy1_all.deb) ...
Selecting previously deselected package pbuilder.
Unpacking pbuilder (from .../pbuilder_0.155ubuntu3_all.deb) ...
Setting up wget (1.10.2-2ubuntu1) ...

Setting up debootstrap (0.3.3.0ubuntu8~edgy1) ...
Setting up pbuilder (0.155ubuntu3) ...
Setting DEBBUILDOPTS=
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.28 2006/05/30 23:45:45 dancer Exp $
 -> Considering  debhelper (>= 5.0.37.2)
   -> Trying debhelper
 -> Considering  cdbs
   -> Trying cdbs
 -> Considering  python-support (>= 0.5.3)
   -> Trying python-support
 -> Considering  python-dbus
   -> Trying python-dbus
 -> Considering  libdbus-glib-1-dev (>= 0.60)
   -> Trying libdbus-glib-1-dev
 -> Considering  libglib2.0-dev
   -> Trying libglib2.0-dev
 -> Considering  libsysfs-dev
   -> Trying libsysfs-dev
 -> Considering  libexpat1-dev
   -> Trying libexpat1-dev
 -> Considering  libpopt-dev
   -> Trying libpopt-dev
 -> Considering  pkg-config
   -> Trying pkg-config
 -> Considering  pciutils
   -> Trying pciutils
 -> Considering  libcap-dev
   -> Trying libcap-dev
 -> Considering  doxygen
   -> Trying doxygen
 -> Considering  intltool (>= 0.22)
   -> Trying intltool
 -> Considering  libusb-dev
   -> Trying libusb-dev
 -> Considering  libvolume-id-dev
   -> Trying libvolume-id-dev
       -> Cannot install libvolume-id-dev; apt errors follow:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pciutils is already the newest version.
E: Couldn't find package libvolume-id-dev
W: Unable to locate package libvolume-id-dev
E: Could not satisfy build-dependency.
Copying back the cached apt archive contents
 -> new cache content debootstrap_0.3.3.0ubuntu8~edgy1_all.deb added
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /home/xopher/pbuilder/result filesystem
 -> unmounting /var/cache/prevu/edgy-debs filesystem
 -> unmounting /var/cache/prevu/src/2048 filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/2133 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
[/HTML]

Edit:

Oh yeah, this is probably my problem:

```
   -> Trying libvolume-id-dev
       -> Cannot install libvolume-id-dev; apt errors follow:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pciutils is already the newest version.
E: Couldn't find package libvolume-id-dev
W: Unable to locate package libvolume-id-dev
E: Could not satisfy build-dependency.
```

Does this mean I need to prevu libvolume-id-dev first?

Edit2: I prevu'd libvolume-id-dev , it builds fine, but still ends with an error, any clues on this? :

```

.
.
.
dh_builddeb
dpkg-deb: building package `udev' in `../udev_103-0ubuntu4~6.10prevu1_amd64.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `udev-udeb' in `../udev-udeb_103-0ubuntu4~6.10prevu1_amd64.udeb'.
tar: -: file name read contains nul character
dpkg-deb: building package `volumeid' in `../volumeid_103-0ubuntu4~6.10prevu1_amd64.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `libvolume-id0' in `../libvolume-id0_103-0ubuntu4~6.10prevu1_amd64.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `libvolume-id-dev' in `../libvolume-id-dev_103-0ubuntu4~6.10prevu1_amd64.deb'.
tar: -: file name read contains nul character
 dpkg-genchanges
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /home/xopher/pbuilder/result filesystem
 -> unmounting /var/cache/prevu/edgy-debs filesystem
 -> unmounting /var/cache/prevu/src/17519 filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/17603 and its subdirectories
debsign: Can't find or can't read changes file /home/xopher/pbuilder/result/udev_103-0ubuntu4~6.10prevu1_amd64.changes!
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

Edit3: Couldnt get prevu to work so I built these in pbuilder, built just fine.

Is it safe to assume they work? I mean udev isnt something Id like to break.

---

### Post by jdong on 2006-11-26
It is not at all safe to assume that they work :)

udev versions need to match up with the kernel's udev counterpart's version in terms of compatibility... if not, you'll end up with an unbootable system and will be digging for your LiveCD's :)

Try at your own risk :)


```

debsign: Can't find or can't read changes file /home/xopher/pbuilder/result/udev_103-0ubuntu4~6.10prevu1_amd64.changes!

```

Fascinating... I'll have to investigate that error.

---

### Post by xopher on 2006-11-27
Yeah, I thought it wouldn't be the best idea. Oh well - We found a solution with the developer of bmpx, so it will still work with libhal 0.5.7.1 - no need for the update. Thanks a lot anyway!

---

### Post by fuoco on 2006-12-13
Would it be possible to use prevu to backport some mesa packages with newer drivers for my video card ?

---

### Post by fuoco on 2006-12-14
Another question, can I use prevu to backport a package from debian unstable/testing instead of feisty (a package that's not yet synced in feisty) ?

---

### Post by foxy123 on 2006-12-14
> **fuoco said:**
> Would it be possible to use prevu to backport some mesa packages with newer drivers for my video card ?

I guess it will involve backporting the whole X which is really not advisable.

---

### Post by foxy123 on 2006-12-14
> **fuoco said:**
> Another question, can I use prevu to backport a package from debian unstable/testing instead of feisty (a package that's not yet synced in feisty) ?

I am not sure if you can do it, but you can try and let us know. However I doubt if it is possible to do straight forward. You may need to fetch the packages and change version numbers and maybe some other stuff in debian/control. It may be easier to fetch the packages and try to rebuild it with dpkg-buildpackage -rfakeroot.

---

### Post by fuoco on 2006-12-14
> **foxy123 said:**
> I am not sure if you can do it, but you can try and let us know. However I doubt if it is possible to do straight forward. You may need to fetch the packages and change version numbers and maybe some other stuff in debian/control. It may be easier to fetch the packages and try to rebuild it with dpkg-buildpackage -rfakeroot.

Thanks. I would like to try that but I don't really know how, I never build packages in ubuntu/debian before...

---

### Post by foxy123 on 2006-12-14
> **fuoco said:**
> Thanks. I would like to try that but I don't really know how, I never build packages in ubuntu/debian before...

I did and in general it is not very difficult but could be a pain sometimes, really :)

---

### Post by fuoco on 2006-12-14
> **foxy123 said:**
> I did and in general it is not very difficult but could be a pain sometimes, really :)

Can you tell me what I should do to use prevu with debian unstable packages ?

---

### Post by foxy123 on 2006-12-14
> **fuoco said:**
> Can you tell me what I should do to use prevu with debian unstable packages ?

I did not use prevu, I used
```
dpkg-buildpackage -rfakeroot
```

---

### Post by jdong on 2006-12-14
Yes, prevu can indeed backport Debian Sid or other source packages.

You can either:
(1) fetch and unpack the sources yourself, and when in the directory that contains the debian/ control dir, issue "prevu" with no arguments
(2) Give prevu the path or URL to a .dsc file. For example, on [http://packages.qa.debian.org/t/torrentflux.html](http://packages.qa.debian.org/t/torrentflux.html), we see a link to : [http://ftp.debian.org/debian/pool/main/t/torrentflux/torrentflux_2.1-6.dsc](http://ftp.debian.org/debian/pool/main/t/torrentflux/torrentflux_2.1-6.dsc)

Invoke prevu as:
```

prevu http://ftp.debian.org/debian/pool/main/t/torrentflux/torrentflux_2.1-6.dsc

```

and it'll fetch the sources, unpack, then backport.

---

### Post by Jeff250 on 2006-12-19
Thanks for this great tool.  I'm having trouble with a two-part backport of Feisty's Rhythmbox to Edgy.  Rhythmbox in Feisty needs an updated gpod lib, which I've backported using prevu and installed.  However, I still get this error:

```
 -> Considering  libgpod-dev (>= 0.4.0-0ubuntu3)
      Tried versions: 0.4.0-0ubuntu3~6.10prevu1 0.3.2-1.1ubuntu1
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
```

This seems to indicate that it sees the updated libgpod but doesn't believe that it satisfies the dependency, even though it looks like it should.  What's going on here?  Thanks.

---

### Post by Toehead on 2006-12-19
ubchenelle@brendan-laptop:~$ sudo prevu xserver-xorg-video-ati
I: Building against currently running distro: edgy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 1004kB of source archives.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main xserver-xorg-video-ati 1:6.6.2-0ubuntu4 (dsc) [1729B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main xserver-xorg-video-ati 1:6.6.2-0ubuntu4 (tar) [979kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main xserver-xorg-video-ati 1:6.6.2-0ubuntu4 (diff) [23.2kB]                                     
Fetched 1004kB in 11s (86.0kB/s)                                                                                                      
gpg: WARNING: unsafe ownership on configuration file `/home/ubchenelle/.gnupg/gpg.conf'
gpg: Signature made Fri 06 Oct 2006 02:05:54 AM EDT using RSA key ID 63549F8E
gpg: Can't check signature: public key not found
dpkg-source: extracting xserver-xorg-video-ati in xserver-xorg-video-ati-6.6.2
dpkg-source: unpacking xserver-xorg-video-ati_6.6.2.orig.tar.gz
dpkg-source: applying ./xserver-xorg-video-ati_6.6.2-0ubuntu4.diff.gz
dch warning: new version (1:6.6.2-0ubuntu4~6.10prevu1) is less than
the current version number (1:6.6.2-0ubuntu4).
W: /home/ubchenelle/.pbuilderrc does not exist
W: /home/ubchenelle/.pbuilderrc does not exist
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/edgy.tgz]
 -> creating local configuration
hostname: Unknown host
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.


This is the error I get trying to upgrade my ATI drivers. The same goes for any package i try to install. Any ideas? Thanks
-Brendan

---

### Post by fuoco on 2006-12-19
Toehead: maybe you didn't do prevu-init or something like that? At any rate, I told you to use the dsc files from debian testing because the version in feisty you are trying to backport is the same as the one you already have in edgy, so even when you succeed it would give you no benefit I predict. If it does tell me ;)

---

### Post by jdong on 2006-12-19
> **Jeff250 said:**
> Thanks for this great tool.  I'm having trouble with a two-part backport of Feisty's Rhythmbox to Edgy.  Rhythmbox in Feisty needs an updated gpod lib, which I've backported using prevu and installed.  However, I still get this error:

```
 -> Considering  libgpod-dev (>= 0.4.0-0ubuntu3)
      Tried versions: 0.4.0-0ubuntu3~6.10prevu1 0.3.2-1.1ubuntu1
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
```

This seems to indicate that it sees the updated libgpod but doesn't believe that it satisfies the dependency, even though it looks like it should.  What's going on here?  Thanks.

Ah, it's looking for  0.4.0-0ubuntu3, but it's finding  0.4.0-0ubuntu3~6.10prevu1, which due to the backports version tags appears lower than the desired version.

What you need to do is apt-get source rhythmbox, edit debian/control, and change the libgpod-dev dependency from  0.4.0-0ubuntu3 to  0.4.0-0ubuntu3~6.10prevu1. Then, you can just issue **prevu** in the unpacked source directory you just edited and it'll build.

---

### Post by Toehead on 2006-12-19
> **fuoco said:**
> Toehead: maybe you didn't do prevu-init or something like that? At any rate, I told you to use the dsc files from debian testing because the version in feisty you are trying to backport is the same as the one you already have in edgy, so even when you succeed it would give you no benefit I predict. If it does tell me ;)

:) don't worry, i didnt forget what you told me! i only tried the fiesty ones after the debian testing files gave me that error message! I'm re-doing my prevu init :) Thanks!

---

### Post by Toehead on 2006-12-19
Also, since installing prevu, I suddenly have 550 update notifications. i assume this is normal?

I think my problems are caused by the gpg key error, but I have no idea how to resolve it.

---

### Post by jdong on 2006-12-19
> **foxy123 said:**
> a community backport repo is what we need. Ubuntu security team is focused on security backports and Ubuntu backporting team on other critical backports, then a community backport repo could provide other less essential packages, which would be nice to have for many people.

I'd prefer it if community backports are done through the official backports repositories. You can request any package you want, and as long as prevu will build it, it'll be acceptable.

The only thing right now holding packages back from mass-backporting is my limited man-hours for testing packages. So if more people can get involved with helping official backports test packages with prevu, we can make our official backports repository very complete :)

---

### Post by Toehead on 2006-12-19
well, previe -init wasnt the problem., does anybody know how to proceed?

---

### Post by jdong on 2006-12-19
> **Toehead said:**
> Also, since installing prevu, I suddenly have 550 update notifications. i assume this is normal?

I think my problems are caused by the gpg key error, but I have no idea how to resolve it.

No, that's absolutely not normal! What kind of packages does it claim can be updated?

---

### Post by Toehead on 2006-12-19
starting at the top
aduser, alsa-base, alsa utils, anacron, apt, apt-utils, aptitude, aspell-en, at-spi to name a few.. It asks me to do a distribution upgrade.

---

### Post by jdong on 2006-12-19
wow, it seems like it wants to upgrade to a newer version of ubuntu... very weird.

Can you post your sources.list in code tags or pastebin and also what version of ubuntu you're running?

---

### Post by Toehead on 2006-12-19
I figured it out, was a bad deb source in my sources.list file. Sorry for the false alarm. Now i'm back to where I started, with everything I try to build yielding the same error. Thanks for the help!
-Brendan

---

### Post by Jeff250 on 2006-12-19
> **jdong said:**
> What you need to do is apt-get source rhythmbox, edit debian/control, and change the libgpod-dev dependency from  0.4.0-0ubuntu3 to  0.4.0-0ubuntu3~6.10prevu1. Then, you can just issue **prevu** in the unpacked source directory you just edited and it'll build.

Worked great.

---

### Post by megamaced on 2006-12-22
I am trying to backport Kaffeine 0.8.3 but for some reason Prevu doesn't detect the need for the LAME development files. Kaffeine compiles fine and the debian packages are made, but theres no CD encoding as a result of the lack of LAME.

How can I force Prevu to download the LAME dev package? Thanks

---

### Post by foxy123 on 2006-12-22
> **megamaced said:**
> I am trying to backport Kaffeine 0.8.3 but for some reason Prevu doesn't detect the need for the LAME development files. Kaffeine compiles fine and the debian packages are made, but theres no CD encoding as a result of the lack of LAME.

How can I force Prevu to download the LAME dev package? Thanks

you can try to edit debian/control file. You need to d/l the source, edit the dependencies and run 'prevu' from the source directory

---

### Post by jdong on 2006-12-22
> **megamaced said:**
> How can I force Prevu to download the LAME dev package? Thanks

The only way to force prevu to install a package in the build environment is the proper Debian way: to add the package name to Build-Depends: in debian/control of the source. I think I've already said once or twice in this thread how to roughly do that.

---

### Post by fuoco on 2006-12-23
I tried to backport the kernel image and got the following error:

```
cat: /var/cache/prevu/src/11769/linux-source-2.6.19-2.6.19/debian/abi/2.6.19-7.11/abiname: No such file or directory
# Check for the previous kernel's abi file; now a requirement for builds!
Missing /var/cache/prevu/src/11769/linux-source-2.6.19-2.6.19/debian/abi/2.6.19-7.11/abiname file.
```

I used the command: 
```
prevu linux-image-2.6.19-7-powerpc
```

What do i need to do?

---

### Post by foxy123 on 2006-12-23
> **fuoco said:**
> I tried to backport the kernel image and got the following error:

```
cat: /var/cache/prevu/src/11769/linux-source-2.6.19-2.6.19/debian/abi/2.6.19-7.11/abiname: No such file or directory
# Check for the previous kernel's abi file; now a requirement for builds!
Missing /var/cache/prevu/src/11769/linux-source-2.6.19-2.6.19/debian/abi/2.6.19-7.11/abiname file.
```

I used the command: 
```
prevu linux-image-2.6.19-7-powerpc
```

What do i need to do?
I do not think, that you can backport the kernel using prevu. What you need to do is to get the kernel source and build the kernel using one of various howtos available on this forum.

---

### Post by foxy123 on 2006-12-23
I am thinking about writing a new howto for prevu putting together jdong's comments and some other tips. Otherwise I can put them together and send to jdong to update this thread.

---

### Post by jdong on 2006-12-23
Kernels currently cannot be backported using prevu because prevu puts that ~version trailer, which confuses the heck out of the kernel building scripts. 

For moral political and ethical reasons I will not release a version of prevu that does not mangle versions; that's just plain irresponsible. But, you guys can modify your prevu to do that. Make a temporary copy of prevu (i.e. cp /usr/bin/prevu /tmp/), then edit /tmp/prevu and find where the map of version trailers to distro releases are, and blank out the version trailers.

Don't do this unless you absolutely must, i.e. for a kernel package, prolonged exposure may lead to skin cancer and wrinkles.

---

### Post by megamaced on 2006-12-30
> **jdong said:**
> The only way to force prevu to install a package in the build environment is the proper Debian way: to add the package name to Build-Depends: in debian/control of the source. I think I've already said once or twice in this thread how to roughly do that.

I edited the debian/control file and put liblame-dev in there but Prevu still refuses to compile Kaffeine with Lame encoding support. Do you know why this is?

BTW, has anyone successfully backported Firefox 2.0 using Prevu? I was backporting to Dapper but Prevu failed right at the end. Not sure what went wrong

---

### Post by foxy123 on 2006-12-30
> **megamaced said:**
> Sorted! Thanks.

BTW, has anyone successfully backported Firefox 2.0 using Prevu? I was backporting to Dapper but Prevu failed right at the end. Not sure what went wrong

personally I do not see a reason for backport FF2.0. It is much easier to install it using a tar from Mozilla's site and instruction in wiki. As I remember the backports team tried to backport 1.5 in Breezy but gave up due to many problems. Maybe it is easier now.

BTW, is it possible to use prevu as a clean building environment, like chroot? I wanted to build some packages which are not in Feisty or Debian but my root partition is too small at the moment to have 2 bases.

---

### Post by foxy123 on 2006-12-30
> **megamaced said:**
> I edited the debian/control file and put liblame-dev in there but Prevu still refuses to compile Kaffeine with Lame encoding support. Do you know why this is?

Look into debian/rules:
```
#!/usr/bin/make -f

include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/rules/simple-patchsys.mk
include /usr/share/cdbs/1/class/kde.mk

DEB_INSTALL_MANPAGES_kaffeine := debian/kaffeine.1
DEB_CONFIGURE_EXTRA_FLAGS := --without-gstreamer --without-lame

install/kaffeine::
	install -D -p -m0644 debian/kaffeine.xpm debian/kaffeine/usr/share/pixmaps/kaffeine.xpm
	install -D -p -m0644 debian/kaffeine.lintian-overrides debian/kaffeine/usr/share/lintian/overrides/kaffeine

```

It states --without-lame I guess if you remove this option, it should build with lame

---

### Post by megamaced on 2006-12-30
Yes! That's it! :-D 

Thanks Foxy =D>

---

### Post by jdong on 2006-12-30
> **megamaced said:**
> I edited the debian/control file and put liblame-dev in there but Prevu still refuses to compile Kaffeine with Lame encoding support. Do you know why this is?

It may need a --enable-something flag (like --enable-lame) to be added to debian/rules's ./configure line. Consult Kaffeine's source documentation to figure out exactly what it takes to enable lame.
> 
BTW, has anyone successfully backported Firefox 2.0 using Prevu? I was backporting to Dapper but Prevu failed right at the end. Not sure what went wrong
Ubuntu Firefox has so many Ubuntu-specific integration patches that I doubt it'd compile against any version of Ubuntu except the one it was destined for. You'd have better luck doing a binary install of Firefox into /opt, /usr/local, or your home directory from mozilla.org's official binaries. Oh yeah, backporting Firefox 2.0 will break all the packages listed in **apt-cache rdepends firefox** and also anything that depends on libnss, libnspr, and such libraries. In other words, don't do it.

If it were that easy to give Dapper users Firefox 2.0, wouldn't you expect me to have backported it officially to Dapper a lot earlier? ;-)

---

### Post by jdong on 2006-12-30
> **foxy123 said:**
> As I remember the backports team tried to backport 1.5 in Breezy but gave up due to many problems. Maybe it is easier now.

Ha! nope. I gave it a good 30-minute look when edgy finalized and it absolutely trashed Dapper until I could rebuild all its reverse deps which was a good 30 packages or so. Not gonna do something that intrusive, or else I'd have to start coining "half-releases" and gathering a Backports Release team to press 6.10.5 CD's :D


However, currently 2.0.0.1 will backport from Feisty to Edgy with prevu, if you are really jumping up and down for that security fix. The real one is being delayed by (1) the holiday break (2) upgrade break paranoia :D

> 
BTW, is it possible to use prevu as a clean building environment, like chroot? I wanted to build some packages which are not in Feisty or Debian but my root partition is too small at the moment to have 2 bases.
Prevu is a clean building environment, it's pbuilder, which basically makes and destroys chroots. The only difference is it puts that ~6.10prevu1 version trailer to not cause you upgrade hell in the future.

You can even remove that by editing prevu's source code and replacing those trailers with blank strings using a find-replace.

---

### Post by david.rahrer on 2006-12-30
I just installed and tried prevu to build a backport of gaim for edgy which seems to have worked fine.  Before I install, I'm curious about what to do if I want to return to the original edgy version.  Can this be done?  How?

Thanks.

---

### Post by jdong on 2006-12-30
> **david.rahrer said:**
> I just installed and tried prevu to build a backport of gaim for edgy which seems to have worked fine.  Before I install, I'm curious about what to do if I want to return to the original edgy version.  Can this be done?  How?

Thanks.

Use Synaptic's Force Version feature or from the command-line,

apt-get install gaim/edgy gaim-data/edgy

You do need to keep a complete list of all the package names updated.

---

### Post by david.rahrer on 2006-12-30
Ah, cool.  Thank you :)

---

### Post by david.rahrer on 2006-12-31
Ok, one more question.  Each time I run prevu, even when the build is successful, I get the following in the output:
> W: /home/username/.pbuilderrc does not exist
Is this something I need to fix?

---

### Post by jdong on 2006-12-31
No, it's no biggie, .pbuilderrc can override some aspects of pbuilder behavior on a per-user basis. Look at /etc/pbuilderrc for an example of what a pbuilderrc can configure.

This is a totally optional configuration file if you have special needs.

---

### Post by foxy123 on 2007-01-04
Is there an easy way to update a sources.list in the base tarball? I need to add a source for some packages, which are not present in dapper official repositories (cli-common-dev).

---

### Post by twickn11 on 2007-01-04
Take a lil break...  I know how hard you guys work.

[Free Internet Music Radio]("http://www.eplanetradio.com")

---

### Post by jdong on 2007-01-04
> **foxy123 said:**
> Is there an easy way to update a sources.list in the base tarball? I need to add a source for some packages, which are not present in dapper official repositories (cli-common-dev).

You need to edit /usr/bin/prevu-init and /usr/bin/prevu-update. Search for "pbuilder" and you'll see where it calls pbuilder. In that command is a string with a bunch of "deb ...." entries separated by a '|'. Add yours in, save, then run a prevu-update.

---

### Post by fuoco on 2007-01-06
I'm trying to backport network-manager. That seems to fail because of missing linux-headers. Am I supposed to manually install linux-headers on my system for prevu to use it when compiling?

---

### Post by jdong on 2007-01-06
> **fuoco said:**
> I'm trying to backport network-manager. That seems to fail because of missing linux-headers. Am I supposed to manually install linux-headers on my system for prevu to use it when compiling?

no. There's some patching and modifying that needs to be done before network-manager backports to Edgy, primarily related to changes in how kernel includes are done in Feisty. I can't recall them right now...

---

### Post by jek on 2007-01-20
I tried prevu with clamav (to get the security bug fixes) and it failed dependencies on dpkg:

    Setting DEBBUILDOPTS=
     -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.22 2005/12/04 05:16:40 dancer Exp $
     -> Considering  dpkg-dev (>= 1.13.19)
          Tried versions: 1.13.11ubuntu7 1.13.11ubuntu6
       -> Does not satisfy version, not trying
    E: Could not satisfy build-dependency.

Then trying to bring in dpkg seemed to start pulling in lots of stuff.

Is there any chance that clamav from feisty might build with the existing dpkg?  (i.e. any chance that the dependence got created sort of by default?)

Any way to tell prevu to ignore some dependencies in order to try this?

---

### Post by foxy123 on 2007-01-20
> **jek said:**
> I tried prevu with clamav (to get the security bug fixes) and it failed dependencies on dpkg:

    Setting DEBBUILDOPTS=
     -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.22 2005/12/04 05:16:40 dancer Exp $
     -> Considering  dpkg-dev (>= 1.13.19)
          Tried versions: 1.13.11ubuntu7 1.13.11ubuntu6
       -> Does not satisfy version, not trying
    E: Could not satisfy build-dependency.

Then trying to bring in dpkg seemed to start pulling in lots of stuff.

Is there any chance that clamav from feisty might build with the existing dpkg?  (i.e. any chance that the dependence got created sort of by default?)

Any way to tell prevu to ignore some dependencies in order to try this?

download the source:
```
apt-get source clamav
```

cd into the source dir and edit debian/control file with any text editor. Remove the version restriction from dpkg-dev. Then run prevu in the same directory and see if it works.

---

### Post by jek on 2007-01-21
> **foxy123 said:**
> download the source:
```
apt-get source clamav
```

cd into the source dir and edit debian/control file with any text editor. Remove the version restriction from dpkg-dev. Then run prevu in the same directory and see if it works.

Is there an option for prevu to tell it to pick up the modified package or do I need to add it to the sources.list?

---

### Post by jdong on 2007-01-21
sure, just type prevu with no arguments inside the modified source directory. Prevu will build that package.

---

### Post by jek on 2007-01-23
Thanks, that caused it to build but no surprise that clamav really does depend on that version:

dpkg-deb: parse error, in file `debian/clamav-daemon/DEBIAN/control' near line 6 package `clamav-daemon':
 `Depends' field, reference to `clamav-base': error in version: version string is empty
dh_builddeb: command returned error code 512
make: *** [clamav-daemon] Error 1

---

### Post by jdong on 2007-01-23
Most of the times higher build dependencies are put there for a reason ;-)

You can try backporting edgy-security clamav to Dapper to gain more support, but the versions of clamav in -security for supported distros are in fact not vulnerable to any outstanding issues. They've had the respective security patches worked in.

The only thing you miss are feature level addons (more sigs)...

I do feel you on the whole clamav thing... I wish it was in main.

---

### Post by jek on 2007-01-24
Yes, not surprising.

I did get edgy postfix working easily with prevu and deployed: [https://launchpad.net/dapper-backports/+bug/55599](https://launchpad.net/dapper-backports/+bug/55599)

It is unclear what it takes to get something "confirmed" in backports.  My problem is solved (I needed SSL working properly) but I'm sure many others can benefit.  I posted the .debs to Launchpad and nominated it.  

Anyway, prevu is great, thanks!!

---

### Post by jdong on 2007-01-24
For something as big as Postfix that has been hit with security fixes before, I am pretty wary about approving backports requests for. If a security hole comes up in the future and the security update does not backport to previous releases (case-and-point, clamav in dapper-backports), I'm in trouble.

---

### Post by megamaced on 2007-01-24
Can someone explain what package "cdbs" is, and whether it's important? I've seen it come up in this thread before and I've encounted it when I was trying to backport Amarok 1.4.4.

Do you think it would be OK to strip the cdbs version requirement out of debian/control?

BTW, thanks again for this great app! So far I have backported Kerry, Kaffeine, Wesnoth, Supertux and Compiz from Feisty to Dapper :)

---

### Post by jdong on 2007-01-24
CDBS is a packaging system used to make the debian/ package. Newer versions have updated/expanded functionality. Usually if it depends on a newer cdbs, it is serious. You can try stripping it but it'll likely fail.


Kubuntu.org has Amarok debs for Edgy at least....

---

### Post by megamaced on 2007-01-24
Do you think I'd get any problems by updating cdbs with Prevu?

---

### Post by jdong on 2007-01-24
No, but I don't think cdbs would be too happy to build either :) Will probably fail with an even longer chain of dependencies :D

---

### Post by nicweb on 2007-01-25
I was trying to install gaim beta 6. Therefore I need to build nautilus-sendto 0.8.2 The gaim package has a dependency on that. But nautilus-sendto needs gaim-dev (>= 1:2.0.0+beta6) on building. How to manage that?

---

### Post by jdong on 2007-01-25
apt-get source the nautilus-sendto, edit debian/control, change 2.0.0-beta6 to the version that prevu built (i.e. append ~6.10prevu1), then run prevu in the source directory.

---

### Post by megamaced on 2007-01-26
[QUOTE=jdong]By default, prevu will build debs for the current distro version you are running. If you would like to build for another distro, just run, for example, DIST=breezy prevu gdebi. Note you need to run DIST=breezy prevu-init first.[/QUOTE]

Just tried:

```
$ sudo DIST=edgy prevu-init
sudo: DIST=edgy: command not found
```

---

### Post by jdong on 2007-01-26
Wrong order... silly bash thing. It's DIST=edgy sudo prevu-init.

---

### Post by megamaced on 2007-01-27
Thanks

What happens to the source packages once prevu has finished? I've just spent the last 10 minutes downloading OpenOffice but there are dependency problems. That's fine, I can edit the debian/control, but where is the source package? Please don't tell me that Prevu removes it, even if the build fails. That's over 300MB+ I've got to download again otherwise :(

---

### Post by jdong on 2007-01-27
Yes, unfortunately prevu removes them regardless of build status.

If you are downloading something huge, have dial-up, or anticipate the need to build several times, you're much better off doing a manual "apt-get source <pkgname>; cd pkgname; prevu". prevu will not touch the downloaded sources.

---

### Post by Johan! on 2007-02-18
I can't build any packages:( 
Prevu gives the following error:
```

johan@ubuntu-desktop:~$ prevu deluge-torrent
I: Building against currently running distro: edgy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 484kB of source archives.
Get:1 http://archive.ubuntu.com feisty/universe deluge-torrent 0.4.1-2 (dsc) [846B]
Get:2 http://archive.ubuntu.com feisty/universe deluge-torrent 0.4.1-2 (tar) [475kB]
Get:3 http://archive.ubuntu.com feisty/universe deluge-torrent 0.4.1-2 (diff) [8539B]
Fetched 484kB in 1s (480kB/s)    
gpg: Signature made Wed 17 Jan 2007 09:14:05 PM CET using DSA key ID 4B2B2B9E
gpg: Can't check signature: public key not found
dpkg-source: extracting deluge-torrent in deluge-torrent-0.4.1
dpkg-source: unpacking deluge-torrent_0.4.1.orig.tar.gz
dpkg-source: applying ./deluge-torrent_0.4.1-2.diff.gz
dch warning: new version (0.4.1-2~6.10prevu1) is less than
the current version number (0.4.1-2).
W: /home/johan/.pbuilderrc does not exist
W: /home/johan/.pbuilderrc does not exist
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/edgy.tgz]
 -> creating local configuration
hostname: Unknown host
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
```

---

### Post by jdong on 2007-02-18
This is a problem with your system configuration -- if you issue 'hostname -f' you'll get the same error.

I have no idea how people are getting hostname problems but I've had a few others report this problem too -- it's not a prevu bug... but usually it's because /etc/hostname or /etc/hosts is improperly configured, typically arising from attempts to change the hostname.

---

### Post by Johan! on 2007-02-18
I don't know what happened, but /etc/hosts was changed.
I didn't try to change the hostname, or something like that.

This is the first time I've seen this error, and the error occurred after I installed prevu.
Anyway, I repaired /etc/hosts, and now it seems to work. :) 

By the way, is it normal to see a lot of warnings like these?
```

./include/libtorrent/asio/ip/address_v6.hpp:338: warning: missing braces around initializer for 'unsigned char [16]'
```
```

cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
```

---

### Post by jdong on 2007-02-18
Those are warnings gneerated when the package compiles -- most of the time harmless but you definitely don't need to be concerned about them.

---

### Post by edeca on 2007-02-19
I am trying to backport apache2 from feisty to dapper, as it has a number of bugfixes that I need for my environment.

However, 'prevu apache2' does not work because the build-deps has libaprutil1-dev, which isn't available on dapper (I notice it is libaprutil1.0-dev).

Is this a broken source package or something that cannot be backported using prevu easily?

Thanks.

---

### Post by jdong on 2007-02-19
That usually means it cannot be backported due to differences in the development distro and your current distro.

You can try prevu'ing the libaprutil package too and see if following the dependency chain works.

---

### Post by chandra on 2007-02-28
> **jdong said:**
> 

Invoke prevu as:
```

prevu http://ftp.debian.org/debian/pool/main/t/torrentflux/torrentflux_2.1-6.dsc

```

and it'll fetch the sources, unpack, then backport.

I tried

prevu [http://ftp.debian.org/debian/pool/main/s/skencil/skencil_0.6.17-7.dsc](http://ftp.debian.org/debian/pool/main/s/skencil/skencil_0.6.17-7.dsc)

and got

I: Building against currently running distro: dapper
sh: dget: command not found
Traceback (most recent call last):
  File "/usr/bin/prevu", line 144, in ?
    BackportFromDsc(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 83, in backport
    self.prepare_sources()
  File "/usr/bin/prevu", line 131, in prepare_sources
    raise ValueError("Extracting source package failed")
ValueError: Extracting source package failed

Is there a typo in the prevu script.  Should dget really be wget?

Tahnks.

---

### Post by jdong on 2007-02-28
no, dget is dget and should be in devscripts.

---

### Post by chandra on 2007-02-28
> **jdong said:**
> no, dget is dget and should be in devscripts.

dpkg -l devscripts
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  devscripts     2.9.10         Scripts to make the life of a Debian Package

and

dpkg -L devscripts | grep dget

gives a null response.

Can you please tell me what I am missing?

Thanks.

---

### Post by jdong on 2007-02-28
Hmm, it appears like devscripts in Dapper doesn't have dget. You can wget:

[http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224-0ubuntu2.diff.gz](http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224-0ubuntu2.diff.gz)
[http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224-0ubuntu2.dsc](http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224-0ubuntu2.dsc)
[http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224.orig.tar.gz](http://buntudot.org/people/~jdong/xgl/xserver-xgl_7.2.0.git.20070224.orig.tar.gz)

then dpkg-source -x *.dsc


and proceed.

---

### Post by malte on 2007-03-01
Thank you jdong for prevu!
Is it possible to strip '~${version}prevu' from the resulting deb's filename?

---

### Post by desperado666 on 2007-03-19
Wanted to backport displayconfig-gtk
Errorlog

prevu displayconfig-gtk
I: Building against currently running distro: edgy


Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

---

### Post by jdong on 2007-03-19
Please post more of the error (like 10-20 more lines up to the end). Wrap them in code tags to improve readability.

---

### Post by desperado666 on 2007-03-19
please be so kind and try to backport "displayconfig-gtk"
[http://packages.ubuntu.com/feisty/admin/displayconfig-gtk](http://packages.ubuntu.com/feisty/admin/displayconfig-gtk)

---

### Post by jdong on 2007-03-19
```

Selecting previously deselected package pbuilder.
Unpacking pbuilder (from .../pbuilder_0.155ubuntu3_all.deb) ...
Setting up wget (1.10.2-2ubuntu1) ...

Setting up debootstrap (0.3.3.0ubuntu8~edgy1) ...
Setting up pbuilder (0.155ubuntu3) ...
Setting DEBBUILDOPTS=
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.28 2006/05/30 23:45:45 dancer Exp $
[b]
 -> Considering  debhelper (>= 5.0.38)
      Tried versions: 5.0.37.3ubuntu4
   -> Does not satisfy version, not trying
[/b]
E: Could not satisfy build-dependency.
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/12087 filesystem
 -> unmounting /var/cache/prevu/edgy-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/12173 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 177, in <module>
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 115, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 96, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport/python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/prevu", line 177, in <module>
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 115, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 96, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

I have bolded for you what is the true error from the build -- the version of debhelper in Edgy is too old to support displayconfig-gtk.

---

### Post by desperado666 on 2007-03-19
Thanks for helping. So what to do now? 

"prevu debhelper"

 maybe ? ;)

---

### Post by foxy123 on 2007-03-20
> **desperado666 said:**
> Thanks for helping. So what to do now? 

"prevu debhelper"

 maybe ? ;)

In my experience you can always downgrade debhelper without any problem. To do that you should download the source:
```
apt-get sorce displayconfig-gtk
```

then cd to the source directory and then debian directory and edit the 'control' file, changing debheler version in dependencies. Howeve there may be a reason for setting its version to 5.0.38.

It is not worth to backport debhelper, because it depends on many core packages and vice versa many core packages depend on it.

---

### Post by desperado666 on 2007-03-20
So trying prevu is obsolete? Nice :(

---

### Post by jdong on 2007-03-20
Debhelper dependencies aren't put there for nonsense reasons.... I think in this case it uses some special Python tags in the control and rules files that aren't in earlier debhelpers.

prevu isn't obsolete... Edgy is obsolete for building that package :-/

---

### Post by foxy123 on 2007-03-20
> **desperado666 said:**
> So trying prevu is obsolete? Nice :(

no, if you downgrade debhelper requirement in the debian/control file you then will run prevu from the source directory...

---

### Post by megamaced on 2007-03-29
I am having a problem getting Prevu to download from 3rd party repositories. I am trying to backport Beryl 0.2.1 to Dapper. I am using the Beerorkid repository to provide all of my xgl related stuff. Beryl requires libxcomposite-dev 0.3, which is in the beerorkid repository. The Dapper repo only has version 0.2.2.2. Prevu does not fetch the beerorkid version, it will only download from the official mirrors.
I have run apt-get update and prevu-update several times but no joy.

---

### Post by chandra on 2007-04-08
I am having trouble getting prevu to build alsa-base and alsa-utils on Edgy using sources from Feisty.

First, the reason for doing this is because the alsa 1.0.11 libraries have a bug that prevents VoIP applications from functioning as noted here:

[http://tinyurl.com/28mu7f](http://tinyurl.com/28mu7f)

After installing prevu  0.4.1-0ubuntu1 I tried

prevu alsa-base

and got (among other things) this output at the end:

```
...
gpg: Can't check signature: public key not found
dpkg-source: extracting alsa-driver in alsa-driver-1.0.13
dpkg-source: unpacking alsa-driver_1.0.13.orig.tar.gz
dpkg-source: applying ./alsa-driver_1.0.13-3ubuntu1.diff.gz
dch warning: new version (1.0.13-3ubuntu1~6.10prevu1) is less than
the current version number (1.0.13-3ubuntu1).
...
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/edgy.tgz]
 -> creating local configuration
hostname: Unknown host
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
```

What do I need to do to get prevu to build successfully?

Alternatively, is there some simple package (with few dependencies) that I can use to confirm that prevu is working OK, before I try packages with complicated dependencies?

Thanks.

---

### Post by jdong on 2007-04-08
This error has been discussed in this thread, but the rough gist is that your system does not have a proper hostname set (see hostname -f output), so check /etc/hostname and /etc/hosts for a proper fully qualified domain name (i.e. jd-laptop.jd.lan)

---

### Post by malte on 2007-05-12
Hi, I'm a satisfied, long time prevu user :P
But, I'm trying to build pidgin from gutsy source repos and prevu fails with:
```

 -> Considering build-dep libebook1.2-dev
   -> Trying libebook1.2-dev
       -> Cannot install libebook1.2-dev; apt errors follow:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libebook1.2-dev: Depends: libebook1.2-9 (= 1.10.1-0ubuntu1) but it is not going to be installed
  libnss3-dev: Depends: libnspr4-dev (= 1.8.0.10-3ubuntu1) but it is not going to be installed
E: Broken packages
E: Could not satisfy build-dependency.

```
I don't think it's a matter of a two-step backport because those packages are in feisty repos...
Anybody could help me addressing the problem, please?

---

### Post by jdong on 2007-05-12
Some libnss4/libnspr4 dependencies have to be changed to libnss/libnspr (Without the 4), then it should build.

---

### Post by chandra on 2007-05-26
I have downloaded the texlive 2007 files from Debian at:

ftp.debian.org/debian/pool/main/t/texlive-{bin,base,doc,lang,extra}

In the download directory, I have:

texlive-base_2007.orig.tar.gz
texlive-base_2007-6.diff.gz
texlive-base_2007-6.dsc

I then did:

tar -zxvf texlive-base_2007.orig.tar.gz
cd texlive-base-2007
prevu

and got this message after which prevu exited:

I: Building against currently running distro: feisty
Usage (fetch from APT): /usr/bin/prevu source_package_name
Usage (build current directory): /usr/bin/prevu
Usage (build from .dsc file): /usr/bin/prevu dscfile_or_url
Prevu builds for your currently running version of Ubuntu. To override this, use the DIST environment variable
Build for Warty Warthog: DIST=warty /usr/bin/prevu

I had previously done 

sudo prevu-init

So, what should I do to make prevu start building the texlive-base-2007 package from 2007?

Thanks.

---

### Post by jdong on 2007-05-26
Run prevu on the .dsc file, because just extracting the orig.tar.gz does not apply the Debianization patches.

---

### Post by chandra on 2007-05-27
Thanks.

I have now successfully built tex-common from tex-common_1.7.dsc

dpkg -l tex-common gives
-----
ii  tex-common     1.7~7.04prevu1 Common infrastructure for using and building
-----
I have also done sudo prevu-update

But when I try building texlive-bin with

prevu texlive-bin_2007-9.dsc

it fails with this error message:
-----
-> Considering build-dep tex-common (>= 1.7)
      Tried versions: 1.7~7.04prevu1 0.42
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
-----
Why is this so and what must I do to get a successful build?

Thanks.

---

### Post by ubuntubrian on 2007-06-10
OK, I'm really interested inthis so I can backport VLC 0.8.6 to Dapper. I just don't get the how-to!
The first thing is to get prevu, which I did, but how do I install Prevu? Dpkg?
sorry to be a numbnut but I just can't think straight!
Thanks!:)

---

### Post by ubuntubrian on 2007-06-10
OK, I installed with dpkg after adding some dependencies. I initialized Prevu and tried "prevu vlc" and got an error:
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 83, in backport
    self.prepare_sources()
  File "/usr/bin/prevu", line 104, in prepare_sources
    raise ValueError("Fetching source package failed. Are you sure it exists?")
ValueError: Fetching source package failed. Are you sure it exists?


Any ideas? I know that vlc exists in dapper and I downloaded the Feisty deb file separately. Can I use that deb to make the backport?
Thanks

---

### Post by megamaced on 2007-06-11
Firstly you need to download Prevu from the Sourceforge page.

Then you install it with "sudo dpkg -i prevu*.deb"

Then you correct the dependencies with "sudo apt-get -f install"

Then you need to add the Fiesty / Gutsy repos to your /etc/apt/sources.list file

Then you run "sudo apt-get update"

Then "sudo prevu-init"

If you want to backport VLC, you would do "apt-get source vlc"

Then "cd" into the new VLC source directory and edit the debian/control file. Example "nano debian/control"

In the control file, you need to strip the version requirements for the dependencies.

Then you run "prevu" in the source directory

Prevu is an amazing tool and without it, I surely would have moved away from Kubuntu Dapper a long time ago! I've lost count of the amount of successul backports I've acheived!

---

### Post by ubuntubrian on 2007-06-11
thanks Megamaced! those are some seriously good instructions and I wouldn't have gleaned that from the initial how-to.
I did everything right until the "apt-get source vlc" so I'll give that  ago and post the results.
Many thanks!

---

### Post by ubuntubrian on 2007-06-11
hmmm...
I got this after running "apt-get source vlc"

apt-get source vlc
Reading package lists... Done
Building dependency tree... Done
E: Could not open file /var/lib/apt/lists/packages.freecontrib.org_plf_dists_dapper_free_source_Sources - open (2 No such file or directory)

I checked and there is no such directory.

Where does the VLC source directory get downloaded? the whole command above took about 4 seconds so I doubt anything got downloaded anyway.

Here's what's added to my sources.list:
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

#Added by prevu
deb file:/var/cache/prevu/dapper-debs ./

Thanks for any help!:)

---

### Post by ubuntubrian on 2007-06-11
I wondered if there was a package in Feisty or Gutsy for VLC and here's what I found at the page of the source in my source.list:

Page address: [http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)
Package: vic
Binary: vic
Version: 1:2.8ucl1.1.5-8
Priority: optional
Section: universe/net
Maintainer: Guus Sliepen <guus@debian.org>
Build-Depends: libx11-dev, libxext-dev, tcl8.4-dev, tk8.4-dev, libuclmmbase1-dev, debhelper (>= 4.0.0)
Architecture: any
Standards-Version: 3.6.2
Format: 1.0
Directory: pool/universe/v/vic
Files:
 0f0421daa3a0c24dd2fdb3ae31004b56 631 vic_2.8ucl1.1.5-8.dsc
 db4593e7686f1089aef55827271b5564 1113030 vic_2.8ucl1.1.5.orig.tar.gz
 f5ce54a676ad8de0e5d879e140724b01 37781 vic_2.8ucl1.1.5-8.diff.gz

---

### Post by megamaced on 2007-06-12
Sounds like you might have a problem with one of the repositories. Can you post your whole /etc/apt/sources.list file?

---

### Post by ubuntubrian on 2007-06-12
Thanks Megamaced-here it is:

# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
# deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Beta powerpc (20060420)]/ dapper main restricted
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse




#Added by prevu
deb file:/var/cache/prevu/dapper-debs ./

---

### Post by foxy123 on 2007-06-12
> **ubuntubrian said:**
> Thanks Megamaced-here it is:

# deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
# deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free
# The above lines were generated automatically by EasyUbuntu 3.0 Beta Release
# The rest of your sources.list follows

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Beta powerpc (20060420)]/ dapper main restricted
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# deb-src [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse




#Added by prevu
deb file:/var/cache/prevu/dapper-debs ./

comment out PLF REPOSITORY and try again

---

### Post by megamaced on 2007-06-12
Yes, as Foxy said, comment out the PLF repo, then run "sudo aptitude update" again.

---

### Post by ubuntubrian on 2007-06-12
Yes! Now I just need to do everything else and hopefully I'll have the backport.
Thanks guys! I'm sure I'll be back soon with more questions.:p

---

### Post by ubuntubrian on 2007-06-12
OK-this takes some effort but I'm game!
Commenting out the repository in ? worked and vlc downloaded just fine. I edited the debian/control file and got rid of every version number I could find. I ran prevu in the vlc directory and got some dependency issues;

 -> Considering  linux-libc6-dev
   -> Trying linux-libc6-dev
       -> Cannot install linux-libc6-dev; apt errors follow:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-libc6-dev
W: Unable to locate package linux-libc6-dev
E: Could not satisfy build-dependency.


SO I guess that I can use prevue to backport these also? I know another came up because I again edited the control file and just changed the "linux-lib-dev" to libc6-dev as I know that exists. the compile ran until another dependency issue. that's when I decided to change the control file back to "linux-libc-de" and then run:

"prevu linux-lbc-dev"

I get this:

"Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

The only error I see in the attempt is this:
"-> Considering  kernel-wedge (>= 2.24ubuntu1)
      Tried versions: 2.05ubuntu5
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency."

So do I have to do "apt-get source  linux-lbc-dev", strip the dependencies, etc and go on to the next one?

Thanks!:)

---

### Post by megamaced on 2007-06-12
The "linux-libc6-dev" package exists under Dapper, but just under a different name. Package names sometimes change between Ubuntu versions, and this can make backporting slightly tougher as you need to discover what the "old" name was.

The "linux-libc6-dev package" in Dapper is called "linux-kernel-headers", so you will need to make the change in the control file.

Also, you will need to replace "xlibmesa-gl-dev" with "x11proto-gl-dev" in the control file.

I went as far as checking the rest of the dependencies, but I didn't actually compile the package... That's your job! ;)

You might find this package search tool useful:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

That's pretty much what I use to discover the different package names

---

### Post by ubuntubrian on 2007-06-12
Many thanks Megamaced! I started down the path that I mentioned in my last post and that is a deep rabbit hole! I thought that the names may just need changing but didn't know the alternatives.
I really appreciate your help! I will compile away and post the results.:)

---

### Post by ubuntubrian on 2007-06-12
> You might find this package search tool useful:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I can see how to search for the packages but not how to see how the different names correlate. Sorry for the high density of my brain!

---

### Post by ubuntubrian on 2007-06-12
The build of vlc failed-thank god! The build wanted to install 239 new packages and use 278MB of disk. Luckily it crapped out with:

 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/14983 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 148, in ?
    BackportCurrentDir(DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.


This may not be a suitable package to backport?

---

### Post by megamaced on 2007-06-13
I'll try to compile it myself tonight if I get time

---

### Post by ubuntu_demon on 2007-06-13
I'm trying to build a Dapper backport of bittornado from Gutsy on my laptop running Feisty. To do this I have to modify the debian control and rules files and I need some help.

I added both Dapper and Gutsy sources to my /etc/apt/sources.list

```

DIST=dapper sudo prevu-init
apt-get source bittornado
cd bittornado-0.3.18/

```
[B]
I editted debian/control and removed versions from python-support and debhelper. I removed the package target bittornado-gui because I don't need it.

I editted debian/rules and changed dh_pysupport to dh_python.

I also tried "dh_python /usr/share/python-support/bittornado/BitTornado" instead of dh_pysupport
[/B]

```

DIST=dapper prevu

```

The package builds without problems. I copied the package to my Dapper box and installed it without problems. 

But there is a problem when I try to run bittornado :

> 
$ btlaunchmanycurses.bittornado
Traceback (most recent call last):
  File "/usr/bin/btlaunchmanycurses.bittornado", line 8, in ?
    from BitTornado import PSYCO
ImportError: No module named BitTornado
depjayds@p3-animal:~$ btlaunchmany
Traceback (most recent call last):
  File "/usr/bin/btlaunchmany", line 6, in ?
    from BitTornado import PSYCO
ImportError: No module named BitTornado


The directory /usr/share/python-support/bittornado/BitTornado exists and contains files (including __init__.py). 

So for some reason python can't find the python-package BitTornado (which is  /usr/share/python-support/bittornado/BitTornado). Ideally I would like to fix this in bittornado-0.3.18/debian and make a package which does this.

**Any ideas ?**

---

### Post by ubuntubrian on 2007-06-13
In looking further at the output I see these errors with my repositories:

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.16-0ubuntu3.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.16-0ubuntu3.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/file/file_4.16-0ubuntu3.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file/file_4.16-0ubuntu3.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5ubuntu0.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5ubuntu0.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.8rel-5ubuntu0.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.8rel-5ubuntu0.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]


And:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libmagic1 4.16-0ubuntu3.1
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main file 4.16-0ubuntu3.1
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libpng12-0 1.2.8rel-5ubuntu0.1
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libpng12-dev 1.2.8rel-5ubuntu0.1
  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.16-0ubuntu3.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.16-0ubuntu3.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/file/file_4.16-0ubuntu3.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file/file_4.16-0ubuntu3.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5ubuntu0.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.8rel-5ubuntu0.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.8rel-5ubuntu0.1_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-dev_1.2.8rel-5ubuntu0.1_powerpc.deb)  404 Not Found [IP: 91.189.89.6 80]


You can see my sources.list earlier in the thread. Any ideas why these packages aren't found?

Muchas gracias!  :)

---

### Post by ubuntubrian on 2007-06-13
I checked one of the error sites, "Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main libmagic1 4.16-0ubuntu3.1
404 Not Found [IP: 91.189.89.6 80]" 

and found:

Package: libmagic1
Priority: standard
Section: libs
Installed-Size: 1576
Maintainer: Michael Piefel <piefel@debian.org>
Architecture: powerpc
Source: file
Version: 4.16-0ubuntu3.2

My sources.list doesn't have an "archive.ubuntu.com..." as you can see in the earlier post. Do I just add that repository?

---

### Post by megamaced on 2007-06-13
That's for Power PC. If you are on i386 then you don't need the powerpc packages

---

### Post by ubuntubrian on 2007-06-13
I should have said that I am on Power PC.

---

### Post by Tommy on 2007-06-13
> **ubuntubrian said:**
> I should have said that I am on Power PC.


Apparently the auto-generated sources.list is broken for PowerPC -- try comparing and adjusting yours as described here: [http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

P.S.: I have been using PowerPC myself but have temporarily "jumped ship" to Intel for my main work and will tinker with PowerPC on a system that ISN'T holding my daily work. Dapper still works on PowerPC but it's getting really dated and sadly, more critical stuff has broken with each subsequent release.

---

### Post by Tommy on 2007-06-13
I'm new to prevu -- (not new to linux so I know more than enough to be dangerous ;-) )

I'm trying to install and test the latest version of gnucash for the good reasons described in [https://bugs.launchpad.net/feisty-backports/+bug/113712/](https://bugs.launchpad.net/feisty-backports/+bug/113712/)

I tried to take a couple of shortcuts, and maybe that has bitten me.

I just did a clean install to Ubuntu Feisty 7.04, i386 Desktop.

I installed prevu using synaptic (not downloading from Sourceforge)
I checked the "feisty-backports" checkbox in Synaptic (not editing the sources.list because to me it looked OK)
I added file:///var/cache/prevu/feisty-debs /. to the end of sources.list because it sounded like a good idea

When I issued the prevu gnucash command, it apparently grabbed the source for the CURRENT version of gnucash in Feisty (gnucash_2.0.2-3ubuntu1) not the one I was hoping for (gnucash 2.0.5). I'm letting it run to make sure I understand the prevu procedure (so far so good).

I see that gutsy has 2.0.5-1ubuntu1 in it, but I don't know how to tell if it's in Backports. I'm guessing it itsn't, despite having a bug in launchpad.

How can I tell what's in Backports, and more importantly make sure I will get the version I'm looking for?

Edit: prevu just finished with gnucash and despite tons of errors (lots of "file be moved" errors apparently due to the lack of libxslt, but it reported success) it created the two gnucash debs as expected. Now I'll just grab the latest source deb and run prevu "manually" -- BTW should the manual procedure be mentioned in your excellent howto at [http://ubuntuforums.org/showthread.php?t=293988](http://ubuntuforums.org/showthread.php?t=293988) ? I can understand how you want to keep it simple, but some of the other options are not evident to us newbies.

Edit2: I believe gnucash is not in backports because it doesn't fit all the backports rules -- it's a "universe" package. Since the package is in gutsy I just added  ```
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe
``` to my sources.list -- but I just realized I probably should have just put "universe" in there to avoid "polluting" the build environment. Is that correct, or am I mis-understanding how prevu works?

---

### Post by ubuntubrian on 2007-06-13
Well I was disappointed when Apple went Intel and now I'm confronted with the problem again it seems. I can find the repos that apt complains about and if I knew the correct link addresses I would just add those to my sources.list.
I would like to upgrade to Feisty but am worried about breakage, especially since there was apparent trouble with the Feisty PPC code and boxes not booting all the way requiring editing the boot code-yikes!!
I have a Beta live cd that boots and runs great but I'd really have to take a leap of faith to do a distro upgrade. 
Especially after tommy says the later distros just "break"!
Maybe I'll find some other x86 box for cheap.

---

### Post by Tommy on 2007-06-13
> **ubuntubrian said:**
> I have a Beta live cd that boots and runs great but I'd really have to take a leap of faith to do a distro upgrade. 
Especially after tommy says the later distros just "break"!
Maybe I'll find some other x86 box for cheap.

Now we're Off Topic but please don't take my comments TOO hard -- if you have a liveCD that works great then it's likely Feisty will work great on your system. I have a 1998-vintage Mac that runs Dapper pretty well but after that the world seriously passes it by.

FORTUNATELY, it's tools like prevu that will help PPC keep going -- the more packages you can test and help fix bugs, the more packages will keep working for PowerPC -- it is a COMMUNITY supported version, after all. Sorry I was a bit down when I posted that.

---

### Post by ubuntubrian on 2007-06-14
Back on topic then. I don't see a big difference in my sources.list and the one on the site you posted Tommy. Can you help out any further?
Thanks!
:)

---

### Post by ubuntubrian on 2007-06-14
I've been checking repo lists all over Ubuntu forums and the only thing that I see is that occasionally there is a / after ubuntu and sometimes not. As in:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

versus:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

the distro doesn't seem to matter re: the syntax.

The weird gzip error seems to have something to do with the repos but all the posts regarding it don't seem to have an answer.

Thanks!
:)

---

### Post by Tommy on 2007-06-14
> **ubuntubrian said:**
> I've been checking repo lists all over Ubuntu forums and the only thing that I see is that occasionally there is a / after ubuntu and sometimes not. 
You are correct that the difference is not material -- either should work.

I had to search this (gigantic) thread to find your sources list -- I presume its the one in this message [http://ubuntuforums.org/showthread.php?p=2829901#post2829901](http://ubuntuforums.org/showthread.php?p=2829901#post2829901)

I presume you realize that lines with # are comments. (ALSO you can condense repository descriptions a couple of different ways so sometimes you have to "translate" when they're written differently.

I just realized you're apparently running Dapper -- my sources list in Dapper looks simpler (I've tried all sorts of different things and keep going back to simpler.  I need to go at the moment but I have a note in my sources list that I got mine from [http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html](http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-add-extra-repositories.html)
and the only difference between mine and that one is I didn't add the plf repositories because I couldn't get them to work. I would suggest that you could start by making a copy of your sources.list, copy in the one at that web site, and adding a # at the beginning of any lines that you're not certain about (like the plf ones).

---

### Post by ubuntubrian on 2007-06-14
Thanks Tommy. I redid my sources.list with a hybrid of your suggestions and this:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

I commented out the repos that won't load and finally got a version of the list that loads all the repos.
I'll have to think of another package to backport and try as VLC seems problematic.

thanks again for the effort and yes, i want to be part of the community that helps solve problems!

:p

---

### Post by chandra on 2007-06-15
> it fails with this error message:
-----
-> Considering build-dep tex-common (>= 1.7)
Tried versions: 1.7~7.04prevu1 0.42
-> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
-----
Why is this so and what must I do to get a successful build?

Thanks to Frank Küster and John Dong, the solution is to modify the
Build-Depends for tex-common from 

tex-common (>= 1.7) 

to 

tex-common (>= 1.7~).

[COLOR="Red"]Update: Since tex-common-1.9 is now available this is no more a
problem. Instead of tex-common-1.7, use tex-common-1.9, or whatever is most
current in the source repository, in the steps below.[/COLOR]

The complete method for making a texlive-full installation on Feisty using
sources for TexLive 2007 from Gutsy is given below:

```
sudo apt-get install prevu
```

Edit /etc/apt/sources.list to to add the following:

```
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe
multiverse
```

```
sudo apt-get update
```

Create a directory in which to download TeXLive 2007 sources. Let us call
this directory ~/Build

```
cd ~/Build
sudo apt-get source tex-common texlive-base texlive-bin texlive-doc
texlive-extra texlive-lang context lmodern dvipdfmx
```

Once the packages have been downloaded
```
cd tex-common-1.7;prevu
```

This should build
/var/cache/prevu/feisty-debs/tex-common_1.7~7.04prevu1_all.deb

```
sudo dpkg -i
/var/cache/prevu/feisty-debs/tex-common_1.7~7.04prevu1_all.deb
```

It should install successfully.

```
sudo prevu-update 
```

[COLOR="Red"]Update: -------- What is below may now be left out --------[/COLOR]

Change the Build-Depends dependency line for tex-common from
tex-common (>= 1.7) to tex-common (>= 1.7~)
for each of the following files:

~/Build/texlive-bin-2007/debian/control
~/Build/texlive-base-2007/debian/control
~/Build/texlive-doc-2007/debian/control
~/Build/texlive-extra-2007/debian/control
~/Build/texlive-lang-2007.dfsg.1/debian/control

Make sure that the change does not introduce an artificial line break.

[COLOR="Red"]Update:-------- What is above may now be left out --------[/COLOR]

Build the new texlive 2007 packages with:

```
cd ~/Build/texlive-bin-2007
prevu cd ~/Build/texlive-base-2007
prevu cd ~/Build/texlive-doc-2007
prevu cd ~/Build/texlive-extra-2007
prevu cd ~/Build/texlive-lang-2007.dfsg.1
prevu cd ~/Build/context-2007.04.17
prevu cd ~/Build/lmodern-1.010x
prevu cd ~/Build/dvipdfmx-20061211
```

You should then be able to do:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

This should install your new texlive 2007 distribution without further ado.

[COLOR="Red"]Update: Check that dvipdfmx is installed by doing 
```
dpkg -l dvipdfmx
```
If it is not,
```
sudo dpkg -i
/var/cache/prevu/feisty-debs/dvipdfmx_20061211-2~7.04prevu1_i386.deb
```
[/COLOR]

In case that does not work, you may have to try the workaround below:

-------- Start of workaround --------
Uninstall texlive-full 2005 if you already have it installed in feisty:

```
sudo apt-get remove texlive-full
```

Copy and paste any packages that are removed as a consequence of this into a
temporary file, called say, ~/Removed.txt. You will need to re-install those
packages that are not prefixed by "texlive-" or "tetex-" after you have
installed the new texlive packages that you are building.

Then install the texlive 2007 packages with:
```
cd /var/cache/prevu/feisty-debs
sudo dpkg -i *.deb
```
(assuming you are starting out with a clean /var/cache/prevu/feisty-debs
directory). Otherwise, just install the list of built packages that you wish to
have on your system.

There will be some failures because of dependencies on packages that you
removed when you removed texlive-full. Cut and paste those package names from
~/Removed.txt  that do not have "texlive-" or "tetex-" in them and run

```
sudo apt-get install <insert names of removed packages here>
```

Repeat with

```
cd /var/cache/prevu/feisty-debs
sudo dpkg -i *.deb
```
-------- End of workaround --------

You should now have a fully functional texlive-full installation of the
TeXLive 2007 distribution.

If there are any problems or errors, please list them so that this process
can be made robust.

Chandra

---

### Post by ubuntubrian on 2007-06-17
In my seemingly never-ending quest to get media functionality in Dapper PPC I have tried backporting xine-lib so I can play .flv files in DemocracyPlayer. 
there are many, many dependencies that Dapper does not have and that won't build in Dapper.
Should I use Prevu, or try to at least, to backport all the dependencies? Assuming I do that then what do I do?
I used to just down load rpms for ppc and convert them to debs with alien and install them with dpkg, hunting down dependencies as I went. I would much rather correctly build a backport, if possible.
Thanks

:popcorn:

---

### Post by knight_killer on 2007-06-18
Hi,
i'm a noob to prevu (and Ubuntu) and I just try to backport Trac 0.10.4-2 from gusty to my feisty. Well, I made this:
```
apt-get install prevu
```
that works well. Then:
```
prevu --help
```
and I get this:
```
I: Building against currently running distro:sh: lsb_release: not found
Traceback (most recent call last):
  File "/usr/bin/prevu", line 168, in <module>
    DIST=os.popen('lsb_release -c').read().split(':')[1].strip()
IndexError: list index out of range
```

I get always the same error, when I want to do something with prevu (e.g. prevu-init)

Did I something wrong?

---

### Post by ubuntubrian on 2007-06-18
I'm trying to backport Swf-player from Gutsy to Dapper. Everything downloaded, configure worked great and the build started and ran great until 

```
/bin/sh: dh_gtkmodules: command not found
make: *** [binary-install/swf-player] Error 127
Copying back the cached apt archive contents
 -> new cache content libgstreamer0.10-0_0.10.6-0ubuntu2_powerpc.deb added
 -> new cache content libgstreamer-plugins-base0.10-0_0.10.7-0ubuntu5_powerpc.deb added
 -> new cache content libgstreamer0.10-dev_0.10.6-0ubuntu2_powerpc.deb added
 -> new cache content libgstreamer-plugins-base0.10-dev_0.10.7-0ubuntu5_powerpc.deb added
 -> new cache content liboil0.3_0.3.7-0ubuntu5_powerpc.deb added
 -> new cache content liboil0.3-dev_0.3.7-0ubuntu5_powerpc.deb added
 -> new cache content mozilla-browser_2%3a1.7.12-1.1ubuntu2_powerpc.deb added
 -> new cache content mozilla-dev_2%3a1.7.12-1.1ubuntu2_powerpc.deb added
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> unmounting /var/cache/prevu/src/23718 filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/23778 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 148, in ?
    BackportCurrentDir(DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
```

I googled the gtk error but found nothing. Any ideas?

---

### Post by kitterma on 2007-07-12
> **knight_killer said:**
> Hi,
i'm a noob to prevu (and Ubuntu) and I just try to backport Trac 0.10.4-2 from gusty to my feisty. Well, I made this:
```
apt-get install prevu
```
that works well. Then:
```
prevu --help
```
and I get this:
```
I: Building against currently running distro:sh: lsb_release: not found
Traceback (most recent call last):
  File "/usr/bin/prevu", line 168, in <module>
    DIST=os.popen('lsb_release -c').read().split(':')[1].strip()
IndexError: list index out of range
```

I get always the same error, when I want to do something with prevu (e.g. prevu-init)

Did I something wrong?

Open a console and try:

lsb_release -c

It should return:

Codename:       feisty

If it doesn't, you have a system problem unrelated to prevu.  If it does, please report a prevu bug in launchpad.

---

### Post by jdong on 2007-07-12
```

I: Building against currently running distro:sh:** lsb_release: not found**

```

It's claiming you do not have the lsb_release command! This is in the base installs of Ubuntu, so hmm I have no idea why it wouldn't work :(


P.S. I am working on a web service of prevu, where you can actually just use a web-based point-and-click interface to request a backport, it will **automatically build via prevu**, then output an APT repository you can use to download the packages. it will be super cool if I can get it to work :D

---

### Post by foxy123 on 2007-07-13
> **jdong said:**
> 
P.S. I am working on a web service of prevu, where you can actually just use a web-based point-and-click interface to request a backport, it will **automatically build via prevu**, then output an APT repository you can use to download the packages. it will be super cool if I can get it to work :D

Wow! It will be absolutely fantastic!

---

### Post by ubuntubrian on 2007-07-23
You will be my newest and best hero!!

[-o<

---

### Post by jdong on 2007-07-23
[http://sharkattack.media.mit.edu/](http://sharkattack.media.mit.edu/)

surprise!!!

Still some kinks and memory leaks and facelifts I'm working on, but it's totally functional :)

---

### Post by megamaced on 2007-07-25
> **jdong said:**
> [http://sharkattack.media.mit.edu/](http://sharkattack.media.mit.edu/)

surprise!!!

Still some kinks and memory leaks and facelifts I'm working on, but it's totally functional :)

That's really neat!

---

### Post by fuoco on 2007-07-27
I made symlinks from /var/cache/prevu{builds,src} to my home directory on another partition, so that I have more space when building.stuff (my root partition is too restrained). 
That works great really. The only issue is that it won't save the downloaded dependencies where it can later on reuse them for another build or a rebuild. So everytime I build something it downloads the entire list of dependencies from scratch. Is there some way around it? is this a bug?
I get lots of warnings like:

 -> new cache content libwww-perl_5.805-1_all.deb added
ln: creating hard link `/var/cache/pbuilder/aptcache//libwww-perl_5.805-1_all.deb' to `/home/gad/prevu/build-tmp/29010/var/cache/apt/archives/libwww-perl_5.805-1_all.deb': Invalid cross-device link

etc..

---

### Post by jdong on 2007-07-27
You should also change /var/cache/pbuilder/aptcache/ to a symlink to somewhere onthe same device as your prevu builders.

---

### Post by fuoco on 2007-07-27
> **jdong said:**
> You should also change /var/cache/pbuilder/aptcache/ to a symlink to somewhere onthe same device as your prevu builders.

thanks, that helps!

---

### Post by hfdragon on 2007-08-19
I just installed prevu, run prevu-init, and tried to backport some apps.

Each time I get this (or a similar) error :

> cp: cannot create regular file `/var/cache/pbuilder/result/tomboy_0.7.4-0ubuntu1~7.04prevu1.dsc': Permission denied

Should I run prevu with sudo ?:confused:

---

### Post by jdong on 2007-08-19
No, you should run sudo prevu-update to reset permissions.

---

### Post by hfdragon on 2007-08-19
> **jdong said:**
> No, you should run sudo prevu-update to reset permissions.

I don't know why, but it's not working.. :-(

I still get this kind of error :
> cp: cannot create regular file `/var/cache/pbuilder/result/backuppc_3.0.0-3ubuntu1~7.04prevu1.dsc': Permission denied


---

### Post by jdong on 2007-08-19
Hmm, it's trying to save the results to the wrong place. What version of prevu is this, and where was it downloaded from? Have you previously done any setup work with pbuilder?

---

### Post by hfdragon on 2007-08-20
Version is 1:0.4.1bzr46-0ubuntu2 (feisty)

And I got ,it from universe (archive.ubuntu.com/universe)

Edit : I tested prevu on another machine with feisty installed and it worked all right... so I think maybe one of the dependencies isn't OK, I'l need some time to check that..

---

### Post by hfdragon on 2007-08-20
Ok, I found which packacge was 'faulty'.

I got pbuilder version form telemail.fi (which I added to my sources.list to get thunderbird 2.0) with a version number : 0.169ubuntu1~feisty0.1 

Changed it back to the 0.161ubuntu2 (from the ubuntu repos) and now prevu is working correctly :)

---

### Post by jdong on 2007-08-20
ah, ok, good. What happened was that your other pbuilder wasn't respecting the option to set the results directory. Prevu forces the results to be placed in /var/cache/prevu/DISTRO-debs where DISTRO is your Ubuntu version. However, your pbuilder was ignoring this directive and trying to shove it in /var/cache/**pbuilder/results**, which indeed the regular user cannot write to.

---

### Post by berteh on 2007-10-03
Thanks for this great tool!

I could backport sqlite3 from gutsy to dapper in no time, with a small change to debian/control for replacing ${binary:Version} (unknown in Dapper) to ${Source-Version} (deprecated in gutsy).

Next candidate: Tracker ([http://www.tracker-project.org](http://www.tracker-project.org))... hope this will work as smooth.. I'll keep you posted.

Thanks again for the time gained!
B.

---

### Post by berteh on 2007-10-03
a few quick questions:

1) is there anyway to get back the source package prevu created after a successful backport with prevu?
2) is there a way to get back a *signed* source package... something like the result of "debuild -S -sa"?

thanks!
B.

---

### Post by kjsaw on 2007-10-12
Can anyone give advice on how to solve this problem; It looks like the makefile is needs to change the way if references these directories, However I am not sure how I can change the Makefile to work around the problem.

```
Creating directory /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man
Creating directory /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man/man1
/usr/bin/install -c -m 644 ../Misc/python.man \
                /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man/man1/python.1
make[1]: Leaving directory `/var/cache/prevu/src/16676/python2.5-2.5.1~rc1/build-static'
: # remove files, which are not packaged
rm -f debian/tmp/usr/bin/smtpd.py
: # move manpages to new names
if [ -d debian/tmp/usr/man/man1 ]; then \
            mkdir -p debian/tmp/usr/share/man; \
            mv debian/tmp/usr/man/man1/* debian/tmp/usr/share/man/man1/; \
            rm -rf debian/tmp/usr/man/; \
        fi
mv: target `debian/tmp/usr/share/man/man1/' is not a directory: No such file or directory
mv debian/tmp/usr/share/man/man1/python.1 \
                debian/tmp/usr/share/man/man1/python2.5.1
mv: cannot stat `debian/tmp/usr/share/man/man1/python.1': No such file or directory
make: *** [stamp-install] Error 1
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> unmounting /var/cache/prevu/src/16676 filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/16748 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

Thanks

---

### Post by jdong on 2007-10-12
> **berteh said:**
> a few quick questions:

1) is there anyway to get back the source package prevu created after a successful backport with prevu?
2) is there a way to get back a *signed* source package... something like the result of "debuild -S -sa"?

thanks!
B.


No; there isn't; if you need to sign the source or get source packages, then you should have the knowledge to do this by hand ( a simple dch -i, edit the changelog with the correct version number, then debuild -S -sa)

prevu is intended for people who are unfamiliar with the Debian packaging tools and simply want to do a personal backport.

---

### Post by Phred on 2007-10-22
> **jdong said:**
> ah, ok, good. What happened was that your other pbuilder wasn't respecting the option to set the results directory. Prevu forces the results to be placed in /var/cache/prevu/DISTRO-debs where DISTRO is your Ubuntu version. However, your pbuilder was ignoring this directive and trying to shove it in /var/cache/**pbuilder/results**, which indeed the regular user cannot write to.

Under Gutsy with pbuilder 0.170ubuntu1, I always get the same error as hfdragon (see reply [#234]("http://ubuntuforums.org/showpost.php?p=3218109&postcount=224")) :
```
cp: cannot create regular file `/var/cache/pbuilder/result/ikiwiki_2.10~7.10prevu1.dsc': Permission denied
```

I tried to run sudo prevu-update but it didn't work.
Any ideas ? :confused:

---

### Post by jdong on 2007-10-23
> **Phred said:**
> Under Gutsy with pbuilder 0.170ubuntu1, I always get the same error as hfdragon (see reply [#234]("http://ubuntuforums.org/showpost.php?p=3218109&postcount=224")) :
```
cp: cannot create regular file `/var/cache/pbuilder/result/ikiwiki_2.10~7.10prevu1.dsc': Permission denied
```

I tried to run sudo prevu-update but it didn't work.
Any ideas ? :confused:

This might be a valid bug -- please report it on Launchpad, ubuntu, package prevu, and subscribe me (jdong).... otherwise I'll forget to look at it :)

---

### Post by Phred on 2007-10-25
> **jdong said:**
> This might be a valid bug -- please report it on Launchpad, ubuntu, package prevu, and subscribe me (jdong).... otherwise I'll forget to look at it :)

Done ! :-)
See [LP #157196]("https://bugs.launchpad.net/ubuntu/+source/prevu/+bug/157196")

By the way : Thanks a lot for PREVU, it's really a great tool.

---

### Post by djbloc on 2007-11-07
> **jdong said:**
> 
P.S. I am working on a web service of prevu, where you can actually just use a web-based point-and-click interface to request a backport, it will **automatically build via prevu**, then output an APT repository you can use to download the packages. it will be super cool if I can get it to work :D

Did the web service happen in the end? It seems a great idea :)

---

### Post by jdong on 2007-11-07
It happened for a while but the build machine was overwhelmed by constant builds and is in perpetual hardware failure mode right now... I'm looking for another victim (err, replacement server) to bring the interface back up.

---

### Post by smartboyathome on 2007-11-08
> **kjsaw said:**
> Can anyone give advice on how to solve this problem; It looks like the makefile is needs to change the way if references these directories, However I am not sure how I can change the Makefile to work around the problem.

```
Creating directory /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man
Creating directory /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man/man1
/usr/bin/install -c -m 644 ../Misc/python.man \
                /var/cache/prevu/src/16676/python2.5-2.5.1~rc1/debian/tmp/usr/man/man1/python.1
make[1]: Leaving directory `/var/cache/prevu/src/16676/python2.5-2.5.1~rc1/build-static'
: # remove files, which are not packaged
rm -f debian/tmp/usr/bin/smtpd.py
: # move manpages to new names
if [ -d debian/tmp/usr/man/man1 ]; then \
            mkdir -p debian/tmp/usr/share/man; \
            mv debian/tmp/usr/man/man1/* debian/tmp/usr/share/man/man1/; \
            rm -rf debian/tmp/usr/man/; \
        fi
mv: target `debian/tmp/usr/share/man/man1/' is not a directory: No such file or directory
mv debian/tmp/usr/share/man/man1/python.1 \
                debian/tmp/usr/share/man/man1/python2.5.1
mv: cannot stat `debian/tmp/usr/share/man/man1/python.1': No such file or directory
make: *** [stamp-install] Error 1
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> unmounting /var/cache/prevu/src/16676 filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/16748 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 146, in ?
    BackportFromAPT(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 86, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 67, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

```

Thanks

This happens to me also. Would someone help please? :confused:

---

### Post by fuoco on 2007-11-09
Using prevu in gutsy I keep getting these errors at the end of a backporting:

cp: cannot create regular file `/var/cache/pbuilder/result/libtelepathy_0.2.0-1~7.10prevu1.dsc': Permission denied

What's wrong?

---

### Post by jdong on 2007-11-09
It's a bug in prevu thanks to pbuilder's behavior changing behind my back. [https://bugs.edge.launchpad.net/ubuntu/+source/prevu/+bug/157196](https://bugs.edge.launchpad.net/ubuntu/+source/prevu/+bug/157196)

It has been fixed in Hardy but the hardy builders have not processed it into debs yet. I will backport it as soon as that is done.

---

### Post by fuoco on 2007-11-12
I now get many times at the end an error:

cp: cannot stat `../<debian-x@lists.debian.org>': No such file or directory
Prevu Error: Build failed.


what is that? many packages give me that error - after successfully building (but i get no .deb) - while others work just fine..

---

### Post by jdong on 2007-11-12
> **fuoco said:**
> I now get many times at the end an error:

cp: cannot stat `../<debian-x@lists.debian.org>': No such file or directory
Prevu Error: Build failed.


what is that? many packages give me that error - after successfully building (but i get no .deb) - while others work just fine..
Install the binary pbuilder deb file from Hardy. This is actually a pbuilder bug, that prevu caught and is now fixed in Hardy. Apologies for that mess...

---

### Post by Phred on 2007-11-13
> **jdong said:**
> Install the binary pbuilder deb file from Hardy. This is actually a pbuilder bug, that prevu caught and is now fixed in Hardy. Apologies for that mess...

It seems to me that the pbuilder deb for Hardy is not installable/rebuildable on Gutsy.
So an alternate way is to use the pbuilder package I have rebuilt with your patch :
[https://bugs.launchpad.net/ubuntu/+source/prevu/+bug/157196/comments/9](https://bugs.launchpad.net/ubuntu/+source/prevu/+bug/157196/comments/9)

---

### Post by jdong on 2007-11-13
Ah, good point. If that is the case, then I will follow up with a SRU (Stable Release Update) against Gutsy for the pbuilder bug.

---

### Post by F-3582 on 2007-11-14
By the way: Should prevu be run as root?

---

### Post by jdong on 2007-11-14
No, you should not directly invoke it as root. However, prevu does require the user to have sudo access as one of the build processes will temporarily gain root and then lose it.

Note that this doesn't mean prevu is failsafe in security -- you should not use prevu to build source packages from untrusted persons.

---

### Post by jdong on 2007-11-19
If you are using the gutsy backports repository, prevu should have all outstanding bugs fixed and work out of the box once again.

---

### Post by zenrox on 2007-12-09
Setting DEBBUILDOPTS=
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: i386
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder and should
Depends: cdbs (>= 0.4.37), debhelper (>= 5.0.0), libgtk2.0-dev, libxss-dev, libmeanwhile-dev, libgadu-dev (>= 1:1.6+20060215-1), libnss3-dev, tcl8.4-dev, tk8.4-dev, libgstreamer0.10-dev, libgtkspell-dev, libltdl3-dev, libperl-dev, libstartup-notification0-dev, libzephyr-dev, libxml2-dev, libebook1.2-dev, libedata-book1.2-dev, libcamel1.2-dev, libdbus-glib-1-dev, dbus, python (>= 2.4), libavahi-client-dev, libavahi-glib-dev, libxml-parser-perl, libncursesw5-dev, libsasl2-dev, doxygen, liblaunchpad-integration-dev, intltool, libnm-glib-dev, libsqlite3-dev, automake, autoconf, libsilc-1.1-2-dev, libavahi-compat-howl-dev, check
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Reading package lists...
Building dependency tree...
Reading state information...
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Selecting previously deselected package pbuilder-satisfydepends-dummy.
(Reading database ... 12437 files and directories currently installed.)
Unpacking pbuilder-satisfydepends-dummy (from .../pbuilder-satisfydepends-dummy.deb) ...
dpkg: dependency problems prevent configuration of pbuilder-satisfydepends-dummy:
 pbuilder-satisfydepends-dummy depends on cdbs (>= 0.4.37); however:
  Package cdbs is not installed.
 pbuilder-satisfydepends-dummy depends on debhelper (>= 5.0.0); however:
  Package debhelper is not installed.
 pbuilder-satisfydepends-dummy depends on libgtk2.0-dev; however:
  Package libgtk2.0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libxss-dev; however:
  Package libxss-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libmeanwhile-dev; however:
  Package libmeanwhile-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgadu-dev (>= 1:1.6+20060215-1); however:
  Package libgadu-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libnss3-dev; however:
  Package libnss3-dev is not installed.
 pbuilder-satisfydepends-dummy depends on tcl8.4-dev; however:
  Package tcl8.4-dev is not installed.
 pbuilder-satisfydepends-dummy depends on tk8.4-dev; however:
  Package tk8.4-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgstreamer0.10-dev; however:
  Package libgstreamer0.10-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libgtkspell-dev; however:
  Package libgtkspell-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libltdl3-dev; however:
  Package libltdl3-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libperl-dev; however:
  Package libperl-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libstartup-notification0-dev; however:
  Package libstartup-notification0-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libzephyr-dev; however:
  Package libzephyr-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libxml2-dev; however:
  Package libxml2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libebook1.2-dev; however:
  Package libebook1.2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libedata-book1.2-dev; however:
  Package libedata-book1.2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libcamel1.2-dev; however:
  Package libcamel1.2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libdbus-glib-1-dev; however:
  Package libdbus-glib-1-dev is not installed.
 pbuilder-satisfydepends-dummy depends on dbus; however:
  Package dbus is not installed.
 pbuilder-satisfydepends-dummy depends on libavahi-client-dev; however:
  Package libavahi-client-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libavahi-glib-dev; however:
  Package libavahi-glib-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libxml-parser-perl; however:
  Package libxml-parser-perl is not installed.
 pbuilder-satisfydepends-dummy depends on libncursesw5-dev; however:
  Package libncursesw5-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libsasl2-dev; however:
  Package libsasl2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on doxygen; however:
  Package doxygen is not installed.
 pbuilder-satisfydepends-dummy depends on liblaunchpad-integration-dev; however:
  Package liblaunchpad-integration-dev is not installed.
 pbuilder-satisfydepends-dummy depends on intltool; however:
  Package intltool is not installed.
 pbuilder-satisfydepends-dummy depends on libnm-glib-dev; however:
  Package libnm-glib-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libsqlite3-dev; however:
  Package libsqlite3-dev is not installed.
 pbuilder-satisfydepends-dummy depends on automake; however:
  Package automake is not installed.
 pbuilder-satisfydepends-dummy depends on autoconf; however:
  Package autoconf is not installed.
 pbuilder-satisfydepends-dummy depends on libsilc-1.1-2-dev; however:
  Package libsilc-1.1-2-dev is not installed.
 pbuilder-satisfydepends-dummy depends on libavahi-compat-howl-dev; however:
  Package libavahi-compat-howl-dev is not installed.
 pbuilder-satisfydepends-dummy depends on check; however:
  Package check is not installed.
dpkg: error processing pbuilder-satisfydepends-dummy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pbuilder-satisfydepends-dummy
<SNIP>
then prevu sontinues to d/l all thoes same deps + others that i thinks it wants

The following partially installed packages will be configured:
  pbuilder-satisfydepends-dummy 
0 packages upgraded, 206 newly installed, 0 to remove and 0 not upgraded.
Need to get 2811kB/58.7MB of archives. After unpacking 239MB will be used.
Writing extended state information...
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main automake 1:1.10+nogfdl-1 [369kB]
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/1904 filesystem
 -> unmounting /var/cache/prevu/gutsy-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/2038 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 181, in <module>
    BackportCurrentDir(DIST).backport()
  File "/usr/bin/prevu", line 116, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 97, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/prevu", line 181, in <module>
    BackportCurrentDir(DIST).backport()
  File "/usr/bin/prevu", line 116, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 97, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.

and the final build error
so whats going on with prevu and pbuilder

---

### Post by F-3582 on 2007-12-09
**EDIT: Never mind. prevu-update did the trick.**

I have a problem, too. Prevu fails on anything that even remotely depends on Firefox preducing 404 errors whenever it tries to download it. This concerns VLC and Liferea, as of now, but I'm sure that there might be more cases. The terminal outputs the following:

```
Err http://archive.ubuntu.com gutsy-updates/main firefox 2.0.0.8+2nobinonly-0ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err http://archive.ubuntu.com gutsy-updates/main firefox-dev 2.0.0.8+2nobinonly-0ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-dev_2.0.0.8+2nobinonly-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.45 80]
Fetched 1233kB in 4s (290kB/s)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 -> Trying to fix apt error

*snip*

0 upgraded, 142 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.4MB/52.1MB of archives.
After unpacking 191MB of additional disk space will be used.
Err http://archive.ubuntu.com gutsy-updates/main firefox 2.0.0.8+2nobinonly-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com gutsy-updates/main firefox-dev 2.0.0.8+2nobinonly-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-dev_2.0.0.8+2nobinonly-0ubuntu1_i386.deb  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
E: Unrecoverable error installing build-dependencies.

*snip*

Prevu Error: Build failed.
```

Notice the requested package by prevu (2.0.0.8) is three version numbers behind the actually installed package (2.0.0.11). Go figure...

Also note that I have firefox and firefox-dev already installed.

---

### Post by ubuntubrian on 2007-12-28
I want to backport the latest Gnash player. I get a unresolved dependency:

 -> Considering  dpkg-dev (>= 1.13.19)
      Tried versions: 1.13.11ubuntu7 1.13.11ubuntu6
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.

So I tried backporting dpkg-dev which has its own dependency problem:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  debhelper: Depends: dpkg-dev (>= 1.13.13) but 1.13.11ubuntu7 is to be installed
E: Broken packages
E: Could not satisfy build-dependency.


I backported successfully debhelper and it is in my synaptic listed packages but I can't install it because, from synaptic:

debhelper:
  Depends: dpkg-dev (>=1.13.13) but 1.13.11ubuntu7 is to be installed


So I guess I have a circular dependency? Any ideas?

Thanks

:popcorn:

---

### Post by ubuntubrian on 2007-12-29
this may be due to the fact that Firefox-2.0 will not build on your version, if it's Dapper. I know that afterDapper Firefoxwas rebuilt at 2.0 version and many other packages depend on it yet it cannot be backported itself. I built it from source but only as a browser not in my PATH so that no other software links to it. Hope this is a help

---

### Post by wog on 2008-01-18
Is there a reason why the version of prevu available on sourceforge is 0.4.1, but the version I can get from Synaptic is 0.4.3?

...might want to update sourceforge at some point. :)

---

### Post by jdong on 2008-01-18
> **wog said:**
> Is there a reason why the version of prevu available on sourceforge is 0.4.1, but the version I can get from Synaptic is 0.4.3?

...might want to update sourceforge at some point. :)

Sorry, I've been keeping Sourceforge horribly up to date, mostly because SF's release mechanism is just about the most painful one I've ever used.

The real one should be branched from [https://code.launchpad.net/~ubuntu-backporters/prevu/dev](https://code.launchpad.net/~ubuntu-backporters/prevu/dev)

I recommend following that bzr branch for my  latest developments -- the stuff I check into there is usually stable and ready to push into Hardy anyway.

Also, since prevu is python, it's safe to install the deb from Hardy on Gutsy.

---

### Post by F-3582 on 2008-01-19
Or just run "prevu prevu" ;)

---

### Post by wog on 2008-01-19
While I'm at it, why is it the first section of the Backports page at [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) tells you why, how and where, but doesn't actually ever tell you *what* backports are??

Does anyone actually know what they are?

Can backports built by other people be accessed somewhere, or do we have to build them ourselves?

---

### Post by F-3582 on 2008-01-19
The wiki explains it in some tech language, yes. If you really care to know, backports are programs ported from a newer version of an operating system than you are using (e.g. from Hardy to Gutsy or drom Hardy to Dapper). This becomes necessary for some packages, because their versions won't get updated after the Feature Freeze kicks in (usually some two months before the actual release of the distribution), but they are still worth updating, anyway.

Anyone can backport programs with Prevu and if you like to make these available for everyone, just notify the Ubuntu Backports team that your build of package x was succesful. They'll add the program to the backports repository for you.

---

### Post by wog on 2008-01-19
Okay, now I understand why they're called 'backports' then. :)

So if one is using the most up-to-date version of Ubuntu, one won't actually need to use prevu unless something is updated within that six-month gap, or whenever the version updates, right?

Backporting is a completely new concept for me. I'm just trying to make sure I understand it completely.

Can later versions of Ubuntu deal with packages intended for earlier versions of Ubuntu, or will those packages need to be 'Frontported'? :)

---

### Post by jdong on 2008-01-20
> **wog said:**
> 
So if one is using the most up-to-date version of Ubuntu, one won't actually need to use prevu unless something is updated within that six-month gap, or whenever the version updates, right?

Right -- backports are for people who absolutely demand newer software than what's available with the current Ubuntu release. You're basically grabbing pieces of the development (alpha) distribution Hardy and building it against Gutsy or whatever you're running.

Unless there's some big reason why you want the newest piece of software so soon, it's probably better on yourself just to sit back and let the next Ubuntu release do that work for you :)


The Backports Project that manages the backports *repositories* (gutsy-backports) has precompiled and tested the most popularly requested and "safe" backports, so you don't have to build them yourself. Some people like to keep that repository enabled so that they can get the latest software trickling in when developers feel they're stable enough for general usage. Mission-critical or other stability conscious systems probably should not use backports, as they are not tested as heavily as the software that ships with your stable release.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) has the most in-depth explanation of what backports are.

---

### Post by jimcooncat on 2008-02-24
"Mission-critical or other stability conscious systems probably should not use backports, as they are not tested as heavily as the software that ships with your stable release."

"Pinning" helps alleviate concerns about that. I had problems with backports many versions ago (not lately), and got pinning advice from Debian. I'm very glad the Ubuntu devs included instructions in the wiki now. As far as I know, it's not done as a default when enabling the Backports repository, and it really should be IMHO.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by sfp-a7x on 2008-03-12
Here's a tricky dependency problem when backporting libclassworlds-java from Hardy to Gutsy:
[LIST=1]
[*]**prevu libclassworlds-java**
    (prevu fails saying a dependency on maven-ant-helper >= 3 was not satisfied because there is no package named 'maven-ant-helper' in Gutsy)
[*]**prevu maven-ant-helper**
    (prevu successfully creates maven-ant-helper_3~7.10prevu1)
[*]**sudo prevu-update**
    (prevu will now see maven-ant-helper_3~7.10prevu1 in all future prevu runs)
[*]**prevu libclassworlds-java**
    (prevu fails because the version of maven-ant-helper_3~7.10prevu1 is less than 3 and libclassworlds-java requires maven-ant-helper >=3)
[/LIST]
I know that the "~7.10prevu1" suffix is added to the version for a good reason -- it's to make sure that the backported package is upgraded when you do a dist-upgrade.  However, it means that dependencies can break as in the above example.  Is there a way that I can get around this?

---

### Post by jdong on 2008-03-12
You should apt-get source libclassworlds-java and edit debian/control to depend on a lower version (i.e. one with the ~7.10prevu1) of the package in question, and run "prevu" with no arguments to build that modified source.

---

### Post by sfp-a7x on 2008-03-12
> **jdong said:**
> You should apt-get source libclassworlds-java and edit debian/control to depend on a lower version (i.e. one with the ~7.10prevu1) of the package in question, and run "prevu" with no arguments to build that modified source.

Brilliant!  Worked like a charm.

Would it be worthwhile to change prevu to automatically modify dependencies to add the "~7.10prevu1" suffix when backporting?

Thanks for your help!

---

### Post by vik_777 on 2008-03-15
Hi. Thanks for such an awesome tool!!!

This is kinda related to sfp's question above:
I'm backporting Festival from Hardy to Gutsy.

Building it and it's deps were successful.
However, installing them gives me some problems.
Specifically, Festival needs a library dependency:
libestools1.2 (>= 1:1.2.96~beta-2)

The version prevu built is called:
libestools1.2_1.2.96~beta-2~7.10prevu1_i386.deb

In the control file "depends" of Festival, I have put:
libestools1.2-dev (>= 1:1.2.96~beta-2~7.10prevu1)

Edit: Just to be clear, in the control file:
Build-Depends: ... libestools1.2-dev (>= 1:1.2.96~beta-2~7.10prevu1) ...
Package: festival
Depends: ${shlibs:Depends}, ${misc:Depends} ...

when I try to install using apt-get -s install festival, I get:
The following packages have unmet dependencies:
  festival: Depends: libestools1.2 (>= 1:1.2.96~beta-2) but 1:1.2.96~beta-2~7.10prevu1 is to be installed

Is this because libestools already has a ~beta-2, and ~7.10prevu1 after it is ignored? I'm not too sure on how this kind of naming works in Debian/Ubuntu.
In any case I would like to keep the beta-2 in there for future reference.

How would I work around something like this?

P.S. I've tried removing the debs and remade them, always apt-get update-ing afterwards, with no luck. Also the Package file in /var/cache/prevu/gutsy-debs/ states that festival depends on:
libestools1.2,  libestools1.2 (>= 1:1.2.96~beta-2) [without the ~7.10prevu1]
Kinda interesting to have 2 entries there.

---

### Post by vik_777 on 2008-03-15
Figured the above out with the help of the good folks at #ubuntu-motu.
I had to edit festival's debian/shlibs.local and add the ~7.10prevu1 in to the libestools entry. 

Thanks jpatrick and Hobbsee for the help.
And thanks jdong once again for such a cool util!

[note to self] Always grep if in doubt.

---

### Post by sfp-a7x on 2008-03-24
How do I get prevu to generate signed packages?  I want to eliminate those authentication warnings.

Also, is it safe to backport dpkg?  I need a newer version of dpkg-dev to satisfy a build dependency of another package I want to backport.

---

### Post by Homer on 2008-10-22
Hello,

I'm trying to backport php 5.2 from hardy to dapper.  prevu stops at :

> Setting DEBBUILDOPTS=
 -> Attempting to parse the build-deps : pbuilder-satisfydepends,v 1.22 2005/12/04 05:16:40 dancer Exp $
 -> Considering  apache2-prefork-dev (>= 2.0.53-3)
   -> Trying apache2-prefork-dev
 -> Considering  autoconf
   -> Trying autoconf
 -> Considering  automake1.4
   -> Trying automake1.4
 -> Considering  bison
   -> Trying bison
 -> Considering  chrpath
   -> Trying chrpath
 -> Considering  debhelper (>= 3)
   -> Trying debhelper
 -> Considering  flex (>= 2.5.4)
   -> Trying flex
 -> Considering  freetds-dev
   -> Trying freetds-dev
 -> Considering  libapr1-dev (>= 1.2.7-8)
W: Unable to locate package libapr1-dev
E: No packages found
      Tried versions: 
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/10556 filesystem
 -> unmounting /var/cache/prevu/dapper-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/10662 and its subdirectories
========================
Prevu Error: Build failed.
Prevu encountered an error performing your build. The actual
error message may be further up in the scrollback before pbuilder
exited. Please look for a failed dependency or compile error in
the full output.


The package libapr1-dev seem to be the problem, but I don't know what to do with that.  Any ideas ?

Thanks !

---

### Post by ubuntubrian on 2008-10-25
I'm running on PowerPC, 8.04. When I try to use Prevu Iget this:

```
 prevu totem
I: Building against currently running distro: hardy

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 4184kB of source archives.
Get:1 http://ports.ubuntu.com intrepid/main totem 2.24.2-0ubuntu4 (dsc) [2667B]
Get:2 http://ports.ubuntu.com intrepid/main totem 2.24.2-0ubuntu4 (tar) [3714kB]
Get:3 http://ports.ubuntu.com intrepid/main totem 2.24.2-0ubuntu4 (diff) [468kB]
Fetched 4184kB in 31s (134kB/s)                                                
gpg: Signature made Fri 24 Oct 2008 01:26:11 PM MDT using DSA key ID A2D7D292
gpg: Can't check signature: public key not found
dpkg-source: extracting totem in totem-2.24.2
dpkg-source: unpacking totem_2.24.2.orig.tar.gz
dpkg-source: applying ./totem_2.24.2-0ubuntu4.diff.gz
dch warning: new version (2.24.2-0ubuntu4~8.04prevu1) is less than
the current version number (2.24.2-0ubuntu4).
W: /home/brianokeefe/.pbuilderrc does not exist
W: /home/brianokeefe/.pbuilderrc does not exist
Building the build Environment
 -> extracting base tarball [/var/cache/prevu/hardy.tgz]

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors
E: failed to extract /var/cache/prevu/hardy.tgz to /var/cache/prevu/builds/8324
========================
Prevu Error: Build failed.
Prevu encountered an error performing your build. The actual
error message may be further up in the scrollback before pbuilder
exited. Please look for a failed dependency or compile error in
the full output.

```

Prevu used to work. Now it doesn't.

---

### Post by jdong on 2008-10-25
Re-run prevu-init; the base image tarball somehow is corrupt; prevu-init rebuilds it.

---

### Post by ubuntubrian on 2008-10-25
thanks for the very quick reply. I get:
```
 sudo prevu-init
I: Building against currently running distro: hardy
W: /home/brianokeefe/.pbuilderrc does not exist
Distribution is hardy.
Building the build environment
 -> running debootstrap
/usr/sbin/debootstrap
I: Retrieving Release
I: Retrieving Packages
I: Retrieving Packages
I: Retrieving Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /var/cache/prevu/builds/8201/. mount -t proc proc /proc
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/8201 and its subdirectories
pbuilder sub-process failed!

```

---

### Post by jdong on 2008-10-25
W: Failure trying to run: chroot /var/cache/prevu/builds/8201/. mount -t proc proc /proc
pbuilder: debootstrap failed


That's a pbuilder error, not prevu's fault. Pointless blame-punting aside, are you running a grsec kernel or other hardened kernel with chroot restrictions?

---

### Post by ubuntubrian on 2008-10-25
I'm running a vanilla 2.6.24-19 kernel. The newer kernel has problems. I don't know what a grsec kernel is....
I'll boot into 24-21 and see what happens and report back.

---

### Post by ubuntubrian on 2008-10-25
As I'm running a powerpc kernel I wonder if that's the problem. PowerPc is no longer supported and is now a ported distro.
I booted into the newest kernel for Hardy for PowerPc, 2.6.24-21 and ran prevu-init:

```
sudo prevu-init
[sudo] password for brianokeefe: 
I: Building against currently running distro: hardy
W: /home/brianokeefe/.pbuilderrc does not exist
Distribution is hardy.
Building the build environment
 -> running debootstrap
/usr/sbin/debootstrap
I: Retrieving Release
E: Failed getting release file http://archive.ubuntu.com/ubuntu/dists/hardy/Release
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/7235 and its subdirectories
pbuilder sub-process failed!

```
How do I get Prevu to use the release for PowerPC? I think that it is here:
[http://ports.ubuntu.com/dists/hardy/Release](http://ports.ubuntu.com/dists/hardy/Release)

---

### Post by jdong on 2008-10-25
Ah, I think you found the problem then! I don't know of a cleaner way than to manually edit prevu, prevu-init, and prevu-update in /usr/bin with a search-and-replace. It's all legible (pretty well written) Python, so it should be self-explanatory which lines need a bit of mirror mangling :)

---

### Post by ubuntubrian on 2008-10-26
Hmmm...
I edited the appropriate files as you suggested Jdong (Thanks for the quick reply once again!). I wasn't exactly sure about the correct mirror. I tried to follow the site to the same point that would get to the /dist subdirectory as you had originally written the code. In my case that was:

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/)

as opposed to your:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

In each case they both have the same subdirectories so I'm assuming that this should work. Unfortunately I got:

```
~$ sudo prevu-init
I: Building against currently running distro: hardy
W: /home/brianokeefe/.pbuilderrc does not exist
Distribution is hardy.
Building the build environment
 -> running debootstrap
/usr/sbin/debootstrap
I: Retrieving Release
I: Retrieving Packages
I: Retrieving Packages
I: Retrieving Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /var/cache/prevu/builds/8074/. mount -t proc proc /proc
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/8074 and its subdirectories
pbuilder sub-process failed!

```

this is when booted into the 24-21 kernel too. I'm baffled.:(

---

### Post by martinistudio on 2009-10-30
Hi,

Is there a way to backport with using pbuilder but not prevu? It seems prevu changes the changelog itself and adds the extension ~prevu1 or something close to that. Can I set my own extension with prevu? ~martinistudio1 for example?

Thanks in advance,

---

### Post by jdong on 2009-10-30
Editing prevu's source code, it's fairly obvious where prevu keeps track of what version suffix to append. But prevu uses pbuilder internally.

The python code should be fairly readable; prevu is a convenience tool, it doesn't do anything mysteriously magical.

---

### Post by martinistudio on 2009-10-31
I'll look into that, thanks

Is it possible to backport a kernel?

---

### Post by jdong on 2009-10-31
> **martinistudio said:**
> I'll look into that, thanks

Is it possible to backport a kernel?

I would not recommend the use of prevu to do so, as kernel source packages in Ubuntu don't quite get version information from the debian/changelog directly.

---

### Post by martinistudio on 2009-11-10
how do you build 64bit packages on a 32bit system with prevu?

---

### Post by jdong on 2009-11-10
> **martinistudio said:**
> how do you build 64bit packages on a 32bit system with prevu?

This is not supported. Your best bet is to use a 64-bit emulator (like qemu) to build a simple virtual machine server that just runs prevu.


Building 32-bit packages in a 64-bit is equally not well supported. Your best bet there is to set up a 32-bit chroot using stock prevu inside, or have a prevu32 that sets up its prefix in /var/cache/prevu32 instead of /var/cache/prevu; then a simple matter of pbuilder init invocation hacking can build a 32-bit tarball.

---

### Post by martinistudio on 2009-11-23
Thanks, where can I find info how to set up such a 64bit emulation with qemu?
\
Can't find it...

---

### Post by martinistudio on 2009-11-26
ISn't it possible to upload the backport (made by prevu) to launchpad to enable amd64?

---

### Post by megamaced on 2010-05-10
Is there a fix for Prevu in Lucid? I've seen the bug report but no fix

---

