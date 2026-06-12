---
title: "Android emulator"
date: 2011-04-29
forum: Programming Talk
---

### Post by lovinglinux on 2011-04-29
I would be very thankful if anyone could post the steps to get the Android emulator working on Ubuntu. I have downloaded the SDK and followed the instructions on the developers site, but it doesn't even recognize the binary.

---

### Post by SevenMachines on 2011-04-29
* Download sdk
$ wget [http://dl.google.com/android/android-sdk_r10-linux_x86.tgz](http://dl.google.com/android/android-sdk_r10-linux_x86.tgz)

$ tar -zvxf android-sdk_r10-linux_x86.tgz 
$ cd android-sdk-linux_x86/

* Run android manager and install an actual sdk platform
$ ./tools/android 
The go to available packages and install something like SDK Platform 2.3.3

* Now go to 'virtual devices' and create a device with the 'target' set to the SDK you installed above

* With the device highlighted, click 'start...' on the right hand side

If something doesnt work, you'll need to post exactly what you did and what the errors say

---

### Post by lovinglinux on 2011-04-29
> **SevenMachines said:**
> * Download sdk
$ wget [http://dl.google.com/android/android-sdk_r10-linux_x86.tgz](http://dl.google.com/android/android-sdk_r10-linux_x86.tgz)

$ tar -zvxf android-sdk_r10-linux_x86.tgz 
$ cd android-sdk-linux_x86/

* Run android manager and install an actual sdk platform
$ ./tools/android 
The go to available packages and install something like SDK Platform 2.3.3

* Now go to 'virtual devices' and create a device with the 'target' set to the SDK you installed above

* With the device highlighted, click 'start...' on the right hand side

If something doesnt work, you'll need to post exactly what you did and what the errors say

Thanks a lot. After posting, I have found [this tutorial]("http://crashcourse.ca/content/android-emulator-ubuntu-1004-60-seconds") and I am following it.

So far so good. I am downloading the components right now.

---

### Post by lovinglinux on 2011-04-29
Yay!

[IMG]http://www4.picturepush.com/photo/a/5553447/img/5553447.jpg[/IMG]

Thanks a lot.

---

### Post by lovinglinux on 2011-04-29
I have no Internet in the emulator :-(

---

### Post by SevenMachines on 2011-04-29
Note you can now install android in virtualbox [http://www.android-x86.org/](http://www.android-x86.org/), less api versions to test against and eclipse integration but faster too so it can be handy

---

### Post by SevenMachines on 2011-04-29
> **lovinglinux said:**
> I have no Internet in the emulator :-(
hmm, i think that should be automatic. you could try poking around the command line using 
$ adb shell
# netcfg
# logcat
that sort of thing

---

### Post by lovinglinux on 2011-04-29
> **SevenMachines said:**
> Note you can now install android in virtualbox [http://www.android-x86.org/](http://www.android-x86.org/), less api versions to test against and eclipse integration but faster too so it can be handy

Yay!

[IMG]http://www1.picturepush.com/photo/a/5553579/480/Anonymous/android1.jpg[/IMG]

Thanks.

---

### Post by lovinglinux on 2011-04-29
The connection problem seems to affect only version 2.3.3. I have connection with 1.6. Will test 2.3.1 and 3.0 now.

---

### Post by lovinglinux on 2011-04-29
Internet is working with version 2.3.1 and 2.3.3.

So everything is fine now.

Thanks

---

### Post by SevenMachines on 2011-04-30
Thanks to you too, i was inspired to find out how to launch the debugger against the running android on virtualbox! One off the TODO list :)

---

### Post by lovinglinux on 2011-04-30
> **SevenMachines said:**
> Thanks to you too, i was inspired to find out how to launch the debugger against the running android on virtualbox! One off the TODO list :)

You are welcome. I guess we were both inspired, because after installing Android, I started to test Fennec on the desktop,then decided to add support for Fennec testing on my FoxTester extension and ended adding support for testing Fennec, Seamonkey and Thunderbird. So no now FoxTester can be used for testing a lot of stuff besides Firefox itself :-)

---

### Post by mashmusic11235 on 2012-09-02
Hi. Sorry for bringing back an old thread, but I have a question.

I followed the and got everything working, until it comes to the point of running the AVD. If I try to run it from the frontend, it doesn't work at all, and if I try to run it from the terminal, I get the error:

Segmentation fault (core dumped)

Any advice?

Thanks in advance.

---

### Post by lisati on 2012-09-02
From the forum code of conduct: 
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

