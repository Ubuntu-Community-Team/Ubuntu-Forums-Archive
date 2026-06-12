---
title: "Issues with creating Deb package for JDK"
date: 2006-08-25
forum: Packaging and Compiling Programs
---

### Post by nits_555 on 2006-08-25
Hi,

I have been trying to install J2SE on dapper. Following is what I get:

=============================================================================
nitin@ubuntu:~/Desktop$ fakeroot make-jpkg jre-1_5_0_08-linux-i586-rpm.bin
Creating temporary directory: /tmp/make-jpkg.XXXXAxVh3y
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm- j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun- j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
=============================================================================
Where could I possibly be going wrong?

Thanks,
Nitin.

---

### Post by mlind on 2006-08-26
You're doing it for the wrong package. Don't use **.rpm.bin**, that's for Fedora, download the other one.

---

