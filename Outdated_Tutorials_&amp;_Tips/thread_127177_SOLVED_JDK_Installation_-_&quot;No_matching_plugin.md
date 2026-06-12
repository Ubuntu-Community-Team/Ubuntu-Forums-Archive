---
title: "SOLVED: JDK Installation - &quot;No matching plugin was found.&quot;"
date: 2006-02-08
forum: Outdated Tutorials &amp; Tips
---

### Post by rkakkar on 2006-02-08
The file I had downloaded was called:
jdk-1_5_0_05-linux-i586-rpm.bin

Problem:

$ DEB_BUILD_GNU_TYPE=i386-linux fakeroot make-jpkg jdk-1_5_0_05-linux-i586-rpm.bin
Creating temporary directory: /tmp/make-jpkg.XXXXyPf7WT
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done


Solution:

remove the rpm from the filename:

$ mv jdk-1_5_0_05-linux-i586-rpm.bin jdk-1_5_0_05-linux-i586.bin

then try,

$ fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin

It should work.

\\:D/

---

