---
title: "Intel gma, Ubuntu 13.04"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by vincanity84 on 2013-09-27
I have a problem installing intel gma on my dell latitude atg d630. Ubuntu runs very slow i think its duo the lack of a graphic drivers. I red this page
[http://www.ubuntugeek.com/how-to-install-intelr-linux-graphics-drivers-on-ubuntu-13-04.html](http://www.ubuntugeek.com/how-to-install-intelr-linux-graphics-drivers-on-ubuntu-13-04.html)

and after instaling deb package x86 intel gma i try to run a command in terminal 
[COLOR=#000000][FONT=Tahoma]

intel-linux-graphics-installer

but it fails after a couple of seconds and it gives me this

[/FONT][/COLOR]Error running transaction: GDBus.Error:org.debian.apt.TransactionFailed: error-dep-resolution-failed: The following packages have unmet dependencies:


libgles1-mesa: Depends: libglapi-mesa (= 9.0.3-0ubuntu1) but 9.1.3-0ubuntu0.3 is to be installed
libgles2-mesa: Depends: libglapi-mesa (= 9.0.3-0ubuntu1) but 9.1.3-0ubuntu0.3 is to be installed


What should I do? How can I install that drivers?

Tnx
[COLOR=#000000][FONT=Tahoma]

[/FONT][/COLOR]

---

### Post by andreazzz on 2013-09-27
Hi,
The problem you are facing might be not having hardware-acceleration enabled. This is probably caused by the driver you currently have (or haven't) installed. 
Install the appropriate driver with this command:
```

 sudo apt-get install i965-va-driver libva-intel-vaapi-driver vainfo
```
[INDENT]
source: [http://askubuntu.com/questions/240386/how-do-i-enable-hardware-accelerated-video-in-vlc-with-intel-hd-4000-gpu](http://askubuntu.com/questions/240386/how-do-i-enable-hardware-accelerated-video-in-vlc-with-intel-hd-4000-gpu)[/INDENT]

---

### Post by vincanity84 on 2013-09-27
I will try that out. Tnx for replay:)

---

### Post by vincanity84 on 2013-09-27
> **andreazzz said:**
> Hi,
The problem you are facing might be not having hardware-acceleration enabled. This is probably caused by the driver you currently have (or haven't) installed. 
Install the appropriate driver with this command:
```

 sudo apt-get install i965-va-driver libva-intel-vaapi-driver vainfo
```[INDENT]
source: [http://askubuntu.com/questions/240386/how-do-i-enable-hardware-accelerated-video-in-vlc-with-intel-hd-4000-gpu](http://askubuntu.com/questions/240386/how-do-i-enable-hardware-accelerated-video-in-vlc-with-intel-hd-4000-gpu)[/INDENT]

[COLOR=#000000]I did that.(still slow) And what now? How to know if my hardware - acceleration is enabled? :/[/COLOR]

---

### Post by andreazzz on 2013-09-29
Hardware-accelaration is enabled by default when the correct drivers are installed. Since you now installed the right drivers, we may conclude that your laptop is not capable of using Ubuntu 13.04. You might try Linux Mint with Mate desktop or adding a swap partition. Another solution might be to add some RAM to your laptop (?).
Could you give some specifications of your laptop?

---

