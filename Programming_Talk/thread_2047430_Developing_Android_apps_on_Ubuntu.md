---
title: "Developing Android apps on Ubuntu"
date: 2012-08-24
forum: Programming Talk
---

### Post by orrorin on 2012-08-24
Are there any android app developers here who use Ubuntu+Eclipse+AndroidEmulator?

I was trying to use the above setup inside a VirtualBox VM and the emulator seems to wait perpetually. Eclipse console shows a message to the effect that the emulator is waiting for HOME (process.android.acore) to start.

I want to know if this happens on native hardware (no Virtual Machine) as well.

---

### Post by satsujinka on 2012-08-24
The emulator is really slow. It takes aprox. 5-10 min. to start up for the first time on hardware. Virtualized... prepare to double that time (as a guess.)
The wait for home is just eclipse waiting for android to signal that it's at the home screen.

---

### Post by orrorin on 2012-08-25
Thanks for the response.

There was no change after running for about 32 minutes.

The emulator on the Windows7 host (on the same machine) works in less than 2 minutes.

Is there any place that I can look at the logs to see what's happening?

---

### Post by mevun on 2012-08-25
I think if it hangs there, then it is buggy and is having some sort of trouble with its configuration.  So then I delete the AVD and re-create it.  Or you can create a new one with a new name, but the same config settings that you had for your old one.  Maybe I am wrong and you should just re-start it when it seems to hang.  That would be a case where there is a race condition bug where it just happened to get stuck.

Anyway, I am pretty sure if it took you 2 minutes in Win7, then the time on Ubuntu should be about the same.  So when it is taking longer, then at least stop and try re-starting it.

---

### Post by bud986 on 2012-08-26
I use ubuntu and eclipse for dev work depending on your machine the emulator can be a bit sluggish, best option is proably to have a and android device plugged in for testing :)

---

### Post by satsujinka on 2012-08-26
If you're not using it, you could take a look at the output of logcat. Eclipse has the ability to view the log, though I can't walk you through enabling it at the moment.

---

### Post by orrorin on 2012-08-26
I tried deleting and re-creating the AVD but it was of no use. "adb logcat" didn't show anything, but "adb devices" shows the avd is "offline".

---

### Post by tienlbhoc on 2012-08-27
I use bluestack (android 2.3) with window, it is really faster than emulator,
open it and go to cmd:
```
adb connect 127.0.0.1
```

or

```
adb kill-server
adb devices
```

You can use android 4.0 with vmware, virtual box , too. I use vmware player with it, install busydos, type :

```
netcfg
```

and in win i use

```
adb connect <ip address in netcfg>
```

virtualbox can run in linux, android 4.0 for desktop, please google

---

### Post by satsujinka on 2012-08-27
Without a log it's sort of hard to identify the issue. So just a quick check, are you using 64bit Ubuntu? If you are, do you have all the 32bit libraries installed?

---

### Post by mevun on 2012-08-27
> **satsujinka said:**
> Without a log it's sort of hard to identify the issue. So just a quick check, are you using 64bit Ubuntu? If you are, do you have all the 32bit libraries installed?

Other things to check: are you using Sun/Oracle JDK?  (i.e. not the open jdk that comes with Ubuntu)

I also read that you need to use an older version of the C compiler (gcc 4.4 instead of gcc 4.6), but don't know for sure if that is true.

---

### Post by orrorin on 2012-08-27
the Ubuntu version is 12.04(32-bit) and Sun/Oracle JDK 7.

---

### Post by jaithehulk on 2012-09-08
Instead of using VMware... can the android SDK be installed on Ubuntu? and then the emulator be used with Eclipse and java-sdk?.. so the loading time of emulators would be less?

---

