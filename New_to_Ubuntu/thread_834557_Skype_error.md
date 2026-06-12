---
title: "Skype error"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-19
Hy all

I just upgraded skype and I got this message:

```
E: /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb: trying to overwrite `/usr/share/icons/skype.png', which is also in package skype-common
```
Any idea what that means?
And also, do you know where can I find a source package of skype, so I can compile it manualy?I saw that there are multiple variants of skype: skype, skype static, dynamic and static OSS. What does each mean?

---

### Post by brian_p on 2008-06-19
> **Troll_the_Great said:**
> Hy all

I just upgraded skype and I got this message:

```
E: /var/cache/apt/archives/skype_2.0.0.72-1_i386.deb: trying to overwrite `/usr/share/icons/', which is also in package skype-common
```
Any idea what that means?

The file skype.png is in both packages. Harmless. You can ignore it.

> And also, do you know where can I find a source package of skype, so I can compile it manualy?

You cannot get it because Skype do not release it.

> I saw that there are multiple variants of skype: skype, skype static, dynamic and static OSS. What does each mean?

The static packages include the libraries as well as the skype program itself. The dynamic packages don't. If the needed libraries are on your system the dynamic package is usually the one you want.

---

### Post by Troll_the_Great on 2008-06-19
Thx for answering.I have yet another question.This is the official skype download.

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

I saw that there are 3 tar.bz files for dynamic, static and static OSS.Those are not source code?Can't I compile them for my system?

---

### Post by brian_p on 2008-06-19
> **Troll_the_Great said:**
> Thx for answering.I have yet another question.This is the official skype download.

[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

I saw that there are 3 tar.bz files for dynamic, static and static OSS.Those are not source code?Can't I compile them for my system?

No, they are binaries and cannot be used for compiling. The source code is owned by Skype and they have no intention of making it public.

---

### Post by ausrick on 2009-02-22
I get the following error.  "Error: Wrong architecture 'i386'" when trying to install the skype package for Ubuntu.

I know this is because I'm running the x64 version of Ubuntu 8.10, but what I don't know and am hoping you can help me with is are there any work-arounds?  Would the answer be in the bottom 3 packages skype has for download from their site labeled "Dynamic" "Static" and "Static OSS" or is there some other way to get i386 (32bit) architecture programs to install and run on a x64 (64bit) architecture OS?

---

