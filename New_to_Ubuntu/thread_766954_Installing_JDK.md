---
title: "Installing JDK"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by rs_zero_one on 2008-04-25
After 4 hours I am finally able to make a dual boot linux/xp machine. But I hit another snag with linux.

I tried installing the JDK but im getting different errors. when using:
  sudo ./java_app_platform_sdk-5_04-linux.bin
i get this error:
  sudo: unable to execute ./java_app_platform_sdk-5_04-linux.bin: No such 
  file or directory

and i found this via google:
  sudo aptitude install jdk-1_5_0_07-linux-i586.bin
but it gave me a different error:
  Couldn't find any package whose name or description matched "jdk-1_5_0_07-
  linux-i586.bin"

can somebody point out what im doing wrong? i also tried bash <file> sh <file> and still no progress.

your help will be greatly appreciated.

i am using the 64 bit version of ubuntu btw.

---

### Post by SOULRiDER on 2008-04-25
Just install it from the repos, opena  terminal and type
```
sudo aptitude install sun-java6-jdk
```
Check this link out, its important that you read it:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

