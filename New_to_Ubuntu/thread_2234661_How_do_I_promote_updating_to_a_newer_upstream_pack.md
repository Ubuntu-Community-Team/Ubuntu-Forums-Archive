---
title: "How do I promote updating to a newer upstream package?"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by ammon2 on 2014-07-16
How do I find information on software packages availible in Ubuntu other than in the software center itself?
How can I know what the latest integrated version of an upstream package is?
does it depend on which Ubuntu release I am using?
How do I contact a package maintainer?
Is there any way I can promote the updating to a newer version of an an upstream package?
can I do it myself?
where would I start?
Is it difficult?
what skills would be involved?

Specifically: Blender.
the version availible in the software center for Ubuntu 12.10 is 2.63 released in 2012.APR
    [URL="http://www.blender.org/features/past-releases/"]http://www.blender.org/features/past-releases/
[/URL]The latest version is 2.71
There have been changes to the user interface (hotkeys) and some of the tools since at least 2.66. I don't know what else, but it is making it challanging to follow their video tutorials as they are using features that don't exist in my version.

I found this, but it wasn't very helpful:
[https://help.ubuntu.com/community/Blender](https://help.ubuntu.com/community/Blender)

---

### Post by deadflowr on 2014-07-16
First off, 12.10 has reached end of life, so not a good release to try out.

Second, in terms of running updated software, ppa's are the best solution.
([This is old, but still the basics are relevant]("http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them"))

From there you can either do a quick search, via your favorite search engine, or sites like launchpad.net.
Some software makers, like oracle and google, provide ppa's of their own.

But basically, for anyone new, if the version in the default repos is not the one you want, or you would like a newer version, ppa's are the best first option.
After that installing from source, but of course, that's not something someone new would want to do, unless it's the type of stuff they would want to do.
IMHO

---

### Post by bapoumba on 2014-07-16
It quite really depends.
You can check this ppa for Blender, and see if it fits your needs : [https://launchpad.net/~irie/+archive/ubuntu/blender](https://launchpad.net/~irie/+archive/ubuntu/blender)

ppa : 
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu), this part : [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)
When adding and using a ppa on your system, please remember to instal ppa-purge in the process, should you wish to revert packages back to their original ubuntu version.

Ubuntu packages :
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_PPAs)
You will find there most of the info, release, version, maintainer etc.

To promote a specific package version upgrade, please first check with debian as ubuntu releases are based on unstable every 6 months. If it is available on debian, could be pushed in ubuntu, depending on the release distribution, dependencies (libs or other central things as kernel, gcc etc.). You'd need to raise a bug for that, provided we are talking about regular packages ubuntu ships : [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
For other packages, as I said earlier, it really depends and is a case by case situation.

Edit : that is not even ninja'd by deadflowr, call me the slowest of the slow :D

---

### Post by grahammechanical on 2014-07-16
Ubuntu 14.04 has Blender 2.69, which came out on 31st October 2013. So it could not be included in the software centre of Ubuntu 13.10. It had to wait until the release of 14.04.
 
Basically speaking the 6 months release cycle of Ubuntu makes it possible for newer stable versions of software to be included in the software centre. If you are serious about becoming a maintainer, then your involvement will be welcome.

