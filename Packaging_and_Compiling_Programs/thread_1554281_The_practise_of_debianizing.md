---
title: "The practise of debianizing"
date: 2010-08-16
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-08-16
Dear all, 

Slowly I am getting more grips on the entire process of packaging. First I discovered that a Personal Package Archive [PPA] on Launchpad allowed for building an Ubuntu package on a pool of servers. 

**Import source**
Now, I discovered that there is for example a simple way to get an upstream (Debian) source package:
```

mkdir delta3d; cd delta3d
bzr init debian
cd debian
bzr import-dsc http://mentors.debian.net/debian/pool/main/d/delta3d/delta3d_2.4.0-1.dsc

```
This package is created by James Goppert, thanks for that! It is awaiting sponsoring (I know now that that does not involve money) at [mentors]("http://mentors.debian.net/cgi-bin/sponsor-pkglist?action=details;package=delta3d").

**Make source up to date**
So, my first question concerns the fact that it is not entirely up to date. It is the 2.4 version provided on the Delta3D site. The Delta3D svn version contains a lot of new files, so my first question is. How do I handle such a situation? Is it possible to provide an Ubuntu package that is newer than the upstream package? Or is that generally discouraged? I can imagine that it is frowned upon to bypass such an upstream tarball. Is there some easy way to make a diff that includes the changes from the SVN of the Delta3D guys? Or are diffs not meant for that?

**Creating package**
Then I also found out that there is such a thing as:
```
 bzr builddeb -S
```
The problem is here that the source is already signed by the person who debianized it (James Goppert). It says, of course, that his secret key is not available. Do I need to sign it myself now? How would I do that? With "bzr builddeb --help" I don't see a parameter for a key, as in "debuild -S -k66666666". 

Somehow the email address used by "dch -e" (or dch -i) had become my .org address, while the GPG key used my .com address, so I had to add DEBUILD_DPKG_BUILDPACKAGE_OPTS="-k66666666 -sa" to my ~/.devscripts file. Using that, I can sign this package just fine.

**Make the code compile**
Now, let's run pbuilder:
```

sudo pbuilder --build ../delta3d_2.4.0-1ubuntu1.dsc

```
This readily complains about a dependency on Open DIS, namely libdis-dev, which is indeed not in Ubuntu or upstream Debian yet. I have emailed James Goppert about it, who has a Karmic [Launchpad PPA]("https://launchpad.net/~jgoppert/+archive/hsl"). However, I can learn something from this. I tried to retrieve this package in the same way as delta3d: 
```

bzr import-dsc https://launchpad.net/~jgoppert/+archive/hsl/+files/open-dis_2.5-hsl3.dsc

```
Regretfully, it cannot find the tarball in the same directory. I have no clue why it is not there. Is it okay for me to provide a Delta3D package without DIS? Or should downstream packages always have the same functionality as upstream ones? 

I removed the dependency from the debian/control file. And adapted the builddir/Makefile target in the debian/rules file (I included -DBUILD_DIS:BOOL=OFF as cmake option). Is the rules file indeed the file I need to adapt? The default rules file contains only one big mask:
```

%:
	dh  $@

```
Is it still the idea to add all kind of additional targets to it? Or has the policy changed over the years? Another thing, how can I specify something like make -j6 for the build process in pbuilder? There is a call to $(MAKE) in the build target in debian/rules. I might add it there, but that looks utterly ad-hoc.

Something else, is there an Ubuntu tool to extract dependencies? For example, the original debianizer stated libxxf86vm-dev as a dependency. Can I somehow check if that's indeed the case?

**Commit**
For commit it to my PPA I used:
```

dput -f ppa:robot3d_team/ppa-robot3d delta3d_2.4.0-1ubuntu1_source.changes

```
What is the purpose of debcommit? Is there a bzr tool? 

**Branch for packaging**
Should debian packaging be done in a branch separated from the pristine source? Is using bzr-pipeline like explained [here]("https://wiki.ubuntu.com/DistributedDevelopment/Documentation/NewUpstream"), common practice?

**Poll**
Is there a certain place where people can *vote* for a package before it gets into the Ubuntu / Debian repositories? Before I figure out how sponsoring works, I'd like to know what the result of such a poll would be.

