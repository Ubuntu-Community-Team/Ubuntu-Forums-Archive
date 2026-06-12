---
title: "Can't detect emulator after locating Android SDK on Eclipse IDE"
date: 2014-09-04
forum: Programming Talk
---

### Post by Ashfaqur Rahman on 2014-09-04
After installing SDK, API and configuring AVD, I was trying to locate the SDK for Eclipse IDE which is located on /opt/android-sdk-linux. its showing this error " Could not find /opt/android-sdk-linux/tools/emulator! ". But /opt/android-sdk-linux/tools/emulator does exist. I am on Ubuntu 14.04 64bit OS. But **/opt/android-sdk-linux/tools/emulator** is a 32 bit Executable. I think this is the cause of that error. My problem is similar to this problem - [http://askubuntu.com/questions/143319/starting-android-avd-fails-saying-it-cant-find-emulator-but-it-exists](http://askubuntu.com/questions/143319/starting-android-avd-fails-saying-it-cant-find-emulator-but-it-exists)

2nd answer suggests that there are many emulator versions available in the **/opt/android-sdk-linux/tools **folder. True, I can see emulator64-arm, emulator64-mips, emulator64-x86. I think these are suitable for 64bit OS. Now my question is which should I choose from these three and how can I set that manually on Eclipse IDE. I can't see any option for that on preference menu.

Thanks

---

### Post by Ashfaqur Rahman on 2014-09-04
Found my solution here - [http://stackoverflow.com/questions/17474401/cannot-run-program-xx-sdk-tools-emulator-java-io-ioexception-error-2-no-s](http://stackoverflow.com/questions/17474401/cannot-run-program-xx-sdk-tools-emulator-java-io-ioexception-error-2-no-s)
Also there was permission issue. /opt/android-sdk-linux/tools folder was under root permission. I changed the permission recursively
> sudo chmod 777 -R /opt/android-sdk-linux

---

