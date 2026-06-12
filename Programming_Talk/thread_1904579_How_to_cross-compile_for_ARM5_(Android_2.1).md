---
title: "How to cross-compile for ARM5 (Android 2.1)"
date: 2012-01-05
forum: Programming Talk
---

### Post by WitchCraft on 2012-01-05
Question:
(Note - originally asked here: [http://askubuntu.com/questions/90400/how-to-cross-compile-for-arm5-android-2-1](http://askubuntu.com/questions/90400/how-to-cross-compile-for-arm5-android-2-1))

So far I have installed gcc-arm-linux-gnueabi and tried this one here:
[http://balau82.wordpress.com/2010/12/05/using-ubuntu-arm-cross-compiler-for-bare-metal-programming/](http://balau82.wordpress.com/2010/12/05/using-ubuntu-arm-cross-compiler-for-bare-metal-programming/)
(changed processor to armv5)

I have also seen this tutorial
[http://android-dls.com/wiki/index.php?title=Compiling_for_Android](http://android-dls.com/wiki/index.php?title=Compiling_for_Android)
But emdebian-tools is not present in the repositories of ubuntu (11.10).


Anybody knows how I can simply cross-compile for Android on Ubuntu 11.10 (x64) ?

All I want is to cross-compile a (not so) simple C application with some calls to stdlib functions.

I can find tutorials on emdebian and Linario, but Linario doesn't work on Ubuntu 11.10, and emdebian is not present.

Heavens, all I want is a simple cross-compilation environment, where I can cross-compile C programs with some calls to libC/bionic.

Via Google, I find all sort of crap, including the download of 230 MB dependencies (and afterwards no description on how to cross-compile) or "how to build a embedded linux distro from scratch".

This is all very nice, but I don't have the time. Anybody knows something nice ?

---

### Post by shadylookin on 2012-01-06
Well if you want to write an app(apk) for android then download the android native development kit(ndk)it comes with a sample project to get you started. 

If you've got a rooted phone and you're trying to put a pure c/c++ application on there then the native development kit is probably still your best option, but I don't know anything about it.

---