[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

Imagine that it is your responsibility to make sure that the version of Blender in the software centre does not ruin someone's user experience. With that responsibility in mind which version of Blender would you recommend for inclusion in the software centre? It makes us think, does it not?

Regards.

---

### Post by ian-weisser on 2014-07-16
> **ammon2 said:**
> How do I find information on software packages availible in Ubuntu other than in the software center itself?
How can I know what the latest integrated version of an upstream package is?
does it depend on which Ubuntu release I am using?
How do I contact a package maintainer?
Is there any way I can promote the updating to a newer version of an an upstream package?
can I do it myself?
where would I start?
Is it difficult?
what skills would be involved?

The *apt-cache* command is a good start.
It tells you version, maintainer, dependency, upstream, and much more information.

```
$ apt-cache show blender   
Package: blender
Priority: optional
Section: universe/graphics
Installed-Size: 59572
[COLOR=#ff0000]Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>[/COLOR]
Architecture: i386
[COLOR=#ff0000]Version: 2.69-4ubuntu2[/COLOR]
Depends: blender-data (= 2.69-4ubuntu2), fonts-droid, libjs-jquery, libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavdevice53 (>= 6:9.1-1), libavformat54 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libboost-filesystem1.54.0, libboost-locale1.54.0, libboost-system1.54.0, libboost-thread1.54.0, libc6 (>= 2.15), libfftw3-double3, libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglew1.10 (>= 1.10.0), libglu1-mesa | libglu1, libgomp1 (>= 4.2.1), libilmbase6 (>= 1.0.1), libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libjpeg8 (>= 8c), libopenal1 (>= 1:1.13), libopenexr6 (>= 1.6.1), libopenimageio1.3, libopenjpeg2, libpng12-0 (>= 1.2.13-4), libpython3.4 (>= 3.4~b1), libsdl1.2debian (>= 1.2.11), libsndfile1 (>= 1.0.20), libspnav0 (>= 0.2.1), libstdc++6 (>= 4.6), libswscale2 (>= 6:9.1-1), libtiff5 (>= 4.0.3), libx11-6, libxi6, libxxf86vm1, zlib1g (>= 1:1.2.3.4)
Suggests: libtiff4, yafaray-exporter
Breaks: yafaray-exporter (<< 0.1.2+really0.1.2~beta5-1)
Filename: pool/universe/b/blender/blender_2.69-4ubuntu2_i386.deb
Size: 18204496
MD5sum: 6242e7ef00207cd9be0fd694a91afb93
SHA1: 5ad01b4019571b09bd925ce7fccea65d83ec8176
SHA256: aae6417d42fa3f058879c0987d6d972af0a5d830ce444da21da222906efbfccb
Description-en: Very fast and versatile 3D modeller/renderer
 Blender is an integrated 3d suite for modelling, animation, rendering,
 post-production, interactive creation and playback (games). Blender has its
 own particular user interface, which is implemented entirely in OpenGL and
 designed with speed in mind. Python bindings are available for scripting;
 import/export features for popular file formats like 3D Studio and Wavefront
 Obj are implemented as scripts by the community. Stills, animations, models
 for games or other third party engines and interactive content in the form of
 a standalone binary are common products of Blender use.
Description-md5: 90b4f36fda45432800e6a278de5b06b4
[COLOR=#ff0000]Homepage: http://www.blender.org/[/COLOR]
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: ubuntustudio-video, ubuntustudio-graphics
```

The other way to check Debian archives and Ubuntu repositories is to use the *rmadison* command, included in the *devscripts* package
```
$ rmadison -u debian blender
 blender | 2.49.2~dfsg-2    | squeeze | source
 blender | 2.49.2~dfsg-2+b2 | squeeze | amd64, armel, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, sparc
 blender | 2.63a-1          | wheezy  | source, amd64, armel, armhf, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, s390x, sparc
 blender | 2.70a-2          | jessie  | source
 blender | 2.70a-2          | sid     | source, sparc
 blender | 2.70a-2+b2       | jessie  | amd64, armel, armhf, i386, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390x
 blender | 2.70a-2+b2       | sid     | amd64, armel, armhf, hurd-i386, i386, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390x

$ rmadison -u ubuntu blender
 blender | 2.49.2~dfsg-1ubuntu1 | lucid/universe           | source, amd64, armel, i386, ia64, powerpc, sparc
 blender | 2.62-1               | precise/universe         | source, amd64, armel, armhf, i386, powerpc
 blender | 2.66a-3ubuntu2       | saucy/universe           | source, amd64, armhf, i386, powerpc
 blender | 2.69-4ubuntu2        | trusty/universe          | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 blender | 2.69-4ubuntu3        | utopic/universe          | source, amd64, arm64, armhf, i386, powerpc, ppc64el
 blender | 2.70a-2ubuntu2       | utopic-proposed/universe | source, amd64, arm64, armhf, i386, powerpc, ppc64el
```

To see if a new version of any package is available, first check upstream.

Then look at the path that software takes. For the Blender example, an automated tool notifies the Debian maintainer when a new version is available. Then, as time permits, the Debian maintainer packages, tests, and uploads to Debian (see [https://packages.qa.debian.org/b/blender.html](https://packages.qa.debian.org/b/blender.html) for status), then Ubuntu syncs from Debian as it prepares the next release.

The testing and upload time, and the Ubuntu development time, can be considerable. 

Does this mean that software that releases new version frequently will be a version or two behind in Ubuntu? Yes.

Could the upstream release, Debian import, Ubuntu sync, and update backports be more closely coordinated? Perhaps.

---

### Post by bapoumba on 2014-07-16
Thanks ian-weisser, I had forgotten about rmadison :)

---

### Post by ammon2 on 2014-07-18
So, what you are telling me is that I should just update to a newer release. I'm ok with that. But how am I supposed to know it? Is there a pop-up when a release reaches end of life? Is there a page that lists each release and its time frame?

Found it: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
So this shows each release and its life expectancy.

---

### Post by cariboo on 2014-07-18
Removed double post.

---

### Post by ian-weisser on 2014-07-19
> **ammon2 said:**
> But how am I supposed to know it?

Your Software Sources or Software & Updates control panel is accessable from Software Center, Synaptic, System Settings, or the **software-properties-gtk** command.

It has an 'Updates' tab, and one option is that tab is to notify you if a new release is available.

New releases of Ubuntu are also readily predictable using any old paper calendar. April and October.

> **ammon2 said:**
> Is there a pop-up when a release reaches end of life?

Pop-up? No. But your regular updates will start erroring as the repositories they draw from no longer exist.

> **ammon2 said:**
> Is there a page that lists each release and its time frame?

Found it: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
So this shows each release and its life expectancy.

The official list is at [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

