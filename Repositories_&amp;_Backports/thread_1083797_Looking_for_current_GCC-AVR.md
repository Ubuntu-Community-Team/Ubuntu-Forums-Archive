---
title: "Looking for current GCC-AVR"
date: 2009-03-01
forum: Repositories &amp; Backports
---

### Post by allan.w.macdonald on 2009-03-01
Hello all,

I have a Dell 1525 Inspiron, pre-installed with Ubuntu 8.04 (Hardy).

I recently installed the AVR-GCC package that is available from the site:

us.archive.ubuntu.com/universe

My problem is that the version found there, 4.2.2, does not appear to support the target I want to build for: ATtiny88.

I think this is because avr-libc is V1.4 but 1.6 is released and ATtiny88 is only supported in avr-libc 1.6 and later.

Can I expect the Ubuntu software source repositories to be updated with the latest releases of avr-gcc, avr-libc, and any other related packages or must I go to the trouble of installing the latest releases directly from the avr-libc project myself?

Please help.

Best to all,

Allan

---

### Post by WW on 2009-03-01
The most recent version of Ubuntu ("Intrepid...") has version 1.6 of [avr-libc](http://packages.ubuntu.com/intrepid/avr-libc).

In general, a released version of Ubuntu is not updated with newer libraries or programs. Usually updates are limited to security updates. However, take a  look at [Ubuntu Backports](https://help.ubuntu.com/community/UbuntuBackports).

---

### Post by allan.w.macdonald on 2009-03-02
Thanks for the reply, WW.

I thought as much.  I guess I should start to get ready to wade into the icy cold waters of building a toolchain for the first time (I feel myself shrivelling up already!)

So, my next question is, if I already have a pre-compiled binary distribution installed, and I want to instead install the latest source tarball (or CVS checkout, or whatever), should I uninstall the old stuff first or can I just install the new stuff "on top of" the old stuff?

What is the usual practice?

Thanks again

Cheers,

Allan

---

### Post by allan.w.macdonald on 2009-03-02
More questions for WW:

After reading your reply the first time, I looked at the hardy backports page and did a search for the package in question and didn't find it.  However, I decided to give it a second look and realized that I could actually request a backport - so, I did.  I guess I should have read the entire page more carefully.

[https://bugs.launchpad.net/hardy-backports/+bug/337067](https://bugs.launchpad.net/hardy-backports/+bug/337067)

Not sure if it'll work but lets hope.

Also, after reading your post again, I noticed that your post includes a link to the avr-libc for Intrepid page.  Does that mean that I can or should download it from there?  Is that a good idea?  Will it work on my Hardy system?  The download page recommends that I use Aptitude or Synaptic to download and install.  How do I configure my Synaptic Package Manager to get this version of avr-libc instead of the version that shows up for Hardy?  (I guess this will all be moot if the backport request works).

When should I just go the traditional way and build the tarball?

Sorry if I sound kinda dumb - I'm learning as I go.

Cheers,

Allan

---

### Post by WW on 2009-03-03
> **allan.w.macdonald said:**
> More questions for WW:

After reading your reply the first time, I looked at the hardy backports page and did a search for the package in question and didn't find it.  However, I decided to give it a second look and realized that I could actually request a backport - so, I did.  I guess I should have read the entire page more carefully.

[https://bugs.launchpad.net/hardy-backports/+bug/337067](https://bugs.launchpad.net/hardy-backports/+bug/337067)

Not sure if it'll work but lets hope.

It's worth a shot!
> **allan.w.macdonald said:**
> 
Also, after reading your post again, I noticed that your post includes a link to the avr-libc for Intrepid page.  Does that mean that I can or should download it from there?  Is that a good idea?  Will it work on my Hardy system?  

Unfortunately, no, it is usually not a good idea to mix repositories.

In the case of avr-libc, it looks like there are no further dependencies, so that particular package might be safe, but you'll probably want the whole suite of avr tools.  If you attempt to install all of them, you may find that it requires replacing some additional libraries or packages that are dependencies of the avr suite, and the new libraries might not be compatible with other packages in Hardy, so those will have to be removed or updated, which could trigger another set of dependencies being updated, and so on.  In the end, it would be safer to just upgrade to Intrepid.

> **allan.w.macdonald said:**
> 
When should I just go the traditional way and build the tarball?

I don't have a definite answer to that.

You could try grabbing the Intrepid source code packages for the avr suite for building your version.  This means you might end up doing the backport yourself.  Some folks here could probably help you with that.

Good luck!

WW

---

### Post by allan.w.macdonald on 2009-03-04
Hi WW,

If I actually have go to the extent of compiling source code, I might as well just get whatever stuff directly from the AVR toolchain project:

[http://www.nongnu.org/avr-libc/](http://www.nongnu.org/avr-libc/)

Thanks for all of your thoughts and guidance, WW.

If and when I attempt this, I'll post my results here.

Cheers,

Allan

---

### Post by allan.w.macdonald on 2009-03-24
Here are the results of my attempt to build from scratch:  I got hold of the avr-libc-1.6.4 user manual, read section 12 and started digging in.  I choose the option of setting my PREFIX to $HOME/local/avr instead of /usr/local/avr.  Hey... the manual mentions some patches I might need... I'll put off applying those for the moment (Patches?  What patches?).

So, after a bit of effort, farting around and stumbling in the dark, I was finally able to get binutils-2.19, gcc-4.3.3 (with mpfr-2.4.1 and gmp-4.2.4 placed in the source tree) and avr-libc-1.6.4 to build. However, the  build of avrdude-5.6 craps out.  Still, undaunted, I try to use the parts of the toolchain that did successfully build to try to compile my tiny88 project, and what do I discover? That I still don't get any support for the ATtiny88!  Aaargh.

After repeatedly striking my forehead upon a hard surface, I began to realize my problem might be that maybe I needed to apply those patches to binutils and gcc after all.

[http://www.freebsd.org/cgi/cvsweb.cgi/ports/devel/avr-binutils/files/patch-newdevices](http://www.freebsd.org/cgi/cvsweb.cgi/ports/devel/avr-binutils/files/patch-newdevices)
[http://www.freebsd.org/cgi/cvsweb.cgi/ports/devel/avr-gcc/files/patch-newdevices](http://www.freebsd.org/cgi/cvsweb.cgi/ports/devel/avr-gcc/files/patch-newdevices)

Now, I must admit that I am a complete newbie when it comes to applying source-level patches (or even fully understanding them, for that matter) which explains my reluctance to try in the first place.  Nevertheless, taking a deep breath, I go for it and download the latest patches.

However, when I read the cvs log entry for avr-binutils patch-newdevices (rev 1.12), I find the remark "Update to binutils-2.18".  Hmm, does this mean that this patch is supposed to be applied to binutils-2.18?  Thinking the answer is "yes", I instead download binutils-2.18, apply the patch and try to build that.  I also download gcc-4.2.2 since the latest GCC patch-newdevices seems to point to that release.

Now, when I try to build, I can't even get past binutils because I get the error:

WARNING: `makeinfo' is missing on your system.  You should only need it if
         you modified a `.texi' or `.texinfo' file, or any other file
         indirectly affecting the aspect of the manual.  The spurious
         call might also be the consequence of using a buggy `make' (AIX,
         DU, IRIX).  You might want to install the `Texinfo' package or
         the `GNU make' package.  Grab either from any GNU archive site.
make[3]: *** [bfd.info] Error 1

WTF?

So, I try to look around to see what this is about and find various references to this problem.  I find the following bug which references a patch that is supposed to fix it:

Bug:
[http://sourceware.org/bugzilla/show_bug.cgi?id=5021](http://sourceware.org/bugzilla/show_bug.cgi?id=5021)

Patch:
[http://gcc.gnu.org/ml/gcc-patches/2007-09/msg01271.html](http://gcc.gnu.org/ml/gcc-patches/2007-09/msg01271.html)

Unfortunately, applying the patch to my binutils-2.18 doesn't work.  The lines in the diff don't even match the actual lines that are in the binutils-2.18 configure.ac script file.  The diff says that the changed files start at line 2454 but in the configure.ac in 2.18 these lines start at 2403.  I don't understand... is there another "2.18" to which this diff is referring?

Anyway, I change the diff to fix the line numbers so they match the sources I have and apply the patch and still I get the error.  Now what?

So, I go hunting around some more.  More Googling yields another bug report:

[https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/226037](https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/226037)

Now, this is appears to be the same problem I'm having.  However, the bug report says the problem's fixed and provides a link to what appears to be a patch of patches:

Also, the file version name seems different from the release I wanted to use, which is binutils_2.18.1~cvs20080103-0ubuntu1.  What is this?  What do I apply this patch of patches to?  Do I apply it to binutils_2.18.1~cvs20080103.orig?  Will this version be compatible with the patch-newdevices?

[http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.18.1~cvs20080103-0ubuntu1.diff.gz](http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.18.1~cvs20080103-0ubuntu1.diff.gz)

Also, the directory containing this patch also contains a bunch of .deb files.  I'm not quite sure what a .deb file is but I doubt it has anything to do with anyone named Debbie (dang it!).  Are these precompiled binaries or source distributions?  If they are sources, and if I install them, will they end up where I want them? 

I am starting to get a little discouraged ... I've been bumbling at this, off an on, for a couple of weeks now and haven't made any headway.  Maybe I'm a bit retarded or something but, really, doesn't this stuff seems kinda hard?

Any help/guidance would be greatly appreciated.  Does anybody have a script or description of a successful build of the entire toolchain that I could study (i.e. copy)?

All comments welcome!

Best to all,
Allan

---

### Post by allan.w.macdonald on 2011-03-12
Long since solved.

---

