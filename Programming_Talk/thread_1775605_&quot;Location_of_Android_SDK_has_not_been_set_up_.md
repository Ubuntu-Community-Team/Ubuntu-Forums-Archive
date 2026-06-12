---
title: "&quot;Location of Android SDK has not been set up in the Preferences&quot; ~ Eclipse"
date: 2011-06-05
forum: Programming Talk
---

### Post by skytreader on 2011-06-05
Hi. I'm having the issue described [here]("http://code.google.com/p/android/issues/detail?id=11503") except that I'm running Lucid Lynx and Eclipse Galileo.

The proposed solution, click on Window->"Android SDK and AVD Manager" while in an Android perspective (e.g., DDMS), doesn't work for me.

How do I set-up the location of my Android SDK? Thanks.

---

### Post by ubudog on 2011-06-05
Hi there.  This is a really easy one to fix.

First, while in Eclipse, click on the Window tab.  There you will find Preferences.  Click that.  Then click on Android, and enter the location of your sdk.  Easy, right?  Let me know if you have any problems.

---

### Post by skytreader on 2011-06-05
Err... this is embarrassing but what is the path to the Android SDK?

I've tried whereis but to no avail

```
chad@chad-laptop:~$ whereis android-sdk
android-sdk:
chad@chad-laptop:~$ whereis android-sdk-linux_86
android-sdk-linux_86:
chad@chad-laptop:~$ whereis android
android:
chad@chad-laptop:~$ whereis adb
adb:

```

Does this mean I don't have it installed? But I have DDMS in Eclipse! So....dead-end for me :C

---

### Post by ubudog on 2011-06-05
You don't have to install the sdk.  You just have to download it and extract it.  If you have it extracted, you will be able to see it in your home directory.  To be sure it's there, run this command and post the output.  Extract it in your home directory.  

```
cd $HOME && ls | grep android
```

Then, from Eclipse, click the browse button and it should be android-sdk-linux_86 in your home directory or wherever you extracted it.

---

### Post by ubudog on 2011-06-07
So you got it working?  Cool!

---

### Post by skytreader on 2011-06-08
Yep. Thanks. You (already) have my support in your Ubuntu Membership by the way. Good luck with that!

---

### Post by ubudog on 2011-06-08
Glad you got it working and thanks for the support!

---

