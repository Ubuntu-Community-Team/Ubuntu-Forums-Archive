---
title: "android sdk/avd managers crash unless root"
date: 2014-06-30
forum: Programming Talk
---

### Post by aaronp on 2014-06-30
Hi all,
I've been developing Android Apps on Eclipse ADT for Windows with no issue. I have decided to set up my home PC which is running Ubuntu 14.04

In both the Eclipse ADT and Android Studio install I am unable to run the SDK or AVD Managers. They seem to load, the window appears for a split second and then goes away.

I've run the cli ./android sdk and ./android avd commands from within the sdk/tools directory within both the Eclipse ADT and Android Studio installation and they always yield the same result. It appears to be launching (just like when I run it from within the IDE) and then as it appears, this stacktrace is printed and the window goes away:

```
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
	at java.util.Properties.loadConvert(Properties.java:568)
	at java.util.Properties.load0(Properties.java:391)
	at java.util.Properties.load(Properties.java:341)
	at com.android.sdklib.internal.repository.sources.SdkSources.loadUserAddons(SdkSources.java:294)
	at com.android.sdklib.internal.repository.updater.UpdaterData.setupDefaultSources(UpdaterData.java:371)
	at com.android.sdkuilib.internal.repository.ui.AvdManagerWindowImpl1.setupSources(AvdManagerWindowImpl1.java:383)
	at com.android.sdkuilib.internal.repository.ui.AvdManagerWindowImpl1.postCreateContent(AvdManagerWindowImpl1.java:329)
	at com.android.sdkuilib.internal.repository.ui.AvdManagerWindowImpl1.open(AvdManagerWindowImpl1.java:141)
	at com.android.sdkuilib.repository.AvdManagerWindow.open(AvdManagerWindow.java:94)
	at com.android.sdkmanager.Main.showAvdManagerWindow(Main.java:437)
	at com.android.sdkmanager.Main.doAction(Main.java:379)
	at com.android.sdkmanager.Main.run(Main.java:150)
	at com.android.sdkmanager.Main.main(Main.java:116)
```

If I run them via sudo, they open up fine, but this is a bandaid, since I want to be able to launch them from within Android Studio and can't.

Hoping someone might know the cause of the problem.
Thanks
Aaron

---

### Post by aaronp on 2014-07-12
bump

---

