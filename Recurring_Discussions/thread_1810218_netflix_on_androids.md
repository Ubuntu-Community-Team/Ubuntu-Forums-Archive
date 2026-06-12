---
title: "netflix on androids"
date: 2011-07-22
forum: Recurring Discussions
---

### Post by ehaley on 2011-07-22
Just a dumb question 
if the android is running linux kernel and netflix has released a app for it can that app be used in ubuntu
to be able to watch netflix:popcorn:

---

### Post by roololing on 2011-07-22
Hm, don't think so. But, they *are* releasing a Netflix plugin for Chrome. It's HTML 5 instead of Silverlight, so we can use it on Ubuntu.

Here's the link:
[http://www.thechromesource.com/netflix-plug-in-for-chrome-and-chrome-os-is-on-the-way/](http://www.thechromesource.com/netflix-plug-in-for-chrome-and-chrome-os-is-on-the-way/)

---

### Post by cybergalvez on 2011-07-22
> **roololing said:**
> Hm, don't think so. But, they *are* releasing a Netflix plugin for Chrome. It's HTML 5 instead of Silverlight, so we can use it on Ubuntu.

Here's the link:
[http://www.thechromesource.com/netflix-plug-in-for-chrome-and-chrome-os-is-on-the-way/](http://www.thechromesource.com/netflix-plug-in-for-chrome-and-chrome-os-is-on-the-way/)

unfortunately it does not say when they will release it, because its not released yet

---

### Post by doas777 on 2011-07-22
> **ehaley said:**
> Just a dumb question 
if the android is running linux kernel and netflix has released a app for it can that app be used in ubuntu
to be able to watch netflix:popcorn:
maybe, maybe not. the app is bound to use android stack components above the kernel, some of which are likely to be proprietary drm components. if that is the case, then those components will have to be ported or replaced before the app can be ported over.

---

### Post by perspectoff on 2011-07-25
The Netflix app for Android is here:

[https://market.android.com/details?id=com.netflix.mediaclient](https://market.android.com/details?id=com.netflix.mediaclient)

The Android OS can be installed into a Virtualbox (or QEMU or VMWare) virtual machine using the Android-i86 installer found here:

[http://www.android-x86.org/documents/installhowto](http://www.android-x86.org/documents/installhowto)

---------------------------------------------------------------

The alternative is to install the 32-bit Linux Android SDK, which provides an emulator. This requires:

ia32-libs
sun-java6-jdk

and the Linux Android SDK found here:
[http://developer.android.com/sdk/index.html](http://developer.android.com/sdk/index.html)

Then the ADB is used to install apps:
[http://developer.android.com/guide/developing/tools/adb.html](http://developer.android.com/guide/developing/tools/adb.html)

Canonical is reportedly working on a method to run Android apps without having to install a full Android environment, but they've been at it for about 2 years, so who knows.

---

### Post by illuminatifire on 2011-11-19
I had no luck with this setup. I installed the 2.2.2 eepc android version on my virtual machine, but it doesn't come with a regular market place so there is no easy way of installing netflix through it.

---

