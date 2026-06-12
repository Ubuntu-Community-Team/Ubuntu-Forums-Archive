---
title: "Stuck in App Store Deployment: &quot;dpkg-shlibdeps -l option&quot; fails at canonical"
date: 2015-02-09
forum: Packaging and Compiling Programs
---

### Post by Y_Ernst on 2015-02-09
Sorry If I sound a little frustrated but I'm already waiting for over 4 month for an app-store review of my game and it just won't happen:

The last response I got was that my application could not be build from source (debsrc package) because the execution of dh_shlibdeps failed:

dh_shlibdeps --dpkg-shlibdeps-params="--ignore-missing-info -ldebian/memorytheminorplanets/opt/memorytheminorplanets"
dpkg-shlibdeps: unknown option `-ldebian/memorytheminorplanets/opt/memorytheminorplanets'

which I think is funny because this option is described in the manual:
```
yousry@Blasphemy:~/Documents/deploy/Feb15/memorytheminorplanets-1.1$ man dpkg-shlibdeps


Options:
...
-ldirectory
Add directory to the list of directories to search for private shared libraries (since dpkg 1.17.0). This option can be used multiple times.
...

```

and it is also working for me:

```
yousry@Blasphemy:~/Documents/deploy/Feb15/memorytheminorplanets-1.1$ dh_shlibdeps --dpkg-shlibdeps-params="--ignore-missing-info -ldebian/memorytheminorplanets/opt/memorytheminorplanets"
dpkg-shlibdeps: warning: debian/memorytheminorplanets/opt/memorytheminorplanets/libobjcxx.so.4.6 contains an unresolvable reference to symbol object_getClass: it's probably a plugin
dpkg-shlibdeps: warning: 2 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 contains an unresolvable reference to symbol SSL_CTX_load_verify_locations: it's probably a plugin
dpkg-shlibdeps: warning: 150 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets contains an unresolvable reference to symbol BIO_push: it's probably a plugin
dpkg-shlibdeps: warning: 14 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 contains an unresolvable reference to symbol EVP_des_ede3_cbc: it's probably a plugin
dpkg-shlibdeps: warning: 62 other similar warnings have been skipped (use -v to see them all)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 were not linked against libcrypto.so.1.0.0 (they use none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 was not linked against libkrb5.so.3 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 was not linked against libk5crypto.so.3 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets was not linked against libIexMath-2_1.so.11 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets was not linked against libmsgpack.so.4 (it uses none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 debian/memorytheminorplanets/opt/memorytheminorplanets/libssh2.so.1 were not linked against libssl.so.1.0.0 (they use none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libIlmImf-Imf_2_1.so.21 debian/memorytheminorplanets/opt/memorytheminorplanets/memoryTheMinorPlanets were not linked against libImath-2_1.so.11 (they use none of the library's symbols)
dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/memorytheminorplanets/opt/memorytheminorplanets/libcurl.so.4 was not linked against libcom_err.so.2 (it uses none of the library's symbols)

```
I'im using utopic as build system:  

```
yousry@Blasphemy:~/Documents/deploy/Feb15/memorytheminorplanets-1.1$ uname -a
Linux Blasphemy 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

I also checked the resulting deb on the same system:

[http://virtualhorde.com/BIN/memorytheminorplanets_1.1ubuntu1_amd64.deb]("http://virtualhorde.com/BIN/memorytheminorplanets_1.1ubuntu1_amd64.deb")

So what could be the difference between my and the reviewers system?

---

### Post by ian-weisser on 2015-02-09
You submitted a deb package or click package?

---

### Post by Y_Ernst on 2015-02-09
> **ian-weisser said:**
> You submitted a deb package or click package?

I submitted a dev-src package: (**memorytheminorplanets-1.1-debsrc.tar.gz**) for Ubuntu desktop (64 Bit).

I followed the instructions from here: [https://developer.ubuntu.com/en/publish/other-forms-of-submitting-apps/my-apps-packages/]("https://developer.ubuntu.com/en/publish/other-forms-of-submitting-apps/my-apps-packages/")

A deb package can then be build with: **dpkg-buildpackage -rfakeroot -uc -b**

---

### Post by ian-weisser on 2015-02-09
Good place to start is irc.freenode.net #ubuntu-devel
Ubuntu developers experienced with upload reviews and packaging lurk there.
If the right people aren't already there, they will be able to refer you to the right person.

Most of the ones I know are in Europe, so be aware of any time difference.
Do be patient, many are volunteers.

> **Y_Ernst said:**
> I submitted a dev-src package: (**memorytheminorplanets-1.1-debsrc.tar.gz**) for Ubuntu desktop (64 Bit).
I followed the instructions from here: [https://developer.ubuntu.com/en/publish/other-forms-of-submitting-apps/my-apps-packages/](https://developer.ubuntu.com/en/publish/other-forms-of-submitting-apps/my-apps-packages/)

...and you haven't heard any status on the submission. Yes, that's pretty much all you should need to say.

---

### Post by mc4man on 2015-02-09
Does/did the source build in your ppa?

---

### Post by Y_Ernst on 2015-02-11
As Ian-weisser suggested, I tried to contact someone from canonical at #ubuntu-devel. 
[I]There it was confirmed that the script "dpkg-shlibdeps" has the -l option and it should not be used at all, because internal libraries must not be referenced as shared-libraries and system libs could be found via the system path. 
[/I](Bad memory quotation)

This contradicts my understanding that this output hints at a bug:
```
dh_shlibdeps --dpkg-shlibdeps-params="--ignore-missing-info -ldebian/memorytheminorplanets/opt/memorytheminorplanets"
dpkg-shlibdeps: unknown option `-ldebian/memorytheminorplanets/opt/memorytheminorplanets'

```

To avoid further time-wasting on this topic I removed **dpkg-shlibdeps** from the build-script. The consequences are, that it is not possible to prevent erroneous referencing to outdated or bad-configured/compiled libraries. It was also necessary to remove any library containing subdirectories.       

Let us wait another month for the next app-store feedback ](*,)

---

### Post by Y_Ernst on 2015-02-13
Removing **dpkg-shlibdepsm** didn't work either. With this, the build process fails because of missing libraries during the dh-shlibdeps step.
(To avoid this problem the library path had to be altered before the build)

I really hoped that a test with pbuilder would give comparable results, but if a build works an my system and not on a test-system a **reliable reference** is unavailable and the developer is lost.

I now uploaded a new version that was partially compiled on utopic and added an environment variable to the debian-rules (as -l replacement).  
If I would further see problems with the executable I would switch to rpath / static linking. But this is not the case.

---

### Post by Y_Ernst on 2015-02-25
Perhaps someone could help me and test the source-code package at: [http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu4-debsrc.tar.gz]("http://virtualhorde.com/BIN/memorytheminorplanets-1.1ubuntu4-debsrc.tar.gz") (Binary:  [http://virtualhorde.com/BIN/memorytheminorplanets_1.1ubuntu1_amd64.deb]("http://virtualhorde.com/BIN/memorytheminorplanets_1.1ubuntu1_amd64.deb")) I have testet the package again against ubuntu (utuopic) and with pbuilder.

With sh512sum you should check the identity:
4704a77e6de53e2ee962dc3e6bddc2235e43f1a41ff8a38c92473e6fdcb4079d86e2401a739fa9ca15f66697c3d63d3ff74680de18c104006006cfeff86d145b  memorytheminorplanets-1.1ubuntu4-debsrc.tar.gz

I have applications on almost any major app-store (inclusive  ubuntu-store) and I'm more or less disappointed about the progress of this app-review.   

It is a completely harmless little game ([http://youtu.be/qPMS1BZ0Av4]("http://youtu.be/qPMS1BZ0Av4")) and I could not send it to steam because of the missing windows binary (My windows partition with vstudio didn't boot anymore).

---

### Post by Y_Ernst on 2015-03-06
I will close this question. I removed the buggy -l option in my rules script.

---

