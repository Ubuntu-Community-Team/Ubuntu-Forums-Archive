---
title: "Android SDK - adb won't start"
date: 2010-12-25
forum: Programming Talk
---

### Post by bikeboy on 2010-12-25
Hi all,

I'm not a programmer but decided to have a go at setting up the Android SDK as it interests me. Following the guides on the Android dev site it has mostly been fine. The one thing that won't work though is ADB, the Android Debug Bridge that's required for an emulated device.

The error is: ```
* daemon not running. starting it now on port 5037 *
cannot bind 'tcp:5037'
ADB server didn't ACK
* failed to start daemon *
```

You might think (and Googling suggested) something is already running on that port, but a netstat suggests otherwise. top shows no instances of any Android tools running. I tried re-installing the platform-tools and running it as root even though that seemed illogical. Nothing.

Switched from OpenJDK to SunJDK in case that made a difference. The problem persists across reboots.

All of my Google hits have been for people with something bound to that port or with PATH problems, but I really can't see how that's possible here. Also, I have no ufw or iptables setup that should interfere with the port. Unless there's some other reason that port can't be opened...

Any ideas?

---

### Post by Queue29 on 2010-12-26
Could it be the case the daemon is already running? I believe eclipse starts it automatically when you have the android plugin installed, so if you're trying to start it by hand after starting eclipse, you could be causing a conflict. 

Is your PATH already set to include the /tools directory of the android plugin?

---

### Post by bikeboy on 2010-12-26
Hi thanks for the reply.

I first encountered issues via Eclipse with it not being able to connect. Manually running ADB has really just been to try and troubleshoot, as that's where the failure seems to be occurring. Even if I restart the PC and try starting ADB without opening Eclipse at all, it still fails in the same manner. All quite confusing.

I'm wondering if there's something special I need to do because I'm running the 64-bit distro, but it wouldn't seem so, and I've already got the ia32 stuff installed.

---

### Post by moma on 2010-12-26
Hello,
You may setup the Android development environment as instructed by these notes: [http://www.futuredesktop.org/#guides](http://www.futuredesktop.org/#guides)  (follow the link to "Developing applications for Google's Android phone."). It won't let you down.

---

### Post by bikeboy on 2010-12-27
Thanks moma, unfortunately it made no difference. I now know why.

A helpful person on Identica suggested an strace (strace adb fork-server server) and towards the bottom were some extra details about the failed binding of the port. Googling for this got me to [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422327), which suggested an ipv6/localhost issue and that was indeed it. Somehow my lo interface was down and just needed to be enabled again. Voila!

Pretty obscure issue I'd say. My localhost mis-config may have been present for a year or more without symptoms until this. Hopefully if somebody else is unlucky enough to run into that problem they'll find this thread and get help.

---

### Post by Rodu on 2011-02-26
Hi guys,

I solved the issue about starting the server by adding to the PATH environment variable the paths pointing to the android sdk locations:

open ~/.profile with an editor, find export PATH and add:

export PATH=/ANDROID SDK LOCATION/tools:/ANDROID  SDK LOCATION/platform-tools:PATH

Then save, logout and login, and I could run adb from the console with no errors.

The main problem for me is that android adb fires my CPU at 100% !!!

I tried to search for a solution on line but even though some people mention the same thing I couldn't find any.

Anybody had the same problem and managed to solve it? It sounds really strange to me and without a solution I have to give up! I don't want to fry my CPU!


I am using Ubuntu 10.04 32-bit, kernel 2.6.32-28-generic, adb version 1.0.26.


cheers!

---

### Post by Rodu on 2011-03-03
Hi all,

released security update brought my kernel version to 2.6.32-29-generic

and apparently this fixed the problem for me. Now the adb keeps quiet at 0 percent cpu usage.

> **Rodu said:**
> Hi guys,

I solved the issue about starting the server by adding to the PATH environment variable the paths pointing to the android sdk locations:

open ~/.profile with an editor, find export PATH and add:

export PATH=/ANDROID SDK LOCATION/tools:/ANDROID  SDK LOCATION/platform-tools:PATH

Then save, logout and login, and I could run adb from the console with no errors.

The main problem for me is that android adb fires my CPU at 100% !!!

I tried to search for a solution on line but even though some people mention the same thing I couldn't find any.

Anybody had the same problem and managed to solve it? It sounds really strange to me and without a solution I have to give up! I don't want to fry my CPU!


I am using Ubuntu 10.04 32-bit, kernel 2.6.32-28-generic, adb version 1.0.26.


cheers!

---

### Post by hemantborole on 2011-03-08
I am on  2.6.35-27-generic (ubuntu meerkat).
The adb for me is still taking over 100% cpu.

---

