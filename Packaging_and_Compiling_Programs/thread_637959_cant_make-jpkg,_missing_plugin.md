---
title: "cant make-jpkg, missing plugin"
date: 2007-12-11
forum: Packaging and Compiling Programs
---

### Post by cuco2772 on 2007-12-11
I have java version "1.5.0_11", I cant compile servlets so I installed
this one, the SDK with JDK : java_ee_sdk-5_03-linux.bin, in /opt/SDK/jdk
Problem is, if I do javac, it only finds the 1.5 version, so I cant compile servlets. I've reset $JAVA_HOME to /opt/SDK/jdk, doesnt help.

I tried doing this from a java package, using fakeroot, here's what 
happened:

cuco@coat:~/Desktop$ fakeroot make-jpkg java_ee_sdk-5_03-linux.bin
Creating temporary directory: /tmp/make-jpkg.WOrlLt6874
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done

---