Thanks for the swift responses all the time you all! And especially thanks to SevenMachines! Sorry for all the questions, but I would like to do it in the most professional way possible. If there are dedicated Ubuntu tools, I don't want to struggle with obsolete or upstream packaging methods. I have read many tutorials online, but they don't discuss alternatives, or sometimes outdated, and rarely discuss the reasoning behind the existing tools. I hope this is concrete enough to help others that encounter the same practical issues and questions.

Anne

---

### Post by SevenMachines on 2010-08-17
*** Make source up to date**
> Is it possible to provide an Ubuntu package that is newer than the upstream package? Or is that generally discouraged?Many people use ppa's to provide versions that are newer than versions in ubuntu or even than those in debian, theres even a new automatic 'daily-build' feature that should build new versions in your ppa automagically. haven't used it yet but its an interesting thing, especially when you begin to think about how it could change the way ubuntu develops and how people use it, the mind boggles :). Why ubuntu versions in its repositories don't, generally, leap-frog debian is, as far as i understand it, for a few good reasons.

* Ubuntu syncs from debian, this happens automatically unless there are ubuntu changes ( the -ubuntu1 extensions on versions). If there are changes then some ubuntu maintainer has to go through these packages after dragging themselves home from work and review the differences and ok the sync, perhaps manually merging in the ubuntu changes

* Debian has a *lot* more people working on it, why make life harder for yourself when you can benefit from all that great work.

* if the ubuntu and debian versions are the same its a lot easier to coordinate bug fixing. if someone finds and fixes a bug in ubuntu then its more likely it can be passed up to debian and fixed there (or even better, by the upstream author). That way the bug fix doesnt just help ubuntu, it helps ubuntu, it helps debian, it helps debians millions of derived distributions, and if you can get it fixed by the author, it helps absolutely everyone!

> Is there some easy way to make a diff that includes the changes from the SVN of the Delta3D guys? Or are diffs not meant for that?* You could make a patch if you wanted but its much simpler to just update the whole source package to the svn version i'd say. svn is a constantly moving (and sometimes broken) target, you could find yourself with *huge* and confusing patches.


** * Creating package**
> Do I need to sign it myself now? How would I do that?ppa's require the person who made the last debian/changelog entry to sign the package to be uploaded. debuild should ask you towards the end of the build.



** * Making the Code Compile**
> Is it okay for me to provide a Delta3D package without DIS? Or should downstream packages always have the same functionality as upstream ones? Can't see why not, you'll often see packages being packaged in debian with various elements 'turned off' for one reason or another. You can though, either add a libdis package to the same ppa, the delta3d build will automatically use the packages in the same ppa. You could also a different ppa from the webpage which would also be used for build dependencies in the delta3d ppa.

> Is the rules file indeed the file I need to adapt? The default rules file contains only one big mask:
Code:

%:
    dh  $@

