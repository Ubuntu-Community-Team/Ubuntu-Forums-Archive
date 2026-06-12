---
title: "Nook Tablet sideloading, Indirect, XDA, and no fun"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-02-11
OK, I'm trying to run the script provided by Indirect at the XDA Forums to sideload the Amazon Appstore app (authentically downloaded from the Amazon site) to an unrooted Nook Tablet running OS version 1.4.1 using Wine 1.3. Or at least I'm trying to. Here's the link for the forum post: [http://forum.xda-developers.com/showthread.php?t=1407023]("http://forum.xda-developers.com/showthread.php?t=1407023"). I put the Sideload folder into Documents and put the apk file I want to install into the Sideload folder as instructed. Then I installed Wine 1.3 I connected my NT to my computer, opened a terminal, ran:
```
thomas@Thomas-Desktop:~$ cd ~/Documents/Sideload
thomas@Thomas-Desktop:~/Documents/Sideload$ adb install Amazon-Appstore-release.apk
No command 'adb' found, did you mean:
 Command 'cdb' from package 'tinycdb' (main)
 Command 'gdb' from package 'gdb' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'zdb' from package 'zfs-fuse' (universe)
 Command 'kdb' from package 'elektra-bin' (universe)
 Command 'tdb' from package 'tads2-dev' (multiverse)
 Command 'pdb' from package 'python' (main)
 Command 'jdb' from package 'openjdk-6-jdk' (main)
 Command 'jdb' from package 'openjdk-7-jdk' (universe)
 Command 'ab' from package 'apache2-utils' (main)
 Command 'ad' from package 'netatalk' (universe)
adb: command not found
thomas@Thomas-Desktop:~/Documents/Sideload$
```
What am I doing wrong? Is it even possible?
Thanks in advance.

---

### Post by cortman on 2012-02-11
You need to download and install the Android SDK, available [here]("http://developer.android.com/sdk/index.html").

---

### Post by doppel.ganger on 2012-02-11
And then?

---

### Post by doppel.ganger on 2012-02-11
Also, is installing android sdk just downloading the file, unzipping it, and installing the extra tools?

---

### Post by cortman on 2012-02-11
> **doppel.ganger said:**
> Also, is installing android sdk just downloading the file, unzipping it, and installing the extra tools?

Exactly.

---

### Post by doppel.ganger on 2012-02-11
Should that command work after installing all the extras?

---

### Post by cortman on 2012-02-11
As I recall, adb is among the extra tools you specify for installation. The CLI command "adb" should work after that.

---

### Post by doppel.ganger on 2012-02-11
Thanks. What exactly does the adb command do? Will it install the apk file onto my nook?

---

### Post by doppel.ganger on 2012-02-11
Can anyone explain what adb is and if it will put the app on my Nook?

---

### Post by cortman on 2012-02-11
I'm no Android dev (I'd like to get into it more, but Ubuntu is my main focus right now) but I believe it's a utility that lets the SDK communicate with either an emulator or a device attached to the computer. [Here]("http://developer.android.com/guide/developing/tools/adb.html") is a page on it. It stands for Android Debug Bridge.
I can't tell you if it'll work or not. Looks plausible, except the Wine part- what are you running in Wine to do this procedure?

---

### Post by doppel.ganger on 2012-02-11
The script by Indirect, found at the link on the first post in this thread.

---

### Post by cortman on 2012-02-11
I don't know enough to pass judgement. Give it a try.

I don't know the nature of the NT, but I know with my Galaxy S2 all I have to do is copy the .apk file onto the SD card or something, and installing is one of the options I get when I select it. Could be the NT is locked down too much though.

---

### Post by doppel.ganger on 2012-02-11
Thanks. I'll check back with the results once it's done installing all the extras.

---

### Post by indirect on 2012-04-09
Hey there! This is Indirect (the creator of that sideloading script) and I would like you to know that these are the steps for you to run it within Ubuntu:
download android sdk for linux [here]("http://dl.google.com/android/android-sdk_r18-linux.tgz")
and then unzip that, run ./android inside of that directory and download the "extra tools"
Next you just need to add ~/Directory/with/android_sdk/platform-tools to your path and then reboot then you can sideload where ever you are. :)

Note: I posted this incase anyone was curious on how to set it up.

---

