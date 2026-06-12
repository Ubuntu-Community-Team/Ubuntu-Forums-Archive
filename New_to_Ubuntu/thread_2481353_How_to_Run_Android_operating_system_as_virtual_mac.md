---
title: "How to Run Android operating system as virtual machine on Ubuntu AMD64 ?"
date: 2022-11-27
forum: New to Ubuntu
---

### Post by patrick2957672 on 2022-11-27
Hello

Android OS can be downloaded, it is mostly free. Basically the Google shop is nice to have to use many softwares. 

Some source:
[https://source.android.com/](https://source.android.com/)

How to Run Android operating system as virtual machine on Ubuntu AMD64 ?

QEMU can do that on AMD64 host machine?

Regards

---

### Post by grahammechanical on 2022-11-27
Give consideration to Anbox

[https://anbox.io/](https://anbox.io/)


> [Is it possible to install the Google Play Store?]("https://anbox.io/#collapse2")                                                                           Yes, this is generally possible. However Google doesn't allow anyone                             to ship its applications as long as the device is not certified and the                             vendor didn't sign an agreement with Google.                         

                                                      The Anbox project **does not** have any interest in shipping the                             Google Play store and we're not allowed to do so. We may add                             an easy way for our users at a later point which allows easy                             distribution of Android applications suited for the Anbox                             runtime environment.                         

                                      **[How can I install applications into the Anbox runtime?]("https://anbox.io/#collapse3")**

                                                                           There is no easy way yet for a user to install applications into the                             Anbox runtime, other than using the [Android Debug Bridge (adb).]("https://developer.android.com/studio/command-line/adb.html")                             When you have adb installed on your host system you can install applications                             like this:                         

                         [FONT=Ubuntu Mono]                             $ adb install path/to/my-app.apk                         
[/FONT]
                                                      Afterwards your application should be installed as part of the Anbox runtime                             and can be launched via the host system application launcher.

I have used the Android Debug Bridge to install an Android app. First download the APK file of the app and follow the above instructions. There are web sites that offer APK files to be downloaded for free.

Regards

---