This basically runs all the debhelper goodness. Normally you would add any environment variables and so on to it but I know nothing about cmake at all. maybe DEB_CMAKE_EXTRA_FLAGS := -DBUILD_DIS:BOOL=OFF or something like that. You can also override debhelpers build step if it seems easier. See [https://wiki.duckcorp.org/DebianPackagingTutorial/CDBS](https://wiki.duckcorp.org/DebianPackagingTutorial/CDBS) for a good explanation of some of the various things you can do.


> how can I specify something like make -j6 for the build process in pbuilder? use the pbuilder option --debbuildopts "-j6", see man pbuilder

>  --debbuildopts [options]

              List of options that are passed on to dpkg-buildpackage.  Multi&#8208;
              ple flags are additive and appended ot the any  value  given  in
              DEBBUILDOPTS  as  specified in pbuilderrc.  To clear the list of
              options, pass the empty string, e.g.  --debbuildopts "".

              Multiple options are delimited with spaces, like  --debbuildopts
              "-j100 -E"

> Something else, is there an Ubuntu tool to extract dependencies? For example, the original debianizer stated libxxf86vm-dev as a dependency. Can I somehow check if that's indeed the case?debhelper does clever things for binaries dependencies (see  ${shlibs:Depends} in your control file) but i dont know of any build depends tool so if you hear of one let me know! just the dependencies listed in INSTALL files, the homepage, configure is what i tend to look at. pbuilder will dutifully but helpfully complain if we get them wrong :)

** *Commit**
> What is the purpose of debcommit? Is there a bzr tool? I thought it was a tool to help ease working with VCS and debian packages, using the debian/changelog to create a commit message and that sort of thing. it does work with bzr but i havent used it much so....

> Should debian packaging be done in a branch separated from the pristine source?It seems to be the way things are more and more, there was a good and useful reason for this that i heard at one of the Ubuntu Developer week classes on irc but i've totally forgotten what it was! Maybe someone else can remember. Something to do with making it easier to package things for different releases, even distributions, that are using the same source code version, use the same source code, switch in the bzr packaging branch you want and hey presto! something like that i think


Hopefully that vaguely rambling and questionably informed reply helps a little!

---

### Post by MrQuincle on 2010-08-17
Hi SevenMachines! Thanks a lot for your excellent reply!

**Ubuntu in package names**
> Ubuntu syncs from debian, this happens automatically unless there are ubuntu changes ( the -ubuntu1 extensions on versions).I have used dch -i to add an entry to the changelog. It adds then ubuntu to the package name. My changes are probably also good for Debian, so should I correct this behaviour?

**New releases / tarballs**
> ... its much simpler to just update the whole source package to the svn version i'd say. Actually, the creation of new source packages is still kind of a mystery to me. The tool debuild tries to find an (upstream) tarball all the time, as well as its wrapper bzr builddeb. Last time, it didn't even want to make a package without the tarball. Do I have to copy everything to a new directory for a new release, do a dh_make --createorig, and copy the debian/* files from the old release directory?

**Depends**
> i dont know of any build depends tool so if you hear of one let me know! I rolled out my own scripts which does ldd on every binary/library of a built project, extracts the library names, searches through dpkg the package names, and finally returns a unique list. However, in this case it also contains "indirect" dependencies. E.g. libopenscenegraph56 might depend on libpng12-0, but that doesn't say anything about my package, it only depends on libopenscenegraph56, whatever the dependencies of that package might be.

For completeness, a script like that looks something like this (my own script is less concise), from [here]("http://www.mail-archive.com/debian-mentors@lists.debian.org/msg60672.html"):
```

#!/bin/sh

strace -f -o /tmp/log make
# or make instead of ./configure, if the package doesn't use autoconf
for x in `dpkg -S $(grep open /tmp/log|\
    perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
       grep "^/"| sort | uniq|\
       grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
       cut -f1 -d":"| sort | uniq |\
       cut -f1 -d","| sort | uniq`; \
do \
    echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
done

```
I added a cut on the "," separator, but it's still not working entirely properly, because some package names have ":" in their name, so using ":" as a separator for cut is not a wise idea...

**More info**
> i heard at one of the Ubuntu Developer week classes on irc but i've totally forgotten what it was!Perhaps I should visit those one time. I am wondering e.g. how to accelerate the process. I use ccache and cowbuilder, but it still is quite slow. All packages need to be unpacked each time I run cowbuilder. Regarding the fact that I use the build farm on Launchpad, I would be able to use an adapted pbuilder environment with packages preinstalled on my local machine. The Launchpad builders would than run the complete pristine build instead.

---

### Post by SevenMachines on 2010-08-17
**Ubuntu in package names**
see [_Ubuntu Policy on Versioning_]("http://people.canonical.com/%7Ecjwatson/ubuntu-policy/policy.html/ch-controlfields.html#s-f-Version")

basically if the package 'mypackage' has source code version is say, 1.2 then if

* Debian packages the source code, this will be the same if it enters ubuntu with no changes
mypackage-1.2-1 = (package name)-(source version 1.2)-(debian version 1)

* Debian packages the source code, but ubuntu has to make changes :(
mypackage-1.2-1ubuntu1 =  (package name)-(source version 1.2)-(debian version 1)-(ubuntu version 1)

* The package isnt in debian but goes straight into ubuntu
mypackage-1.2-0ubuntu1 =  (package name)-(source version 1.2)-(no debian version)-(ubuntu version 1)

A useful note for PPA's is the ~ extension. for example, if the main repository version is mypackage-1.2-1ubuntu1, then

* Version in my ppa is greater than the repository version and packages will upgrade to it
mypackage-1.2-1ubuntu2~myppaversion1

but then, when mypackage-1.2-1ubuntu2 proper enters the repositories, this version number is actually greater than mine (think of ~ as -1/2!) and the ppa version will upgrade to the main repository version. this can be useful

**New releases / tarballs**
You should look at bzr-buildpackage, and, i think, svn-autoreleasedeb. I think they do things like create an orig.tar.gz for you and things like that. You could of course, 
* get the upstream tarball
* rename it to the orig.tar.gz 
* copy the debian directory into the new source directory
* dch -i, upgrade version
* hope you dont have to make any changes
* debuild

If there is a debian/watch file, you have the easier option of
* in the source directory, 
$ uscan

* this should do all of the above automatically for you

Also, this is probably an example of where having packaging in one bzr branch and sources in another would come into its own, combining the 2 in whatever variation you need. Something i'll need to learn to do! 

**Depends**
This sort of thing is taken care of by debhelper, it really is helpful :)
see, man dh_shlibdeps
>  dh_shlibdeps is a debhelper program that is responsible for calculating
       shared library dependencies for packages.{/QUOTE]

A simple case in action ( it can generate much longer dependency lists )

$ apt-get source hello-debhelper
$ cd hello-debhelper-2.5/
$ cat debian/control
[QUOTE]Package: hello-debhelper
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}Interesting variables, what do they expand to though?

$ debuild -b -us -uc

So lets see what dh_shlibdeps has done for us
$ cat debian/hello-debhelper.substvars 
> misc:Depends=dpkg (>= 1.15.4) | install-info
shlibs:Depends=libc6 (>= 2.3.4)misc:Depends - Things debhelper uses to do its job
shlibs:Depends - Things your binary uses


Note, if your package depends on libX, which itself depends on libY. Then you should only depend on libX not libY as well. The inclusion or not of a further dependency on libY is up to libX and its implementation. However, libX depends on LibY, and your package explicitly requires libX and libY then you should Depend explicitly on both. I don't know how well dh_shlibdeps generates the right dependencies but i've never had it fail me yet.

**More info**
Yes PBuilder/ Cowbuilder are slow. They should cache packages but as you say, unpacking can take a while. Its a neccessity though so that a clean environment is set up every time to test your build. Most of the time you'll only need to run them as a last stage before uploading though to test your dependencies and other bits and bobs.

---

### Post by MrQuincle on 2010-08-17
> **SevenMachines said:**
> Debian packages the source code, but ubuntu has to make changes :(
mypackage-1.2-1ubuntu1 =  (package name)-(source version 1.2)-(debian version 1)-(ubuntu version 1)Cool, though, that means that I shouldn't rely on the actions of dch -i which doesn't know that of course.

There are a lot of tutorials online, but almost no one assumes you are rolling your own code. It always starts with an original tarball. Let I now be one of the weirdos who writes a lot of code... 

**Native**
> You should look at bzr-buildpackageThat's the same package as bzr-builddeb. I have used that indeed and thanks to your comment I started to read at [http://jameswestby.net/bzr/builddeb/user_manual/native.html](http://jameswestby.net/bzr/builddeb/user_manual/native.html). Finally I realise that the term I am looking for is *"native"*. I have to tell bzr-builddeb that it doesn't need an upstream or Debian tarball by telling it that the package is native:
```

mkdir .bzr-builddeb/
echo -e '[BUILDDEB]\nnative = True' > .bzr-builddeb/default.conf
bzr add .bzr-builddeb/default.conf

```

**Release**
And I discovered how to create actually an orig.tar.gz tarball, which is not even created with bzr-builddeb --native. The magic word here is "release". How to release a project is described at [http://doc.bazaar.canonical.com/latest/en/user-guide/releasing_a_project.html](http://doc.bazaar.canonical.com/latest/en/user-guide/releasing_a_project.html) and it's by *bzr export*.

```
bzr tag version0.3
bzr export ../build-area/robot3d_0.3.orig.tar.gz
bzr builddeb -S
sudo cowbuilder --build ../robot3d_0.3.-0ubuntu1.dsc
dput -f ppa:robot3d-team/ppa-robot3d ../robot3d_0.3-0ubuntu1_source.changes
```

It does now have an empty diff file. I don't like that. It should export the orig.tar.gz file without the debian directory, and it should include that directory in the diff. Do I miss something here?

I am definitely gonna look into a separate release branch. I don't like that there is a "debian" directory in my trunk now. I see there is an bzr builddeb --export-upstream option, but I don't think it's what I search for. Perhaps I am gonna make an additional post about how to do that.

Thanks a lot for all the help!! The basic cycle of compiling, pbuilding, uploading, etc. all seems to work now. I now build my own native package (Robot3D), a package that was already on Debian (yarp) and a package that was only available upstream (Delta3D). It was a nice exercise! Now it's time to check out the dpkg-shlibdeps warnings. :-) Thanks again!! =D>

---

