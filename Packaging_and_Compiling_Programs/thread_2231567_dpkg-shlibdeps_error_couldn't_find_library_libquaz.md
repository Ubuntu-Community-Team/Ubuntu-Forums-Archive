---
title: "dpkg-shlibdeps: error: couldn't find library libquazip.so.1"
date: 2014-06-26
forum: Packaging and Compiling Programs
---

### Post by Manoj_Patidar on 2014-06-26
[COLOR=#000000][FONT=Arial]I am getting the below error during making the .deb package of the QT 5.2.1 app .
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]dpkg-shlibdeps: error: couldn't find library libquazip.so.1 needed by debian/demoapp/usr/bin/DemoApp1 (ELF format: 'elf64-x86-64'; RPATH: '') dpkg-shlibdeps: warning: package could avoid a useless dependency if debian/demoapp/usr/bin/DemoApp1 was not linked against libz.so.1 (it uses none of the library's symbols) dpkg-shlibdeps: error: cannot continue due to the error above Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file. To help dpkg-shlibdeps find private libraries, you might need to use -l. dh_shlibdeps: dpkg-shlibdeps -Tdebian/demoapp.substvars debian/demoapp/usr/bin/DemoApp1 returned exit code 2 make: *** [binary-predeb-IMPL/demoapp] Error 2 dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2 debuild: fatal error at line 1364: dpkg-buildpackage -rfakeroot -D -us -uc failed
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]After done a lot R&D I found that (If I am not wrong) that dynamic linker can not search the libquazip.so.1 into the machine.

Because it searches by default in path /lib the usr/lib and I deleted libquazip.so from these paths ( at which I installed by mannually before).So I think the solution is that I need to link this third party shared library by using -rpath and $ORIGIN .

But I do not know how exactly I can link libquazip.so.1 third party shared library to the **-rpath by using $ORIGIN** variable.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I have go through the below links for the same but could not get the succees.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][ld: Using -rpath,$ORIGIN inside a shared library (recursive)]("http://stackoverflow.com/questions/6323603/ld-using-rpath-origin-inside-a-shared-library-recursive")[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][Building a simple (hello-world-esque) example of using ld's option -rpath with $ORIGIN]("http://stackoverflow.com/questions/6311016/building-a-simple-hello-world-esque-example-of-using-lds-option-rpath-with")[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][http://serverfault.com/questions/279068/cant-find-so-in-the-same-directory-as-the-executable](http://serverfault.com/questions/279068/cant-find-so-in-the-same-directory-as-the-executable)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][http://doc.qt.digia.com/qq/qq11-unix-deployment.html](http://doc.qt.digia.com/qq/qq11-unix-deployment.html)
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Please have look into the issue and suggest me what should I do to resolve the issue ?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks,[/FONT][/COLOR]

---

