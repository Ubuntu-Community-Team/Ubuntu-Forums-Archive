---
title: "Error compiling Unity"
date: 2019-01-16
forum: Packaging and Compiling Programs
---

### Post by fetus on 2019-01-16
I'm attempting to disable built-in multi-touch gestures in Unity in Ubuntu 16. Apparently, this requires editing Unity source code. I came across this post explaining how: [https://askubuntu.com/a/205045/683695](https://askubuntu.com/a/205045/683695) 

I getting an error compiling Unity with **dpkg-buildpackage -us -uc -nc**


```
Scanning dependencies of target run-test-switcher-controller-slow-headless
make[5]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
make -f tests/CMakeFiles/run-test-switcher-controller-slow-headless.dir/build.make tests/CMakeFiles/run-test-switcher-controller-slow-headless.dir/build
make[5]: Entering directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
cd /tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu/tests && env NUX_FALLBACK_TEXTURE=TRUE /tmp/unity/unity-7.4.5+16.04.20180221/tests/dummy-xorg-test-runner.sh /usr/bin/dbus-run-session ./test-switcher-controller-slow --gtest_output=xml:/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu/tests/test-switcher-controller-slow-headless.xml
The X server was not able to run in time
tests/CMakeFiles/run-test-switcher-controller-slow-headless.dir/build.make:60: recipe for target 'tests/CMakeFiles/run-test-switcher-controller-slow-headless' failed
make[5]: *** [tests/CMakeFiles/run-test-switcher-controller-slow-headless] Error 1
make[5]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
CMakeFiles/Makefile2:20125: recipe for target 'tests/CMakeFiles/run-test-switcher-controller-slow-headless.dir/all' failed
make[4]: *** [tests/CMakeFiles/run-test-switcher-controller-slow-headless.dir/all] Error 2
make[4]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
CMakeFiles/Makefile2:24011: recipe for target 'tests/CMakeFiles/check-headless.dir/rule' failed
make[3]: *** [tests/CMakeFiles/check-headless.dir/rule] Error 2
make[3]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
Makefile:7848: recipe for target 'check-headless' failed
make[2]: *** [check-headless] Error 2
make[2]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221/obj-x86_64-linux-gnu'
debian/rules:58: recipe for target 'override_dh_auto_test' failed
make[1]: *** [override_dh_auto_test] Error 2
make[1]: Leaving directory '/tmp/unity/unity-7.4.5+16.04.20180221'
debian/rules:63: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

---

### Post by fetus on 2019-01-16
I realized the error was occuring during unit test phase. So I compiled without unit tests and succeeded:

[FONT=Courier New]DEB_BUILD_OPTIONS=nocheck dpkg-buildpackage -us -uc -nc[/FONT]

---

