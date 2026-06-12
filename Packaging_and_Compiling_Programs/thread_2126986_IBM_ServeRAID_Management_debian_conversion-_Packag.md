---
title: "IBM ServeRAID Management debian conversion- Packaging help."
date: 2013-03-18
forum: Packaging and Compiling Programs
---

### Post by MAFoElffen on 2013-03-18
I am converting an old RPM package for IBM ServeRAID Storage Manager, version v9.30-17006 _2012.04.27 for personal use and challenge... for use on Ubuntu Server >= v12.04 lts. I think the original app was written back before 2004 and was for SCO UNIX, Red Hat and Suse. I have previously changed this to use on Solaris.
 
All went well "functionally." I update the Debain control file and all the applications scripts to be able to set up the correct env vars and use java scripting in Ubuntu... Now I have a few administrative "packaging" kind of problems to work out...

The original app was written in 2004(?) and the lastest update from last April (2012) still has "sun-jre142linux32.tgz.gz" included in it. I changed the scripts to see Ubuntu's conventions for ID and arch and to be able to set JAVA_HOME to the Ubuntu java-default symlink. I have the application running fine on OpenJavajkd-7. I'm thinking it included the Sun Java JRE to install on boxes that didn't include java. So, I should be able to pull this out of the applications directory without any problem as long as it is using the OpenJDK JRE right? (<-- That is question #1) the debian postinst script untars this file in the app directory... but the applaication scripts are using the system's java to run... ??? I'm thinking this is just taking up unneeded real estate.

Second issue is a depends problem somewhere... The depends in the control file had 
```

...
Depends: libc6 (>= 2.3.6-6~), libgcc1 (>= 1:4.1.1), libstdc++5 (>= 1:3.3.15)
...

```
If this dependency is as is, Dpkg would "end" install at error on dependency error- libstdc++5(>=1:3.3.17), leaving the package half-installed and unconfigured..

I looked for it. There is a symlink named "libstdc++5" pointing to an installed package named "libstdc++5:i386". Of course also there is also symlinks and packages installed for libstdc++6*... 

So I changed the control file's dependency field to:
```

Depends: libc6 (>= 2.3.6-6~), libgcc1 (>= 1:4.1.1), libstdc++5:i386 (>= 1:3.3), ia32-libs

```
Even though libstdc++5:i386 is installed and the current version is 1:3.3.6-25... It still errors out saying it couldn't find "libstdc++5". Even taking out the whole depends field out of control and it has the same error. I need help figuring this one out.

Even if I take that whole line out of the control file, on install, dpkg errors on a dependency problem with libstdc++.5 Now If I install it on force-depends-version, it still errors out, saying it can't find "libstadc++5". If I install on force-depends, it does install. On install, it runs great, as it does on other platforms- local or remote. Functionally, the edits I did on the application scripts point it to the "lidstdc++5" symlink and it works fine. So it functionally works, but it still has this annoying install error.

Since it is not getting the dpkg install error from the control file depends field... It is not getting it from debian preinst, as that just checks to make sure the app is not already installed.  Where else in the debain .deb source might dpkg be getting this error from?

---

### Post by tgalati4 on 2013-03-18
One of the issues of converting from RPM to Deb package is that the dependent packages may have similar names but different components inside.  So it is more than just satisfying the top-level dependencies, the supporting libraries need to be in-place and the API's consistent.  Since this package is so old, you might have better luck targeting 8.04 or 10.04 first and see if you can get a successful conversion/installation.  Once that is done, you have the dpkg tools available to force it into 12.04.  

If the source code is available, then you could try recompiling in 12.04 and very quickly you will discover what needs patching.  Is this package needed to work on specific hardware?  Or are your trying to resurrect this dead beast because it has a pretty GUI and it would look nice running on Ubuntu?

As far as libstc++5:

tgalati4@Mint14-Extensa ~ $ apt-cache depends libstdc++5
libstdc++5
  Depends: libc6
  Depends: libgcc1
  PreDepends: multiarch-support
    multiarch-support:i386
  Replaces: libstdc++5:i386
  Breaks: libstdc++5:i386

Check the dependencies of libgc6 and libgcc1 and compare them to the RPM build environment and note any differences.

---

### Post by MAFoElffen on 2013-03-18
Thanks. I got it working now. Depends issue was my external code management systems.  I wasn't building on the current source... so not changing to lidstdc++5:i386 builds, works and installs without error.

---

### Post by MAFoElffen on 2013-03-19
I guess I spoke too soon. I worked through the depends problem and it is installing with only a "few" minor errors... LOL The errors are stopping it from installing or running (sort of).

There are a few syntax errors going from rhel to debain that I need to convert. One is that it copies a script to "/etc/init.d", then tries to add it via "chkconfig --add <service-name>"...which I think if I challenge that to "update-rc.d <service-name> default", that should say the same in the debian way.

It runs. But there are a few challenges to make it work in a debian format and using debian resources. One is that it is installing to a /usr/<program-name> directory. I'm thinking that since that is the only program directory now showing up in ?usr/ that that is not where it should install. I think the package is arch dependent .. I converted in from a 64bit RPM package. So where should it install? So I'm thinking it's an It's an arch dependent application tha intercts with hardware, is call through shh, and can mount to other server's hardware on a network... I know it runs. I know when I get it done, I probably share how to do it to others. In keeping with my learning and practice... I should adapt it to debian conventions. Should it install in "/usr/share/"?

Even though it runs, I think it actually is using the sun java that is included with it, instead of using OpenJava from the host. I removed the sunjava jre tar and commented out the install routine that extracted that during the post install... and it failed to run. So, I'm thinking my edits to point Java_Home failed and it went to the fallback, which is calling that jre. So, I'll add some test script to trace that out to see if I can see if it really is using OpenJava and failing... which would mean that it really is Sun or Oracle Java dependent. I'm thinking that since the original script checks for different versions of Java on different Unix and Linux distro's that it might not be locked into just Sun. 

But if it does end up being tweaky about it's selection of java flavors... then should I set it up to install as an java-alternative instead of exclusive? I'm thinking that if not setup that way, that there may be problems running 2 different version instances of java at the same time.... As this is a TomCat server, I'm thinking that the likelihood may be higher than if it weren't. This server does run and "use" java. I already have this server setup as using the OpenJava JDK as a primary, with OracleJava as an alternative. Not sure just how to add an old Sun Java JRE as an alternative to an alternative... ??? That just sounds "wrong" right?

---

### Post by MAFoElffen on 2013-03-20
I'm starting to learn the .deb "format" conventions.

I'm initially installing to /usr/lib/, etc/init.d/  and /usr/share/<docs>... That's how I have it split out so far. Besides breaking it out in the directory structure of the .deb, I had to update the preinst, postinst and postrm files to that new directory structure.

I'm thinking I need to add more to the postrm file, as during testing, it's getting an error on removal. It's saying that some sub-directories are not empty. Once it gets that error, it does not remove the package from the tree. I'm having to go back and hand-remove it. (Working.)

*** Is there such thing as a "prerm" file?
In postinst it extracts an archive in the program directory structure as a sub-directory. I think I need to delete that before the removal tries to remove the normal files and directory... ???

I'm finished on the edits on this, but I can't test this on hardware until tomorrow. This server has one PS down at the moment- sounds like an airplane (loud), so I can't fire it up until the Mrs. is at work. (Tomorrow)

This utility has 2 licensing issues, that I should probably address... One is from IBM, while the other is from Adaptec. I should add an accept for those 2 licenses.(another practice/challenge kind of thing)

---

### Post by MAFoElffen on 2013-03-22
Done. Thanks for the tips.

---

